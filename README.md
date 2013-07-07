# Pimcore Vagrant + example Data

## introduction
the main benefit of using vagrant is that you can scaffold and versioning your dev environment.
This means you script it using [Chef](http://www.opscode.com/chef/).

This VM is basically a running Pimcore installation with the example data website. Feel free to use it as basic for your next [Pimcore](http://pimcore.org) project.

at first you should know what [vagrant](http://www.vagrantup.com) is, install it and [virtualbox](https://www.virtualbox.org/wiki/Downloads)

espacilly using windows virtualbox + vagrant sucks a bit. Eaven in in bugfix releases the API is broken and cant be used by vagrant. I recommend installing virtualbox 4.2.12 and vagrant 1.2.2. 

## running vagrant on Windows
virtualbox is a bit pain on windows. Make sure you have a vagrant version and a virtualbox version that are working together (look above).  Run the vagrant terminal and virtualbox (open it before you run vagrant up) as Administrator.

## Starting the VM
building the VM is quite easy if vagrant and virtualbox are installed, just run

    git clone --recursive https://github.com/timglabisch/vagrant_pimcore_example your_project
    cd your_project
    vagrant up
    
now wait around 5 minutes and the installation should be finished.

now you can open [localhost on port 8888](http://localhost:8888). Pimcore needs a lot if time because the default settings just use around 350MB Ram.

look at *Troubleshooting* if this doesnt work for you.

## The VM
Chef installs a typically apache stack (apach2, mod_php5, mysql, ...).
You can find the default configuration in the *Vagrantfile* in the root directory.

### Passwords
    Pimcore: admin:admin (localhost:8888)
    Mysql: root:dev (localhost:3306)
    SSH: vagrant:vagrant
    
for more informations look at the vagrantfile in the main directory, feel free to change the ports.
If a port is still used, Virtualbox will use another port, look at the portmapping in the output if you run "vagrant up"

## Developing
just look at the webroot folder, this is the apache main webroot.
Feel free to change the content of the example website and make this repository to you project repository. We plan to optimize this workflow later :)

## The Database
Everytime you build or reload your vagrant vm the init.sql script is executed. Here you can persist your Database.

## Changing Configurations
look at the files in .\cookbooks\any\files\default\root, the files are synced to the server everytime you build or reload the vm. Feel free to change the Files (for example xdebug vonfig, php.ini or the VHost configuration). We plan to optimize this workflow later.

##Troubleshooting
### vm doesnt start
if something doesnt work most time it's related to virtualbox / vagrnt versions. make sure you have versions that work together (virtualbox 4.2.12 and vagrant 1.2.2 for example).
On Windows make sure that you run vagrant and virtualbox as root. In Virtualbox you should see the vm created by vagrant. if the starting process fails you can try to restart the vm in the Virtualbox gui. Sometimes it needs a bunch of tries ... .

### trouble using symlinks on windows
run vagrant and virtualbox as Administrator

