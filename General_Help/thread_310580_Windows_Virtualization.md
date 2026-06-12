---
title: "Windows Virtualization"
date: 2006-12-01
forum: General Help
---

### Post by Entity` on 2006-12-01
I would like to run Windows XP under Ubuntu/Linux so whenever I need to do something that require Windows I would not have to restart my computer or something like that.  I would appreciate this as I have a system that can esily perform this if configured correctly

SPECS:
Dual 850 MHz PII (I think PIII, i dont no)
512 Mb of SDRAM
A whole bunch of hard drives of varying size the largest being 30GB

It also has a strange but seemingly useful TV tuner made by the now extinct STB Systems.  If I can Ill get Pics for yall later.
The system is more a server than anyting else but wi treat it more like a normal system than anything else.

---

### Post by LLRNR on 2006-12-01
[Here](http://ubuntuforums.org/showthread.php?t=183209)'s the perfect thing for what you need, you'll love it... oh well at least I do :D

LLRNR

---

### Post by aussiedini on 2006-12-01
Hi I set up vmware player using automatix2 then went to [this site]("http://www.ffnn.nl/pages/articles/linux/vmware-player-image-creation.php") to get an empty xp image file. If you follow the instructions you can install XP in vmware. I run it and works well, with minimal lag.

---

### Post by Entity` on 2006-12-03
Thanks and heres another question...
After Installation, can I make it so that ONLY Vmware uses ONLY Pocessor 2 so I can pretty much use both operating systems at the same time with no lag?

I know that somewhere out there there is a near-perfect answer for my question.

---

### Post by Mike'sHardLinux on 2006-12-04
You only have 512MB of RAM total. :-k  That won't leave much for the guest OS. I'd bet it'll run slow. Maybe usable, maybe not.

My .02.

On my main desktop(Pentium D820), I have 3GB of RAM and give 1GB to the guest OS. That works pretty good. On another system (Athlon64 2800+), I have 1GB and give 512MB to the guest OS. Often, it's a bit sluggish running apps like Photoshop CS and CorelDraw X3.

Sorry, I don't know about making Linux only use cpu 1, and guest OS only use cpu2, but I really doubt that is possible. If it is possible, I bet it'd be a LOT of work to configure (or program) it.

Almost forgot, 850MHz is definitely P3. I have a Dell Poweredge 2450 that is Dual P3 850 on which I have Ubuntu Server, just for experimentation.

---

### Post by Entity` on 2006-12-05
256MB for each OS is fine for me cause once I had an ubuntu pc that had 256MB of ram and it ran fine.

Now WinXP can run with 128 MB of ram at the very least and Ive had success with running it with 256MB of ram.  If I can hunt down the make and model of my servers MOBO, (intel (BOOO!!!) chipsets all over it)) I can see if it can support more than 512MB of ram.  Im pretty sure im out of luck there...

Now I someone out there that knows how to make certain programs use certain CPUs.
As with Windows, Im sure you can do it with Linux, except that its INcanlulably harder.

---

### Post by salbrecht on 2006-12-05
I have a question in the area of Windows Virtualization also.  I hope this is an appropriate thread to post this.

Hardware:
Dell Inspiron XPS Laptop
3+ghz HT cpu
2 gb ram
ATI Video, 256 mb ram. Screen is 1920x1200 pixels and 32 bit depth.

I have installed Microsoft Virtual PC 2004
I downloaded ubuntu-6.10-desktop-i386.iso

I start VPC, set up a machine with 512 mb ram.
I then drag the ISO file to the CD icon and Ubuntu loads and starts up.

The problem is that Ubuntu starts up in a screen resolution that renders the VPC display unreadable.  I am unable to read any of the text so I can change the screen resolution set-up.  Booting Ubuntu into the second menu choice (save screen mode) results in the same scrambled display.

So it seems that Ubuntu loads and runs just fine, I just can't read the display. 

Any thoughts on how I can set up the display before I boot Ubuntu?

Thanks folks

---

