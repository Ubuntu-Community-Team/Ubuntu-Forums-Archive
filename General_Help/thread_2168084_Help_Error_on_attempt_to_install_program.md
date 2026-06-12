---
title: "Help: Error on attempt to install program"
date: 2013-08-16
forum: General Help
---

### Post by dsfxN7N on 2013-08-16
Hello I'm trying to install a program called chirp on my machine to program some radios I have.  I have attempted to install this manually and through the software suite and no matter what I do I receive the following error:

> The following NEW packages will be installed:  chirp
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 276 kB of archives.
After this operation, 1,359 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/ubuntu-hams-updates/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-hams-updates/ppa/ubuntu/) precise/main chirp amd64 0.3.1-1~sconklin~precise [276 kB]
Fetched 276 kB in 1s (205 kB/s) 
(Reading database ... 188793 files and directories currently installed.)
Unpacking chirp (from .../chirp_0.3.1-1~sconklin~precise_amd64.deb) ...
dpkg: error processing /var/cache/apt/archives/chirp_0.3.1-1~sconklin~precise_amd64.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/chirp.png', which is also in package chirp-daily 20130802~precise~1
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/chirp_0.3.1-1~sconklin~precise_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Prior to running this operation I performed the following commands:

> 
sudo apt-get clean
sudo apt-get update
sudo apt-get autoclean


If I download the package and extract it into a folder I can run the program but it does not see any usb ports as it is not installed (i'm guessing)

the usb cable is recognized under lsusb as:

> 
Bus 003 Device 003: ID 067b:2303 Prolific Technology, Inc. PL2303 Serial Port


adittional info I'm running
> 
[LIST]
[*]Ubuntu 12.04 LTS
[*]memory: 1.9Gib
[*]Processor: AMD Turion(tm) 64 X2 Mobile Technology TL-58 × 2
[*]Graphics: GeForce 7150M / nForce 630M/integrated/SSE2
[*]OS type: 64-bit
[*]Disk: 155.5 GB
[/LIST]


Anyway any help you can give me would be awesome.

thanks,
Tim

---

### Post by GwL3eNC on 2013-08-16
Hello,

im not shure if i can help you, but lets try. First type

sudo apt-get -f install.

Hopefully this is enough. Else, Have you installed a previous version of chirp? You can see that with 

sudo dpkg -l | grep chirp

If there is one remove it first with

sudo apt-get purge chirp. 

Normally you install something in that way:
 
sudo apt-add-repository ppa:ubuntu-hams-updates/ppa
sudo apt-get update
sudo apt-get install chirp

Before you try again, you can try to delete the file /var/cache/apt/archives/chirp_0.3.1-1~sconklin~precise_amd64.deb
to get a new one. Also you can try to rename all chirp scripts in 

/var/lib/dpkg/info/ | grep chirp

to get some new. Also you can try to install the chirp_0.3.1-1~sconklin~precise_amd64.deb using 

sudo dpkg -i chirp_0.3.1-1~sconklin~precise_amd64.deb

If this wont work i dont know further and hope someone else
can help you.

---

### Post by ibjsb4 on 2013-08-16
Im not a radio buff, but Im running 32bit ubuntu and it installed without error from the software center.

> which is also in package chirp-daily 20130802~precise~1

Do you also have the ppa installed?

---

### Post by dsfxN7N on 2013-08-16
Ok so i've done the above and purged all the chirp related stuff and re-added it again and on install I get this now:

> 
The following NEW packages will be installed:
  chirp
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 276 kB of archives.
After this operation, 1,359 kB of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/ubuntu-hams-updates/ppa/ubuntu/](http://ppa.launchpad.net/ubuntu-hams-updates/ppa/ubuntu/) precise/main chirp amd64 0.3.1-1~sconklin~precise [276 kB]
Fetched 276 kB in 1s (229 kB/s) 
(Reading database ... 188662 files and directories currently installed.)
Unpacking chirp (from .../chirp_0.3.1-1~sconklin~precise_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Setting up chirp (0.3.1-1~sconklin~precise) ...
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main amd64 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/earth/deb/](http://dl.google.com/linux/earth/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems


hmmmm  in the mean time i just burned a live cd to run just chirp as a work around but i would really like to get this working. so I don't have to boot from the disk everytime i need it.

---

### Post by GwL3eNC on 2013-08-16
Hi,

have you tried what the message says?

sudo apt-get update

If it wont work i think you can open your software-center and remove one of the above earth sources out of the
list. Please test if chirp is already installed now.

---

