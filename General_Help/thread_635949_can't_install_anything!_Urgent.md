---
title: "can't install anything! Urgent"
date: 2007-12-09
forum: General Help
---

### Post by Steve05TSX on 2007-12-09
I don't know what's going on here.  I did a reformat so I could do a  dual boot with WinXP.  I'm trying to configure back Ubuntu 7.10 the way I had it, but I can't!  I've been googling all night and morning, now I'm sick of it. 

I can't install envy.  I get an error "Error dependency is not satisfiable: xserver-org-dev

I can't install ndiswrapper to install my wifi.  I get this

steve@steve-desktop:~$ cd ndiswrapper-1.5/
steve@steve-desktop:~/ndiswrapper-1.5$ make
make -C driver
make[1]: Entering directory `/home/steve/ndiswrapper-1.5/driver'
Can't find kernel sources in /lib/modules/2.6.22-14-generic/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/steve/ndiswrapper-1.5/driver'
make: *** [all] Error 2
steve@steve-desktop:~/ndiswrapper-1.5$ cd ndiswrapper-1.5/
steve@steve-desktop:~/ndiswrapper-1.5/ndiswrapper-1.5$ sudo make
make -C driver
make[1]: Entering directory `/home/steve/ndiswrapper-1.5/ndiswrapper-1.5/driver'
Can't find kernel sources in /lib/modules/2.6.22-14-generic/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/steve/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make: *** [all] Error 2
steve@steve-desktop:~/ndiswrapper-1.5/ndiswrapper-1.5$ sudo make install
make -C driver install
make[1]: Entering directory `/home/steve/ndiswrapper-1.5/ndiswrapper-1.5/driver'
Can't find kernel sources in /lib/modules/2.6.22-14-generic/build;
  give the path to kernel sources with KSRC=<path>             argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/steve/ndiswrapper-1.5/ndiswrapper-1.5/driver'
make: *** [install] Error 2
steve@steve-desktop:~/ndiswrapper-1.5/ndiswrapper-1.5$ 


That's what I get when I follow the instructions on there.  Synaptic won't let me download it either.  When I click on it it says "The list of applications is not available, click reload"

---

### Post by p_quarles on 2007-12-09
First, I think you may have a broken package somewhere that's preventing APT from working correctly. Try this to fix it:
```
sudo apt-get -f install
sudo apt-get update
```
If that works, let's check why Envy doesn't want to work:
```
sudo apt-get install xserver-org-dev
```
If there's a problem with this package, the output will tell you more specifically what it is. 

For ndiswrapper, I have a hunch that you don't have the build tools installed. Try this:
```
sudo apt-get install build-essential
```
If that doesn't clear up the problem, try installing the specific dependencies needed for that package, with this command:
```
sudo apt-get build-dep ndiswrapper
```
Hope that helps.

---

### Post by Steve05TSX on 2007-12-09
I got ndiswrapper installed, but envy is still not working.  I did all the updates and stuff

when envy did work and download the drivers, next time I booted up it didn't load any of the video drivers . I had to boot into recovery mode and take off  those drivers

ndiswrapper still isn't allowing me to follow [http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828) that website to install my drivers

---

### Post by Steve05TSX on 2007-12-09
now it won't even boot.  it loads up ubuntu, but when it gets to the screen it just stays dark.  I can actually log in (blindly) and hear the sounds, but can't get a display

---

### Post by p_quarles on 2007-12-09
Can you boot into "recovery" mode? You shouldn't need the nVidia driver for that.

---

### Post by Steve05TSX on 2007-12-09
> **p_quarles said:**
> Can you boot into "recovery" mode? You shouldn't need the nVidia driver for that.

only thing that ever lets me do is stay in prompt mode.  Then when I restart my computer it will but it, but without my video drivers.  I then try to install my video drivers via Envy and it says it can't recognize my video card.

something has gotta be missing that I did a couple days ago.  It wasn't half the headache this is now.  I can't even install ndiswrapper, it gives me those errors as seen in the first post.  I never had those before, it just installed right away.

---

### Post by p_quarles on 2007-12-09
Have you tried running the commands I suggested in my first reply? What is the output?

---

### Post by Steve05TSX on 2007-12-09
> **p_quarles said:**
> Have you tried running the commands I suggested in my first reply? What is the output?

yeah sorry.  I did it before posting this thread too.  It loaded up a few things and did whatever it did fine, no errors

still pops up the same problem on installation of ndiswrapper

---

### Post by p_quarles on 2007-12-09
You said earlier that the problem with Envy is that when you run it, you get this:
```
Error dependency is not satisfiable: xserver-org-dev
```
So, you're saying that you've now installed that package, and still can't get Envy to install the driver?

---

### Post by Steve05TSX on 2007-12-09
> **p_quarles said:**
> You said earlier that the problem with Envy is that when you run it, you get this:
```
Error dependency is not satisfiable: xserver-org-dev
```
So, you're saying that you've now installed that package, and still can't get Envy to install the driver?

actually I got past that point.  I got envy to start downloading the drivers by changing the repository settings.  They are installed but I can't see the display

---

