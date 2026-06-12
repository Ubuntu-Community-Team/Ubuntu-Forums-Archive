---
title: "Can't connect to repositories"
date: 2014-04-19
forum: General Help
---

### Post by woopud on 2014-04-19
Just installed Ubuntu 14.04 on my second hard drive just so i wouldn't mess up Windows 7 but after reboot there's no GRUB so no Windows it boot directly into Ubuntu.  So, I tried to install Boot Repair but I can't connect to any repositories?  Any help is greatly appreciated.

---

### Post by grahammechanical on 2014-04-19
Which problem shall we deal with first? If Ubuntu is the only operating system present, then we do not see a Grub boot menu. Did you disconnect the hard drive with Windows 7 on (a sensible thing to do) and then install Ubuntu on the other drive?

If so, the Grub does not know of the existence of Windows 7. When in Ubuntu open a terminal and run

```
sudo update-grub
```

Watch the output in the terminal. Does Grub see Windows 7 loader? If so, try rebooting and see if you get a Grub boot menu with Windows 7 in the list.

As regards not being able to connect to any repositories, you have not given us enough information. What error messages do you see? From my experience with using the development version of 14.04 over many months, we always get an icon appearing in the top panel telling us that there is a connection problem in situations like this. Click on the icon and tell us what it says. Or run

```
sudo apt-get update
sudo apt-get upgrade
```

and again watch the output that comes in the terminal. We need to see those error messages.

Regards.

---

### Post by woopud on 2014-04-19
Okay, here we go:

```
woopud@woopud-pc:~$ sudo update-grub
[sudo] password for woopud: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
woopud@woopud-pc:~$ sudo apt-get update
Ign http://mirror.hmc.edu trusty InRelease
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://mirror.hmc.edu trusty-updates InRelease                             
Hit http://security.ubuntu.com trusty-security Release.gpg                     
Hit http://mirror.hmc.edu trusty Release.gpg                         
Ign http://archive.canonical.com trusty InRelease                    
Hit http://security.ubuntu.com trusty-security Release               
Hit http://mirror.hmc.edu trusty-updates Release.gpg                 
Ign http://ppa.launchpad.net trusty InRelease                         
Hit http://mirror.hmc.edu trusty Release                             
Hit http://security.ubuntu.com trusty-security/universe amd64 Packages         
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://mirror.hmc.edu trusty-updates Release                     
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://mirror.hmc.edu trusty/main amd64 Packages                           
Ign http://ppa.launchpad.net trusty Release.gpg                      
Hit http://security.ubuntu.com trusty-security/restricted amd64 Packages
Hit http://archive.canonical.com trusty Release                                
Hit http://mirror.hmc.edu trusty/universe amd64 Packages                       
Hit http://mirror.hmc.edu trusty/restricted amd64 Packages                     
Hit http://security.ubuntu.com trusty-security/universe i386 Packages          
Hit http://mirror.hmc.edu trusty/main i386 Packages                            
Hit http://security.ubuntu.com trusty-security/main i386 Packages    
Hit http://archive.canonical.com trusty/partner Sources              
Ign http://ppa.launchpad.net trusty Release                          
Hit http://mirror.hmc.edu trusty/universe i386 Packages              
Hit http://security.ubuntu.com trusty-security/restricted i386 Packages
Hit http://mirror.hmc.edu trusty/restricted i386 Packages            
Hit http://archive.canonical.com trusty/partner amd64 Packages       
Hit http://security.ubuntu.com trusty-security/main Translation-en   
Hit http://mirror.hmc.edu trusty/main Translation-en                 
Hit http://archive.canonical.com trusty/partner i386 Packages        
Hit http://mirror.hmc.edu trusty/restricted Translation-en           
Hit http://security.ubuntu.com trusty-security/restricted Translation-en
Hit http://mirror.hmc.edu trusty/universe Translation-en             
Hit http://security.ubuntu.com trusty-security/universe Translation-en         
Hit http://mirror.hmc.edu trusty-updates/universe amd64 Packages               
Hit http://mirror.hmc.edu trusty-updates/main amd64 Packages                   
Hit http://mirror.hmc.edu trusty-updates/restricted amd64 Packages             
Hit http://mirror.hmc.edu trusty-updates/universe i386 Packages                
Hit http://mirror.hmc.edu trusty-updates/main i386 Packages          
Hit http://mirror.hmc.edu trusty-updates/restricted i386 Packages    
Hit http://mirror.hmc.edu trusty-updates/main Translation-en         
Hit http://mirror.hmc.edu trusty-updates/restricted Translation-en             
Hit http://mirror.hmc.edu trusty-updates/universe Translation-en               
Ign http://security.ubuntu.com trusty-security/main Translation-en_US
Ign http://security.ubuntu.com trusty-security/restricted Translation-en_US    
Ign http://security.ubuntu.com trusty-security/universe Translation-en_US      
Ign http://archive.canonical.com trusty/partner Translation-en_US    
Ign http://archive.canonical.com trusty/partner Translation-en       
Ign http://mirror.hmc.edu trusty/main Translation-en_US
Ign http://mirror.hmc.edu trusty/restricted Translation-en_US
Ign http://mirror.hmc.edu trusty/universe Translation-en_US
Ign http://mirror.hmc.edu trusty-updates/main Translation-en_US
Ign http://mirror.hmc.edu trusty-updates/restricted Translation-en_US
Ign http://mirror.hmc.edu trusty-updates/universe Translation-en_US
Err http://ppa.launchpad.net trusty/main amd64 Packages
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US
Ign http://ppa.launchpad.net trusty/main Translation-en
W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
woopud@woopud-pc:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  liboxideqt-qmlplugin qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets webapp-container
  webbrowser-app
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/858 kB of archives.
After this operation, 1,024 B disk space will be freed.
Do you want to continue? [Y/n] 

```

---

### Post by woopud on 2014-04-19
I'm going to reboot now to see if Grub works.

---

### Post by woopud on 2014-04-19
GRUB works!  I'm typing this from Windows 7, thank you.  Will reboot again into Ubuntu to work on the repository issues.

---

### Post by ibjsb4 on 2014-04-19
Yannubuntu is not yet available for 14o4.

[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/)

---

