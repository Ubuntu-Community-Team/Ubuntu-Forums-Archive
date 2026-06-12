---
title: "Synaptic Package Manager Problem"
date: 2008-03-11
forum: General Help
---

### Post by Hoppo88 on 2008-03-11
Heya, im to both linux and these forums.  Recently i had a problem with my package manager when i try opening it i get the following error.

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

How ever when i go into the terminal and type the command i get this message back

"dave@dave-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege"

So a friend told me to try putting sudo in front of the command and then i get this error

"dave@dave-desktop:~$ sudo dpkg --configure -a
#Setting up initramfs-tools (0.85eubuntu20) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: subprocess post-installation script returned error exit status 1"

i am unable to access the package manager or the update manager as a result to this.
anyone have any ideas on what to do ?

Many thanks
Dave

---

### Post by Hoppo88 on 2008-03-12
Anyone have any idea what i can do to fix this ?

---

### Post by Antz002 on 2008-03-12
I have exactly the same problem Dave - no idea how to fix it though!?

---

### Post by plucky on 2008-03-12
```
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade
```

Try each line in a terminal and post output.


Good luck

---

### Post by Antz002 on 2008-03-12
For the first line I got:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

For the second:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_ZA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_ZA
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]             
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Get:3 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/main Translation-en_ZA                  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/restricted Translation-en_ZA  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/universe Translation-en_ZA    
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/multiverse Translation-en_ZA  
Get:4 [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates Release.gpg [191B]  
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_ZA
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_ZA           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates Release                         
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/main Packages                           
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/restricted Packages                     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/main Sources                  
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/restricted Sources            
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/universe Packages             
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_ZA     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/universe Sources              
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_ZA     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/main Packages                   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/restricted Packages             
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/main Sources          
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/restricted Sources    
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/universe Packages     
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/universe Sources      
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/multiverse Packages   
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) gutsy-updates/multiverse Sources    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_ZA
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                     
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources               
Fetched 4B in 6s (1B/s)                                                        
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

For the third:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

Thanks for your reply plucky

---

### Post by kesman on 2008-03-12
> /usr/sbin/mkinitramfs: 13: getopt: not found

Maybe someone with this file could post it here? I'm at work on a windows machine, otherwise I would've done this.

---

### Post by plucky on 2008-03-12
Antz002

You need to run ```
sudo dpkg --configure -a
``` to correct **your** problem.
The other answer was for **Hoppo88**

Good luck

---

### Post by Antz002 on 2008-03-12
Thanks!

---

### Post by happyandblue2 on 2008-03-12
I also thank you...
I was pulling my hair out trying to solve the same problem..

---

### Post by kahukiloia on 2008-03-14
I have similar problem to the one you guys experienced and I hope someone can assist me. 
I'm new to Linux so I'm not quite sure what I'm doing here but this is the error I'm getting:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I have tired to get my xine to work and now neither one of them is working for me.

Thanks in advance

---

### Post by plucky on 2008-03-14
kahukiloia,

> Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list

The problem is **<!DOCTYPE** in the file medibuntu.list should not be there.Open a terminal and type ```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
``` and put a **#** to comment out line 1 that begins with **!DOCTYPE**

This file should look like this > ## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on [https://bugs.launchpad.net/medibuntu/](https://bugs.launchpad.net/medibuntu/)
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free
# deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Good Luck

---

### Post by rab4567 on 2008-03-14
My update manager is broken so I tried to fix the problem through synaptic, I identified the broken package and put in the gusty cd it ask for but got this message

W: Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/pool/main/u/update-manager/update-manager-core_0.81_i386.deb

can you help.

---

### Post by plucky on 2008-03-14
rab4567,

Take the CDROM out of your **Sources.list** by ```
gksudo gedit /etc/apt/sources.list
```
and put a **#** in front of the line > deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted.

Then open a terminal and ```
sudo dpkg --configure -a
``` to try and repair the broken package.
p.s **you have to be online**

If that doesn't work, try ```
sudo apt-get -f install
```

If that works then ```
sudo apt-get update
sudo apt-get upgrade
```

If it doesn't then post error messages.

Good Luck

---

### Post by rab4567 on 2008-03-14
Big Thanks dude.

---

### Post by kahukiloia on 2008-03-14
Plucky,

Got it working. Many thanks!!!'

Kahukiloia

---

