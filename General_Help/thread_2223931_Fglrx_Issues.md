---
title: "Fglrx Issues"
date: 2014-05-13
forum: General Help
---

### Post by john173 on 2014-05-13
**[SIZE=4]Hi[/SIZE]** *[SIZE=5]ALL[/SIZE]* **OUTTHERE**... I need some help over Here :D :D 
I am having a quite important issue 

Just followed the amd drivers guide in here [https://help.ubuntu.com/community/BinaryDriverHowto/AMD](https://help.ubuntu.com/community/BinaryDriverHowto/AMD) and after all i rebooted as well and just BOOM cinnamon Crashed and Back into FallBack Mode
(A horrible mode instead of cinnamon etc :D)
I had an idea to run "sudo apt-get autoremove" and "sudo apt-get autoclean" 

2nd worked fine 
but 1st has the final results 
> [B]Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev[/B]
user@user-desktop ~ $ ```
sudo apt-get autoremove
```
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 12 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up fglrx (2:13.251-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-13.251 DKMS files...
Loading new fglrx-13.251 DKMS files...
Error! DKMS tree already contains: fglrx-13.251
You cannot add the same module/version combo more than once.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.

_dpkg: error processing fglrx-amdcccle_ (--configure):
 dependency problems - leaving unconfigured
_dpkg: dependency problems prevent configuration of fglrx-dev:_
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.

_dpkg: error processing fglrx-dev_ (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

After these all I ran fast into synaptic and tried to find if some of these packages was broken ...nothing at all just keep getting the error from synaptic after i am typing broken in dependencies and trying to reinstall the installed archives are shown in there
[B]E: fglrx: subprocess installed post-installation script returned error exit status 3
E: fglrx-amdcccle: dependency problems - leaving unconfigured
E: fglrx-dev: dependency problems - leaving unconfigured[/B]
> Atlasts in a whole sentence I tried
To fix broken dependencies 
Going to edit and fix broken packages in synaptic

Erros 
> [I]E: fglrx: subprocess installed post-installation script returned error exit status 3
E: fglrx-amdcccle: dependency problems - leaving unconfigured
E: fglrx-dev: dependency problems - leaving unconfigured

and[/I]

[I]Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1[/I])

I am just a silly boy trying to prove myself that Linux Can play games in more than 20 FPS :P

LinuxMint Petra 16 
AMD Radeon 6550D

---

### Post by oldrocker99 on 2014-05-13
OK, when you see "dependency problems," do this:

```
sudo apt-get -f install
```

This should bring in the necessary dependencies and then install fglrx (and, as a nVidia user, I feel your pain).

---

### Post by R33D3M33R on 2014-05-14
The cause of the crash was fglrx not being installed properly at all. Don't forget to run:

```
sudo amdconfig --initial
```

after you fix problems with oldrocker99's suggestion.

---

### Post by john173 on 2014-05-14
> Fast quote 
I am don't use Nvidia i have APU familly Radeon 6550D as you said sth about invidia and  I don't get it :D
```

So started with *sudo apt-get install* and resultsuser@user-desktop ~ $ sudo apt-get -f install
[sudo] password for user:
```
 ```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up fglrx (2:13.251-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-13.251 DKMS files...
Loading new fglrx-13.251 DKMS files...
Error! DKMS tree already contains: fglrx-13.251
You cannot add the same module/version combo more than once.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 3
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.

dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.

dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-20-generic
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

And i have already did that when i installed the amd drivers
```
user@user-desktop ~ $ sudo amdconfig --initial
[sudo] password for user: 
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-2
user@user-desktop ~ $ 

```

Then reboot


I am trying a way to keep the amd drivers and fix crashed cinnamon 


[SIZE=4][FONT=arial]Thank you for your support :)[/FONT][/SIZE]:guitar:

---

### Post by slickymaster on 2014-05-14
Moved the thread to the **General Help** sub-forum, as it's more adequate than Gaming & Leisure.

---

### Post by R33D3M33R on 2014-05-14
Did you only install fglrx from the Ubuntu repository or did you also manually downloaded the installer and tried installing?

---

### Post by john173 on 2014-05-14
Thank you R33D3M33R i though i had already done that but ...

 **_Remove_**  and **_Install_** again  fglrx , fglrx-amdcccle and fglrx-dev
 Games like   ***LoL***    using wi ne have for me   ***20 fps***   about *** more***  an  d  ***Catalys t*** seems*** working*** 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
 The WORST IS THAT I CAN NOT SEE THE MINT ICON NEXT TO THE MENU GRRR>..hope i may find a way to fix it :D 
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[SIZE=3]**Thank you all for your support**[/SIZE] the solved way was preety easy and '*silly*' for dumps like me :P


Now ..... [SIZE=5]GONNA GET THE PARTY STARTED !!![/SIZE]:guitar:

---

