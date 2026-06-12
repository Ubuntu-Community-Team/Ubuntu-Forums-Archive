---
title: "Kernel image issues with installing software"
date: 2015-09-27
forum: General Help
---

### Post by MrMe01 on 2015-09-27
Hi folks,

When I try and install software with apt-get or a .deb from CLI, I get told to run this

```
[FONT=monospace][COLOR=#000000]apt-get -f install[/COLOR][/FONT]
```
 Running that errors out with
```
 [FONT=monospace][COLOR=#000000]Errors were encountered while processing: [/COLOR]
 /var/cache/apt/archives/linux-image-3.19.0-28-generic_3.19.0-28.30_i386.deb 
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/FONT]

```

Googling for the the issue that dpkg gave me pointed me to this [http://ubuntuforums.org/showthread.php?t=1720469](http://ubuntuforums.org/showthread.php?t=1720469)

Naturally, I ran 

```
dpkg --configure -a
```

and that errors out with 
```
 [FONT=monospace][COLOR=#000000]dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-28-generic: [/COLOR]
 linux-image-extra-3.19.0-28-generic depends on linux-image-3.19.0-28-generic; however: 
  Package linux-image-3.19.0-28-generic is not installed. 

dpkg: error processing package linux-image-extra-3.19.0-28-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.19.0-28-generic; however: 
  Package linux-image-3.19.0-28-generic is not installed. 
 linux-image-generic depends on linux-image-extra-3.19.0-28-generic; however: 
  Package linux-image-extra-3.19.0-28-generic is not configured yet. 

dpkg: error processing package linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.19.0.28.27); however: 
  Package linux-image-generic is not configured yet. 

dpkg: error processing package linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 linux-image-extra-3.19.0-28-generic 
 linux-image-generic 
 linux-generic

[/FONT]

```

Any ideas on how to fix this?

---

### Post by Bashing-om on 2015-09-27
MrMe01; Hello;

Maybe try and follow the package manager's hint:
```

sudo apt-get install linux-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-image-extra-3.19.0-28-generic

```

I can foresee the possibility that " /var/cache/apt/archives/linux-image-3.19.0-28-generic_3.19.0-28.30_i386.deb " is corrupted. Maybe delete it ? // Nother thought, why install a 32 bit kernel ??? Most systems are 64 bit ! 

What are you doing here ?

[INDENT][INDENT][INDENT]clarity please
[/INDENT][/INDENT][/INDENT]

---

### Post by MrMe01 on 2015-09-27
It's an older laptop that doesn't have a 64 bit processor, hence the 32 bit kernel (IBM T41) 

I've ran apt-get clean , autoclean and purge and I still get the same responses. And what I'm trying to do is install software.

---

### Post by Bashing-om on 2015-09-27
MrMe01; Hokay ->

Anxiety relieved . 32 bit hardware.
So, what results with the attempts to install :
```

sudo apt-get install linux-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-image-extra-3.19.0-28-generic

```

AND, is the system otherwise up-2-date ?

[INDENT][INDENT]progress made, slowly
[/INDENT][/INDENT]

---

### Post by MrMe01 on 2015-09-27
It was updated 2 days ago, once I had finished installing it. Installed from a bootable USB drive.
Upon running the commands, it tells me to run apt-get -f install.

---

### Post by Bashing-om on 2015-09-27
MrMe01; Well ... well ...

Let's
```

sudo rm /var/cache/apt/archives/linux-image-3.19.0-28-generic_3.19.0-28.30_i386.deb
sudo apt-get purge linux-generic
sudo apt-get purge linux-image-generic
sudo apt-get purge linux-image-extra-3.19.0-28-generic

sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install linux-generic
sudo apt-get install linux-image-generic
sudo apt-get install linux-headers-3.19.0-28
sudo apt-get install linux-headers-3.19.0-28-generic
sudo apt-get install linux-image-3.19.0-28-generic
sudo apt-get install linux-image-extra-3.19.0-28-generic

```

If there are any errors please post the command and the complete outputs.

[INDENT][INDENT][INDENT]we take it up from there
[/INDENT][/INDENT][/INDENT]

---

### Post by MrMe01 on 2015-09-28
All of these commands come back with this,
```
 [FONT=monospace][COLOR=#000000]Reading package lists... Done [/COLOR]
Building dependency tree        
Reading state information... Done 
linux-generic is already the newest version. 
You might want to run 'apt-get -f install' to correct these: 
The following packages have unmet dependencies. 
 linux-image-extra-3.19.0-28-generic : Depends: linux-image-3.19.0-28-generic but it is not going to be installed 
 linux-image-generic : Depends: linux-image-3.19.0-28-generic but it is not going to be installed 
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
[/FONT]
```

---

### Post by dino99 on 2015-09-28
you seems having a borked file related to that kernel inti /var/lib/dpkg/info
so, if you have at least one other kernel installed, other than this faulty 3.19.0-28, purge all the related linux-headers/linux-image (3.19.0-28) following that blog example:   [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

but i wonder if your hardware support PAE (as all actual kernels have it built-in)
[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

---

### Post by mörgæs on 2015-09-29
> **dino99 said:**
> 
but i wonder if your hardware support PAE (as all actual kernels have it built-in)
[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

The link is partly obsolete. Only Workaround 4 is valid today.

More here:
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by MrMe01 on 2015-09-29
> **dino99 said:**
> you seems having a borked file related to that kernel inti /var/lib/dpkg/info
so, if you have at least one other kernel installed, other than this faulty 3.19.0-28, purge all the related linux-headers/linux-image (3.19.0-28) following that blog example:   [http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

but i wonder if your hardware support PAE (as all actual kernels have it built-in)
[http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present](http://askubuntu.com/questions/117744/how-can-i-install-on-a-non-pae-cpu-error-kernel-requires-features-not-present)

I had Debian on here before I installed Kubuntu as it has better (in this case) hardware (GPU) support for this machine. To get that to boot, I had to remove the boot flags for quiet and splash, and it was failing on PAE, I had to do forcepae to get it to boot, so I don't think it does have PAE, most report the maximum amount of RAM is 2 gig.

I've not tried much since I've tried it, but since rebooting with forcepae -- forcepae in grub, Muon has popped up with updates. I'll mark this as solved if I have no further issues.

Coincidentally, whilst searching for how to update grub with the flags, I came across this; [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105)

---

### Post by Bashing-om on 2015-09-29
MrMe01; Hey; Thanks;

Great find for the 'forcepae' work-a-bout .
Appreciate the sharing.

[INDENT][INDENT]take'n care
[/INDENT][/INDENT]

---

### Post by MrMe01 on 2015-09-29
No worries, hopefully this helps someone else (most likely me when I reinstall in a few months :P )

It seems to be some sort of silicon bug with Banias Pentium M processors. The processor supports (I think) PAE, but doesn't report that to the kernel so it gets confused. I'm gonna play and tinker with stuff for a day or two, make the machine my daily driver and report back here any issues I think are related to the forcepae / kernel issues I've had.

//correction, it does support PAE, [https://en.wikipedia.org/wiki/Pentium_M#Banias](https://en.wikipedia.org/wiki/Pentium_M#Banias)

 Debian KP'ed on every shutdown on this machine and eventually got worse to the point I had to reinstall, and as I've been somewhat amazed with recent advances with KDE and sddm, I thought I'd give it a go on here. It's slow at times and doesn't do a great job with video (YouTube) playback but is great for documents and general web browsing, plus it should help with a project that I have in mind :)

Thanks for all your help so far with this, much appreciated :D

---

### Post by Bashing-om on 2015-09-29
MrMe01; K;

Pentium M -> better support in (L)ubuntu .
A guide for getting computers with older Pentium M processors to work with the latest Lubuntu;
[https://help.ubuntu.com/community/PAE/PentiumM](https://help.ubuntu.com/community/PAE/PentiumM)
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

Now 14.04 Lubuntu has support for non-pae:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105) ->guide for getting computers with older Pentium M processors to work with the latest Lubuntu;
[https://help.ubuntu.com/community/PAE/PentiumM](https://help.ubuntu.com/community/PAE/PentiumM)
[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)


[INDENT][INDENT]old hardware need not die
[INDENT][INDENT][INDENT]just get better software
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

