---
title: "Error in Synaptic- Application gone missing"
date: 2007-02-20
forum: General Help
---

### Post by angrez on 2007-02-20
First of all I am relatively new to Linux, so forgive me if I'm 'slow' :) or if I'm using the wrong terms or words. This is what happened...

-I wanted to use Gnomad2 so i could sync my ZVM...so I installed it from Synaptic
-The installation was successful, I saw that Gnomad 2 was available now under Sound and Video 
-But before I could click to open, I accidentally hit my machine's reset button.
-My computer restarted and had errors, Not a problem as Ubuntu fixed all errors and I managed to login again.
-But this time I could not find Gnomad2 anyway, I typed gnomad2 in the terminal, it couldn't find it
- So i thought I will reinstall it again from Synaptic but the problem is Synaptic says it is already installed and I can't remove it or reinstall it       

This is the error that I'm geting in Synaptic

[I]dpkg: failed to open package into file '/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned  an error code  (2)
A package failed to install. Trying to recover:[/I]

Really need your help as I can't live without music. Thanks

---

### Post by Maestro23 on 2007-02-20
Try:

> sudo dpkg -r <package name>

sudo dpkg --purge <package name>

---

### Post by angrez on 2007-02-20
> **Maestro23 said:**
> Try:

I get the following

[I]angrez@angrez-desktop:~$ sudo dpkg -r gnomad2

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory

angrez@angrez-desktop:~$ sudo dpkg --purge gnomad2

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory[/I]

---

### Post by angrez on 2007-02-20
Is there anyone who could help me? Can I reinstall Synaptic or something?

---

### Post by Rui Pais on 2007-02-20
hi,
you seems to have a corrupted /var/lib/dpkg/available. 
Check if the file exist, his a non-zero file and if it's a legible text file. A simple 
```
cat /var/lib/dpkg/available
``` should print on the terminal a list of available packages.

If you have a problem with that you can either, go back to the auto backup file:
/var/lib/dpkg/available-old

(copy that over the broken /var/lib/dpkg/available) and then do a sudo apt-get update

or try:
```
sudo dpkg --clear-avail
sudo apt-get update
```

hope one of those help.

---

### Post by angrez on 2007-02-20
Thanks for your help but it doesn't seem to work... 

At first I could not locate the file then I did a 'sudo aptitude reinstall dpkg'. Both the available and available-old files appeared but they both look similar. Still I replaced it but no difference even after I did sudo apt-get update.

Can't seem to do anything...Oh well I will live with it for a while. I will do a new install when Feisty Fawn arrives. Thanks anyway :)  BTW it shows the following when I did sudo aptitude reinstall dpkg 


desktop:~$ sudo aptitude reinstall dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  app-install-data-commercial apt apt-utils cli-common foo2zjs 
  gnome-applets gnome-applets-data gnome-netstatus-applet gnome-panel 
  gnome-panel-data gnome-system-tools imagemagick initramfs-tools 
  kdelibs-data kdelibs4c2a language-pack-en language-pack-gnome-en 
  libavahi-qt3-1 libc6 libc6-dev libc6-i686 libcurl3 libcurl3-gnutls 
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra 
  libmysqlclient15off libnautilus-extension1 libpanel-applet2-0 libpq4 
  libruby1.8 libtotem-plparser1 libvlc0 libvolumeid0 libwxbase2.6-0 
  libwxgtk2.6-0 libxine-main1 libxine1 linux-libc-dev mysql-common nautilus 
  nautilus-data opera popularity-contest python-apt ruby1.8 synaptic 
  system-tools-backends totem totem-gstreamer totem-mozilla tzdata 
  ubuntu-docs udev update-manager update-notifier vlc vlc-nox 
  vlc-plugin-esd volumeid wine 
The following packages will be REINSTALLED:
  dpkg 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 62 not upgraded.
Need to get 0B/1626kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
(Reading database ... 
[COLOR="Red"]dpkg: serious warning: files list file for package `gnomad2' missing, assuming package has no files currently installed.[/COLOR]
121114 files and directories currently installed.)
Preparing to replace dpkg 1.13.22ubuntu7 (using .../dpkg_1.13.22ubuntu7_i386.deb) ...
Unpacking replacement dpkg ...
Setting up dpkg (1.13.22ubuntu7) ...

---

