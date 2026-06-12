---
title: "Questions on VirtualBox - Trouble with Guest XP on seperate partition"
date: 2008-03-22
forum: General Help
---

### Post by Adman on 2008-03-22
Hi all

Please can someone help me with a problem I'm having. My apologies if this is in the wrong category but this seemed most appropriate.

Background info
-------------------

I am using Linux Mint version 4.0 which afaik is based on Ubuntu 7.10. I installed the newest binary version of Virtualbox and was very excited because I could finally move over to Linux while still using the few Windows programs I require for work. I was very excited about the seamless mode!

Since I had a previous Windows installation, I looked around, and I read that it is possible to import the installation into Windows using a .VMDK File.

I followed the instructions in two tutorials:
[http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/](http://blarts.wordpress.com/2007/12/06/how-to-run-virtualbox-using-a-physical-partition-using-ubuntu-feisty-fawn/)
[http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html](http://n00buntu.blogspot.com/2007/11/howto-ubuntu-compiz-virtualbox-part-1.html)

I completed the installation and opened the VBox.

Problem
---------

Once the VM started, I found that it was fast to boot, but incredibly incredibly slow once in Windows. It took almost 30 minutes to load 1/2 of the applications that are installed. In addition to this, it is difficult to do anything because of the lag that I'm having. Eventually, I managed to get the guest software installed, but then ran into mouse problems as well.

Please can someone help because I'm really eager to get this working.

Thanks a lot

---

### Post by Islington on 2008-03-22
How much video mem have you given it?  turn off virtual xp, go into settings for the machine and see what happens when you bump up the vid mem to 128 mb.

edit: should be under the general tab.

---

### Post by Adman on 2008-03-22
Thanks very much for the info.  I have only 128 MB of video memory, so I didn't want to allocate the full amount to the VM.  Can I allocate the full amount?

I've tried everything between about 24MB and about 110 though, if that helps...

---

### Post by Islington on 2008-03-22
I too have only 128mb, After bumping it up to the maximum, I have not seen any system slowdowns. When you gave it the 110 mb did xp move faster?

Edit: how much base memory does xp have?

---

### Post by Adman on 2008-03-22
It did move faster, but still way too 'buggy' to actually use.  Thought it might be related to the image file or already existent windows installation though...  I have read about VMs and it doesn't _seem_ like the system requirements are that hectic.  

Please note: I'm not suggesting that the VirtualBox is buggy, but rather something that I'm doing wrong in the process ;)  I've seen videos of it working brilliantly.

---

### Post by Victormd on 2008-03-22
I think the better question is: What is your hardware? How much system mem? How much system mem did you allocate for XP? I believe that a minimum 512 is required for XP...
If you have a newer processor, you might be able to enable virtualization under BIOS which will further improve your speeds...

---

### Post by Adman on 2008-03-22
Yes, sorry, should've included this earlier:

I'm running an AMD Athlon 64 X2 4200+, with 2GB RAM, and a GeForce 6600GT (128MB).

I've tried varying somewhat the RAM and Video Memory allocations...

---

### Post by Victormd on 2008-03-22
Ok, you've got a good system, now we just have to set it up properly...
First, you may want to check your BIOS to see whether the AMD X2 4200+ has virtualization capabilities "Virtualization on desktop computers allows a single PC to act like multiple virtual machines. AMD Virtualization can enable client computers to seamlessly support multiple operating environments." (source AMD X2 4200+ specs)
Next, I think you will have to allocate at least 512 for XP to run well... maybe set it to 768 since you have 2GB)
The video memory, you can set it to 64MB. Virtual machines normally don't have the same graphical capabilities as the native OS so setting it to 64 or 128 shouldn't make that much of a difference (I think)...
Check these out and let us know what happens...

Just a thought. Did you install from the repos? If so, remove it and install the non-OSE version (still free though) from [www.virtualbox.org](www.virtualbox.org) (this will give you USB access).  Also, installing the guest extras will further improve performance...

---

### Post by Adman on 2008-03-22
Thanks very much for the advice.

I will give that stuff a try.  

I thought that what was slowing it down was that I installed an already existent windows installation via an image (i.e. didn't install it via the VM) and that it was on a completely separate partition.  As a result, something might be in conflict.

I will try this stuff and get back to you ;)  

Btw, I tried to install the binary from [www.virtualbox.org](www.virtualbox.org), but I had errors.  Will look into this again :)

Thanks

---

### Post by Kiri on 2008-03-22
If you have a windows cd, why dont you try installing a fresh version of xp on a virtual disk and see if it is a problem of installing with your existing partition or not...
I didnt even know that was possible in vbox by the way.

---

### Post by Adman on 2008-03-22
I'll definitely give that a try Kiri.  Thanks for the good advice.

VictorMD - Thanks a lot for all your help.  Unfortunately, I think it's only the 2006 and > (AM2) architechtures that have virtualization support.  My processor is a little bit older.  

I took your other advice and tried it out, but it didn't help much on the performance side... Anything else you guys can think of??

Thanks again

---

### Post by Kiri on 2008-03-22
One other thing I can think of. If you have your current XP accessing virtual memory or swap files, it might be getting confused now that it is in the vm. 
Try resetting them in windows, or changing them. Also, other things like location of drives may have changed and is causing confusion...? 
Or XP may still expect it has 2gb of Ram when it now has much less, and that could explain it... 
Not sure how you could fix that though. 

How much RAM are you allocating it in the VM setup?

Go into the my computer properties when it is running and see how much ram windows is showing. Is it the same?

---

### Post by Adman on 2008-03-22
Hehe

I think the new installation would answer many of these questions we are having.

It is almost impossible for me to access anything in the VM!  So I won't be able to tell you how much RAM it is utilizing.  When I ran it a few minutes ago, I had allocated 1GB to it.  I think I might re-install windows completely... Just have to gather the courage with all the work I have to do in the next few weeks ;)

---

### Post by Kiri on 2008-03-22
Its a shame you cant get it working properly though. I would actually like to do the same thing, so I was curious to see how you go :)

How long has your windows been installed?
Ive heard that the longer it has been installed the more complications you might have converting it to VM.
If its a fairly new install, it might go much more smoothly. (but that kind of defeats the purpose doesnt it?)

---

### Post by Adman on 2008-03-22
It certainly does defeat the purpose!  
My Windows installation is probably over a year old already.  So it kind of makes sense why it's giving me so much trouble then ;)

I will let you know if I manage to find out what I'm doing wrong.  I'm looking now at installing the SCSI drivers that are released here: [http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/](http://mazimi.wordpress.com/2007/06/24/virtualization-of-an-existing-physical-partition-of-windows-within-linux/)

---

### Post by Kiri on 2008-03-22
You might also try vmware server. There is a sticky at the top of virtualization forum about exactly what you are trying to do...

---

