
## 2019 Danimae Vossen
## Uncomment the boxes you want to run, then run 'vagrant up' from the command line to lauch them simultaneously
## If you need to run multiples independently, copy this file into another directory and select individual boxes

## Recommended choices denoted by *

boxes = [

  # "f500/ubuntu-lucid64",                             # Ubuntu 10.04
  # "3dox/ubuntu-oneiric",                             # Ubuntu 11.04
  # "hashicorp/precise64",                             # Ubuntu 12.04
  # "rafaelrosafu/raring64-vanilla",                   # Ubuntu 13.04
  # "ubuntu/trusty64",                                 # Ubuntu 14.04
  # "bento/ubuntu-14.04",                              # Ubuntu 14.04
  # "wzurowski/vivid64",                               # Ubuntu 15.04
  # "geerlingguy/ubuntu1604",                          # Ubuntu 16.04 *
  # "consumerlab/ubuntu-server-16-04-LTS",             # Ubuntu 16.04
  # "mrlesmithjr/zesty64",                             # Ubuntu 17.04
  # "ubuntu/bionic64",                                 # Ubuntu 18.04 *

  # "danimaetrix/openSUSE-Leap-42.3",                  # OpenSUSE (Danimae) *     
  # "opensuse/openSUSE-42.2-x86_64",                   # OpenSUSE
  # "webhippie/opensuse-13.2",                         # OpenSUSE
  # "bento/opensuse-leap-42.1",                        # OpenSUSE
  
  # "generic/rhel7",                                   # Redhat *
  # "thinktainer/centos-6_6-x64",                      # Centos 6 *
  # "ddacunha/CentOS-7.2",                             # Centos 7
  # "generic/fedora27",                                # Fedora *
  # "generic/gentoo",                                  # Fedora *

  # "wvera/sles12sp1",                                 # SLES 12 / SP 1
  # "trueability/sles-12-sp1",                         # SLES 12 / SP 1
  # "danimaetrix/sles12-sp1-sdk",                      # SLES 12 / SP 1 + SDK *

  # "debian/wheezy64",                                 # Debian
  # "debian/contrib-jessie64",                         # Debian
  # "generic/debian9",                                 # Debian *

  # "AndrewDryga/vagrant-box-osx",                     # MacOS (may need to disable folder sync (uncomment below)) *

  # "opentable/win-2008r2-standard-amd64-nocm",        # Server 2008 Standard *
  # "opentable/win-2012r2-standard-amd64-nocm",        # Server 2012 Standard (no updates) *  
   "danimaetrix/2012R2-demo-server",                   # Server 2012 Adobe Demo Server (fully updated) *
  
  # "mwrock/Windows2016",                              # Server 2016 Standard 
  # "danimaetrix/win2016-datacenter-x64",              # Server 2016 Datacenter (Danimae) *
   
  # "inclusivedesign/windows81-eval-x64",              # Windows 8 *
  # "danimaetrix/win10-prof-x64",                      # Windows 10 (Danimae) *
  # "opentable/win-7-professional-amd64-nocm",         # Windows 7 *
  # "danimaetrix/vista-sp2-x64"                        # Vista x64 (Danimae) *

]


box_config = Hash.new 
boxes.each do |key|

	boxName = key.sub("/","-")
	puts "\e[32m\nBox details\n\e[0m-------------"
	puts "name: " + "\e[36m" + boxName + "\e[0m" 
	puts "ssh:  \e[36mvagrant ssh " + boxName + "\e[0m "
	puts 

	box_config[key] = {
		"name" => boxName,
	}

end

Vagrant.configure("2") do |config|  

  boxes.each do |key|	

	#vbox.vm.synced_folder ".", "/vagrant", disabled: true
	#config.vm.synced_folder "D:\\Repositories\\adobe\\UST-Install-Scripts\\other_platforms", "/test"
	#config.vm.synced_folder "D:\\Repositories\\adobe\\user-sync-fork", "/pyinst"
	#config.vm.synced_folder "D:\\Repositories\\adobe\\keyring-test", "/pyinst"

    config.vm.define box_config[key]["name"] do |vbox| 
      vbox.vm.box = key
      vbox.vm.boot_timeout = 600
      vbox.ssh.insert_key = false
      vbox.vbguest.auto_update = false      
      vbox.vm.provider "virtualbox" do |v|
        v.customize ["modifyvm", :id, "--memory", 2048]
        v.customize ["modifyvm", :id, "--cpus", 2]
        v.customize ["modifyvm", :id, "--vram", 256]
        v.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
        v.gui = false		
		v.name = box_config[key]["name"]
	  end
   end	

  end
end