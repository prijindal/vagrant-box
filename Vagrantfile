Vagrant.configure("2") do |config|
    config.vm.box = "debian-bookwarm64/docker"
    config.vm.provision "shell", inline: <<-SHELL
        sudp apt-get update && \
        sudo apt-get install curl -y && \
        curl https://get.docker.com/ | bash

        docker plugin install grafana/loki-docker-driver:latest --alias loki --grant-all-permissions        
    SHELL
    config.vm.synced_folder ".", "/vagrant", disabled: true
  
    config.vm.hostname = "dockerregistry0"
    config.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 1
    end
  end