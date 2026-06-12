---
title: "Trouble installing nvidia drivers in 6.10"
date: 2006-12-21
forum: General Help
---

### Post by shred_thrash on 2006-12-21
Hey all,

I recently switched to ubuntu after many problems with SuSE and I am having some issues with installing drivers for my nvidia video card.  I have read through 2 different how to's with no success so I finalling decided that I was going to check out the forums and ask for some help.  Is there anyone that would be able to give me a quick walkthrough of installing nvidia drivers on ubuntu 6.10. 

Thanks so much in advance,

Cheers!

---

### Post by xopher on 2006-12-21
What have you done exactly?

Things you need to do, basically, aren't that many:

1. ```
sudo apt-get install nvidia-glx
```
2. Edit the device driver from whatever it is, eg. nv in /etc/X11/xorg.conf to nvidia
3. Restart X [CTRL+ALT+BACKSPACE] - Before showing the GDM login screen you should see a NVIDIA splash screen if you haven't disabled it.
4. Voilà.

PS. There's also a program that'll fix your xorg.conf for you, maybe someone else can remember what it's called. I don't , because I've never let apps configure my vital configuration files. :rolleyes:

---

### Post by shred_thrash on 2006-12-21
That seems a heck of a lot easier than the tutorials that I found through google.  They had something upwards of a 20 step process for doing all of it and I don't even remember what it was exactly that I did, all I know is that by the end, it didn't work.

Thanks a lot man,

Cheers!

---

### Post by shred_thrash on 2006-12-21
Hey, I just ran "sudo apt-get install nvidia-glx" from the command line and I was told that "it" was unable to connect to a source and some archives weren't downloaded?

Is there another way to do this?

Here's exactly what the output looked like:

Could not resolve 'security.ubuntu.com'
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.17/nvidia-glx_1.0.8776+2.6.17.6-1_i386.deb)  Could not resolve 'security.ubuntu.com'
E:Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Hope this helps, thanks a lot in advance,

Cheers!

---

### Post by fragos on 2006-12-21
Ubuntu has supported, universe and multiverse repositories.  You may need only have access to the main supported repositories.  Select System-> Administration-> Software Sources and it will help yoy add the universe and multiverse repositories.  Then you'll be able to install nvidia-glx.  You need not go to the command line to do this.  On the Administration menu you used above select Synaptic Package Manager.  Much easier to use than apt-get.

---

