# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |config|
  config.vm.define "ubuntu_vm1" do |ubuntu_vm1|
    ubuntu_vm1.vm.box = "ubuntu/xenial64"
    ubuntu_vm1.vm.network "public_network"
    ubuntu_vm1.vm.provider "virtualbox" do |vb|
       ## Display the VirtualBox GUI when booting the machine
       #vb.gui = true
       #
       ## Customize the amount of memory on the VM:
      #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "90"]
      vb.memory = "1024"
      vb.cpus = 1
    end
    #config.vm.provision "shell", inline: <<-SHELL
    #  apt-get update
    #  apt-get install -y software-properties-common
    #  apt-add-repository ppa:ansible/ansible
    #  apt-get update
    #  apt-get install -y ansible git python3-pip
    #SHELL

    ubuntu_vm1.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      #ansible.playbook = "site.yml"
      ansible.playbook = "main.yml"
      #ansible.vault_password_file = "vault_password_file"
      ansible.groups = {
        "group1" => ["ubuntu_vm1"],
        #"group2" => ["machine2"],
        #"group3" => ["machine[1:2]"],
        #"group4" => ["other_node-[a:d]"] # silly group definition
        #"all_groups:children" => ["group1", "group2"],
        #"group1:vars" => {"variable1" => 9,
        #                  "variable2" => "example"}
      }
    end
  end

  config.vm.define "centos_vm1" do |centos_vm1|
    centos_vm1.vm.box = "centos/7"
    centos_vm1.vm.network "public_network"
    centos_vm1.vm.provider "virtualbox" do |vb|
      ## Display the VirtualBox GUI when booting the machine
      #vb.gui = true
      #
      ## Customize the amount of memory on the VM:
      #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "90"]
      vb.memory = "1024"
      vb.cpus = 1
    end

    centos_vm1.vm.provision :ansible do |ansible|
      ansible.verbose = "vvvvv"
      ansible.playbook = "main.yml"
      #ansible.vault_password_file = "vault_password_file"
      ansible.groups = {
        "group2" => ["centos_vm1"],
      }
    end
  end

  config.vm.define "rhel_vm1" do |rhel_vm1|
    rhel_vm1.vm.box = "generic/rhel7"
    rhel_vm1.vm.network "public_network"
    rhel_vm1.vm.provider "virtualbox" do |vb|
      ## Display the VirtualBox GUI when booting the machine
      #vb.gui = true
      #
      ## Customize the amount of memory on the VM:
      #vb.customize ["modifyvm", :id, "--cpuexecutioncap", "90"]
      vb.memory = "1024"
      vb.cpus = 1
    end

    rhel_vm1.vm.provision :ansible do |ansible|
      ansible.verbose = "v"
      #ansible.playbook = "site.yml"
      ansible.playbook = "main.yml"
      #ansible.vault_password_file = "vault_password_file"
      ansible.groups = {
        "group3" => ["rhel_vm1"],
      }
    end
  end

end
