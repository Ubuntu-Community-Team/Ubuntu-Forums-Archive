---
title: "Custom Minimal Server ISO for VPS Deployment"
date: 2013-04-09
forum: General Help
---

### Post by ThinkPrivacy on 2013-04-09
Hi everyone.

I am about to start a project to create my own minimal Ubuntu Server ISO for VPS deployment (lots of VPS) and was hoping I could get some pointers.

I need the ISO to allow the installation technician to input various parameters at the beginning of the install in order for various services to be setup.


[LIST=1]
[*]Domain Name - All installations will have a different domain name associated with them - this will be used to setup various services such as OpenSSL, OpenVPN, Drupal, Mail to name a few.
[*]List of services to be installed - this should allow the technician to select specific services from a preseeded list to be installed
[/LIST]

Once this is done the installation needs to install and configure the services selected which as an absolute minimum will be Apache, MySQL & PHP.

I need the installation to connect to a custom Repository for upgrades once the installation has completed (I will setup my own repository with just the packages needed for the VPS).

I have a read a little about pre-seeding and rolling my own distro with extra packages on the ISO but I am not sure how to go about taking the input from the technician to initiate the installation, does anyone know how I can do this?

Also, one of the install options will be Drupal - does anyone know how I can pre-seed Drupal installation by installing via Drush instead of Web Setup?

With regards to SSL certificate - many services will be sharing the same certificate on secure.domain.name just using different ports (for example webmail, smtp, pop3, OpenVPN etc.) how easy would it be to automate this and is it possible to automate the CA setup?

Also, with regards to setting up full disk encryption - is it possible to grab the encryption pass phrase from a remote location?  I don't want the installation technician to know the pass phrase so it would be nice to automate the process and grab the pass phrase from something like passphrase.domain.name as a text file.

Any help appreciated, thanks.

---

### Post by ThinkPrivacy on 2013-04-12
Any help?

---

### Post by oldfred on 2013-04-13
I have not installed server, but run a couple of scripts to add packages & update fstab to let me link data into my new install.

I think you are going to have to create a total custom script. You could start with just minimal ISO, server ISO or roll your own ISO as a starting point and then with tasksel or your own scripts install whatever you define.

You have have the script ask for parameters and use those throughout script. 

 OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

   Kickstart - Unattended Ubuntu installations made easy
[http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/](http://www.linuxuser.co.uk/tutorials/unattended-ubuntu-installations/2/)

   Setting up your own APT repository with upload support - 2005
[http://www.debian-administration.org/articles/286](http://www.debian-administration.org/articles/286)
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[https://help.ubuntu.com/community/LocalAptGetRepository](https://help.ubuntu.com/community/LocalAptGetRepository)

Possible starting point?

 Install script from Minimal - Paqman
[http://ubuntuforums.org/showthread.php?t=1460870](http://ubuntuforums.org/showthread.php?t=1460870)
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

