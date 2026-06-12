---
title: "Installing linux-headers"
date: 2008-05-16
forum: General Help
---

### Post by Syroco on 2008-05-16
I'm trying to install linux headers, and this is what happens


syca@syca-desktop:~$ sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-4.2 xserver-xorg-dev
[sudo] password for syca: 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
syca@syca-desktop:~$ sudo dpkg --configure -a
Setting up libgl1-mesa-glx (7.0.3~rc2-1ubuntu3) ...

dpkg: error processing libgl1-mesa-dri (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libgl1-mesa-dri
syca@syca-desktop:~$

---

### Post by kuja on 2008-05-16
First things first, try "apt-get -f install. I doubt that will do it, but it's worth a try and definitely the easiest thing if it works, I forget which thing resolves this problem, it's an ugly one though.
Then I would try to "dpkg -r" the package. If this fails, download a known good copy of the package (and perhaps any reverse dependencies that conflict) and "dpkg -i" them.

---

### Post by Gunman1982 on 2008-05-16
try 'sudo aptitude reinstall libgl1-mesa-dri' to get rid of that libgl1-mesa-dri error

---

### Post by Syroco on 2008-05-16
> **kuja said:**
> First things first, try "apt-get -f install. I doubt that will do it, but it's worth a try and definitely the easiest thing if it works, I forget which thing resolves this problem, it's an ugly one though.
Then I would try to "dpkg -r" the package. If this fails, download a known good copy of the package (and perhaps any reverse dependencies that conflict) and "dpkg -i" them.

Sorry, only on second day of Linux.
Do I put apt get -f install linux-headers-`uname -r` build-essential gcc gcc-4.2 xserver-xorg-dev

then what is dpkg -r?

And where would I get a new package? -_-


Figured it out

It installed with adding f install

:D

---

### Post by Syroco on 2008-05-16
I'm doing this so I can install my nvidia driver.

I do this:
syca@syca-desktop:~$ sh NVIDIA-Linux-x86-173.08-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.08-pkg1.run

:(

---

### Post by Ayuthia on 2008-05-16
> **Syroco said:**
> I'm doing this so I can install my nvidia driver.

I do this:
syca@syca-desktop:~$ sh NVIDIA-Linux-x86-173.08-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.08-pkg1.run

:(

Are you sure that you are in the correct directory?  If you do:
```
ls NVIDIA*
```Does the file show up?  If so, make sure that it is spelled correctly.  You will most likely need to run this as root:
```
sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
```

---

### Post by Syroco on 2008-05-16
> **Ayuthia said:**
> Are you sure that you are in the correct directory?  If you do:
```
ls NVIDIA*
```Does the file show up?  If so, make sure that it is spelled correctly.  You will most likely need to run this as root:
```
sudo sh NVIDIA-Linux-x86-173.08-pkg1.run
```

No file showed up.  The package I downloaded from Nvidia is on my desktop though.  Same spelling as in the command. 

I did do sudo sh NVIDIA-Linux-x86-173.08-pkg1.run in root
It gave me the same message..

---

### Post by Gunman1982 on 2008-05-16
sudo sh ~/Desktop/NVIDIA-Linux-x86-173.08-pkg1.run

---

### Post by lswest on 2008-05-16
have you set it executable?
```
chmod +x ~/Desktop/NVIDIA-Linux-x86-173.08-pkg1.run
sudo sh ~/Desktop/NVIDIA-Linux-x86-173.08-pkg1.run
```

in that example above i assume it's saved on your desktop, if it's not the case, please change it for your actual save location.

---

### Post by Gunman1982 on 2008-05-16
You just need to set the executable flag if you want to run it directly without the sh interpreter. ;)

---

### Post by kuja on 2008-05-19
Note, if you're installing the nvidia drivers from the *.bin file from the nvidia website, you probably want to add `DISABLED_MODULES="nv"` to the end of your /etc/default/linux-restricted-modules-common file.

---

