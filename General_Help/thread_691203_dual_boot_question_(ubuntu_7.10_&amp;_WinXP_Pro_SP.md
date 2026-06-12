---
title: "dual boot question (ubuntu 7.10 &amp; WinXP Pro SP2)"
date: 2008-02-08
forum: General Help
---

### Post by xunil76 on 2008-02-08
i've got Ubuntu 7.10 installed on my hard drive right now, and i'm going to be installing WinXP onto a second partition on the same drive (following the instructions [here](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)).

when Ubuntu was installed, i allowed it to take over the entire hard drive, so it overwrote the MBR & everything.  the swap partition is a little over 2GB, and the rest of my 74GB raptor drive was allocated to another partition for my linux install.

so then i used GParted to partition off a ~30-ish GB partition for Windows XP to reside on.  i also created a PING image of my linux install, so that i can recover it easily if anything goes wonky (the image is stored on a second hard drive).

so my question is this:

when following the steps outlined in the article i linked above, when i install WinXP, it's going to take over as the main OS, and will only boot into itself, without allowing any option for anything else.  is it possible that once i have WinXP installed, that i can just re-load the linux image i created back onto the same partition that it currently resides on, to get it to boot back into linux again (since i'm going to assume that the MBR was also copied during the image creation process, as it was done before Windows was installed).....then continue on from there to add WinXP to GRUB?  would that work, or will it cause problems for WinXP?

i know i will likely have to go back into GParted and set the WinXP partition to not be the boot partition again, but otherwise, i'm thinking this should work, no?

the main reason i'm thinking to do this instead of doing as it says in the tutorial, and just booting into the Ubuntu LiveCD to reinstall GRUB, is because due to my hardware needing video drivers that are not included on the LiveCD, i will not be able to get to a desktop environment.

---

### Post by neurostu on 2008-02-08
>  is it possible that once i have WinXP installed, that i can just re-load the linux image i created back onto the same partition that it currently resides on, to get it to boot back into linux again (since i'm going to assume that the MBR was also copied during the image creation process, as it was done before Windows was installed).....then continue on from there to add WinXP to GRUB? would that work, or will it cause problems for WinXP? 

That might work... honestly the easiest thing to do after you have partioned your drive is to install win XP and then install ubuntu from the live CD.  You said that you already have a linux install on your HD, if this is just Gutsy Gibbon then a simple reinstall will take 30 minutes max which is far less time then it will take you to reconfigure grub on your own (if you have no experience working with grub). Plus when you re install gutsy it will take care of installing GRUB for you.

I have installed gutsy atleast 10 times after windows and each time it sets up grub perfectly!

> i know i will likely have to go back into GParted and set the WinXP partition to not be the boot partition again, but otherwise, i'm thinking this should work, no?

> the main reason i'm thinking to do this instead of doing as it says in the tutorial, and just booting into the Ubuntu LiveCD to reinstall GRUB, is because due to my hardware needing video drivers that are not included on the LiveCD, i will not be able to get to a desktop environment. when you install again just use the VESA drivers and the video card will work.

---

### Post by xunil76 on 2008-02-08
yeah, i'm not so much worried about setting up GRUB again, as long as restoring the image will basically do that for me, and it runs exactly the way it does now.  the WinXP install is the "novelty" install, as it were, and won't be running anything that i can't live without for a few days....my linux install, on the other hand, is what i do the majority of my computing in.

and i still think that if restoring the image works like i'm thinking, it will still take me less time to reconfigure GRUB to see the WInXP install than it would for me to go back through and re-customize my linux setup, since i've pretty much already got everything setup and configured the way i want it.

that's always been the biggest PITA to me, getting all my custom configuration settings re-done after an OS reinstall....

---

### Post by neurostu on 2008-02-08
Okay, that makes sense why you don't want to re-install ubuntu.  The imaged version of grub will not point to windows and you will have to manually set it. Or you can just reinstall grub and that will do it.

---

