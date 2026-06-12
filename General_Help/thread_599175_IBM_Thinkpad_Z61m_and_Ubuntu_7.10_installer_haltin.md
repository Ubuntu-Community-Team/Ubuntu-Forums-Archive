---
title: "IBM Thinkpad Z61m and Ubuntu 7.10 installer halting"
date: 2007-11-01
forum: General Help
---

### Post by shdwsclan on 2007-11-01
Well, I was screwing around with ubuntu, until to the point that i completely corrupted the partition. 
I used a live disk to run fsck on the drive, fixed error 17 in grub, was able to boot into windows and back up my files off of the linux partition using some r/w ext drivers for windows.

Anyways, I messed up ubuntu so bad, that it was complaining about fluxbox and halt and saying somethign about job control....some smartass made a crack about moving to openSUSE since there is no other solution[which i am considering].

Basically, running the regular installer in 7.10 loads while the bar bounces back and forth under the ubuntu logo....then x screensaver kinda loads, flashes intermittenly, and just shows a black console screen with a flashing underscore....except nothing works except the power button.....ctrl+shift+f1, nor f2, esc, none of the usual escape keys....

Using the safe graphic mode....screengibberish appears and then it drop to a very small resultion on console where all the "starting...." are really HUGE

It stops on "* Running local boot scripts (/etc/rc.local)
The only difference is ctrl+shift+f1 responds and shows the console

I try "start x" and nothing.....


7.09 x86_64 works fine....with all drivers...including the builtin webcam....

Laptop is a Z61m  G6U  9450  
It has an ATI X1400 GPU

---

### Post by technodigifreak on 2007-11-08
I too have a Lenovo z61m with the ATI x1400 graphics card.

I had feisty installed and working just fine since the day after it's release in April.  I upgraded my HDD to a 250GB and decided to do a fresh install of Gutsy.  Upon running the install CD I get the same results as you do.  Everything is fine until it tries to run X and then it throws errors about not being able to start successfully and then becomes unresponsive to keystrokes.  

I then downloaded the Feisty CD again, and same result (X failure), even though it worked before (in April).  :mad:

Next I grab my netinstall Etch disk.  Pop it in and it installs just fine.  I login to the desktop and try to load the fglrx drivers so that I could get the full resolution on my laptop.  The driver installs without problems, so I reconfigured X to use the new driver and set it to the proper resolution.  After reconfiguring it, I restart X and ..............  BAM .........X failure again.  I rolled it back to the default Etch X config (Using VESA driver) and have a working desktop at least, but Ubuntu is basically a lost cause right now because of the live CD/driver combination.

So, long story short it appears to be a bug in the updated version of the fglrx drivers.  

Their are two bugs listed on the [Gutsy Release Notes]("https://wiki.ubuntu.com/GutsyGibbon/ReleaseNotes") page, both of them seem to be different descriptions of this same issue.  So, while technically this is an upstream issue, it directly affects user's ability to even install Ubuntu.....Not Good (TM).

---

