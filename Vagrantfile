# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/bionic64"
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "4024"
  end

  config.vm.provision :docker
  config.vm.provision :docker_compose

  config.vm.define "sqlserver" do |mongo|
    mongo.vm.network "private_network", ip: '192.168.33.30'
    mongo.vm.hostname = "sqlserver"
    mongo.vm.provision :file, source:"./docker/docker-composeSQLServer.ci.yml", destination: "/home/vagrant/docker-composeSQLServer.yml"    
    mongo.vm.provision :docker_compose, yml: "/home/vagrant/docker-composeSQLServer.yml", run: "always"
  end
end
