---
title: "Hardy Wubi/Vista"
date: 2008-02-28
forum: General Help
---

### Post by tux_rox on 2008-02-28
Tuesday night I installed Hardy through Wubi and it's been great.  Today, however, I boot into Kubuntu, the progress bar gets to about 66%, and then it gives me a text-only error screen

init:  Unable to execute "/sbin/getty" for tty3:  Input/output error
init:  tty1 main process ended, respawning
init:  tty6 main process (4705) terminated with status 255

etc with many more tty processes until it eventually gives up.

I'm going to try booting into Kubuntu again and I'll see if it works.

---

### Post by ago on 2008-02-28
What version of wubi? Can you access the logs?

---

### Post by tux_rox on 2008-02-28
I'm pretty sure it's rev431 - I used the link from the FAQ's.

I can't access the logs (from Kubuntu, at least) - I've tried booting a couple more times and it crashes after the progress bar.  Can you access them from Windows?

---

### Post by ago on 2008-02-29
Try ctrl+alt+f2 to get to a console, from there the logs will normally be in /var/log. You may also want to try wubi 443+ with latest daily ISO.

---

### Post by mikegr on 2008-03-03
I get the same error. A lot of input/output errors. I cannot even log in. 

I used Wubi-8.04.431on an AMD 64 PC with XP. I haven't found any interesting log files on Windows. 

Any idea how to proceed?

---

### Post by NAM on 2008-03-03
Noob at ubuntu here: I would also like to know a solution as I'm getting the same errors. Sucks too because I had the official Nvidia driver installed finally and compiz working , as well as themes and icons. I've reinstalled like 6 times now due to other problems at first (like the nvidia driver) but I got through them all and Ubuntu stayed up and running well for a few days! (dual booting XP and Ubuntu) Now this! grrr. Should I just reinstall with the new build?

Installed with Wubi-8.04.431on an AMD 64 PC with XP

---

### Post by ago on 2008-03-03
Use wubi rev444 to get the logs. You will find them under /ubuntu if anything goes wrong during installation. Feel free to attach them here. Pls note that the password might be included within /var/log/installer/debug.

---

### Post by NAM on 2008-03-03
Hi ago, where can I get wubi 444?
*Meh, I think I'm just going to reinstall again, then reinstall the nvidia driver, compiz manager, etc, etc etc,  sigh. I won't give up!!!

---

### Post by ago on 2008-03-03
[http://www.wubi-installer.org/devel/minefield](http://www.wubi-installer.org/devel/minefield)

---

### Post by NAM on 2008-03-03
Thank you very much.

---

### Post by NAM on 2008-03-04
Anyone figure out a solution for this problem yet???

---

### Post by mikegr on 2008-03-05
I have tested again with rev. 446 and I get the same errors. Tried the first time 3 days ago, so I used already downloaded ISO file.
A boot time I get after selecting kubuntu in windows boot menu, but before booting of kubuntu I get this warning:

warning unrecognized partition table for drive 80. 
please rebuild it using MS-compatible fdisk (err=116)

Don't know if this is important hint. Guess no. 
 
During boot process I get a lot of input/output errors. No change to log in. No idea what now.

---

### Post by ago on 2008-03-05
> **mikegr said:**
> 
warning unrecognized partition table for drive 80. 
please rebuild it using MS-compatible fdisk (err=116)

Yes that might be relevant

Did you already tried chkdsk /r?

---

### Post by ago on 2008-03-05
> **mikegr said:**
> 
warning unrecognized partition table for drive 80. 
please rebuild it using MS-compatible fdisk (err=116)

Yes that might be relevant

Did you already tried chkdsk /r?

Try googling for "unrecognized partition table for drive"

---

### Post by NAM on 2008-03-06
Well I'm trying to do anything so I can avoid reinstalling at all costs so I dont have to reconfigure everything all over again. 

Here is a blurry picture of the errors Im getting now when I try to boot in recovery mode (version 8 not 10) I know its blurry but I'm sure its readable. I can type it out if need be.

 I know it shows a login name but I care not because I will change it later on if I get in or reinstall.

[IMG]http://i13.photobucket.com/albums/a284/Namuh/IMAG01432.jpg[/IMG]

---

### Post by ago on 2008-03-06
see if that helps: [http://ubuntuforums.org/showthread.php?t=636835](http://ubuntuforums.org/showthread.php?t=636835)

---

### Post by NAM on 2008-03-06
Hmm that sounds good but I cant log in to a desktop environment (or login at all , I get the tty error when I type in my user name and hit enter) so I cant apply these changes. How can I edit that file?
BTW, thanks for your help ago, I really appreciate it.

---

### Post by ago on 2008-03-06
You may try recovery mode or boot from another linux distro (or live CD), mount the virtual disk and edit the files

---

### Post by NAM on 2008-03-06
Thanks I'll burn the iso but when I boot from the disk how do I access the corrupted file, wont the disc just use its own files that are on the disc to boot?  How do I point it to look at the corrupted file so I can fix it, not its own tty file in its etc folder?
Oh ya and the screenshot I posted was from when I tried to boot in recovery mode. If I cant find a solution i'll just re install I guess heh heh. I love ubuntu but it's giving me a headache =) I won't quit on it though.

---

### Post by ago on 2008-03-06
> **NAM said:**
> Thanks I'll burn the iso but when I boot from the disk how do I access the corrupted file, wont the disc just use its own files that are on the disc to boot?  How do I point it to look at the corrupted file so I can fix it, not its own tty file in its etc folder?
Oh ya and the screenshot I posted was from when I tried to boot in recovery mode. If I cant find a solution i'll just re install I guess heh heh. I love ubuntu but it's giving me a headache =) I won't quit on it though.

You first mount the windows drive hosting the wubi disk with something like


sudo mount -t ntfs /dev/sda1 /mnt #assumes first windows partition of first HD

Then you mount the virtual disk in that drive

sudo mkdir -p /media/root.disk
sudo mount -o loop /mnt/ubuntu/disks/root.disk /media/root.disk

Now you can edit your wubi files that will be under /media/root.disk

---

### Post by NAM on 2008-03-09
Thanks ago, I went ahead and reinstalled using the rev444 file you pointed me too. BTW is rev444 for amd 64 or is it 32 bit? Hmm I didn't notice.

Ok, now Im in Ubuntu with a fresh install. (Im in ubuntu now!) 

1st things 1st, should I add all of the updates It found or should I go through them and pick which ones I want?  ( It says 10 updates found)

How do I know which ones to use and which ones can mess the installation up again?

Nvidia driver:Should I install the one Ubuntu tells me it has when I 1st boot that is in the upper right hand corner by the time or should I get it from Nvidias website and install it manually?

---

### Post by ago on 2008-03-09
> **NAM said:**
> Thanks ago, I went ahead and reinstalled using the rev444 file you pointed me too. BTW is rev444 for amd 64 or is it 32 bit? Hmm I didn't notice.
All wubi revisions will always use 64 bit ISO when a 64 bit processors (amd or intel) is detected.

> 1st things 1st, should I add all of the updates It found or should I go through them and pick which ones I want?  ( It says 10 updates found)
You can update everything, keep in mind that during alpha stage there are LOTS of upgrades. And sometimes they break things so that you either get to revert or wait for next batch of upgrades. I normally suggest to upgrade only after an official release (new alpha / beta). Things will stabilize soon.

> Nvidia driver:Should I install the one Ubuntu tells me it has when I 1st boot that is in the upper right hand corner by the time or should I get it from Nvidias website and install it manually?
Always  use Ubuntu drivers, unless you know EXACTLY what you are doing.

---

### Post by NAM on 2008-03-09
Thanks ago, really appreciate it. I think last time I used the Ubuntu drivers for my 8800 gt card it would not go up to 60 hz refresh rate which made compiz and moved windows tear alot. I did manage to install the nvidia driver from their site and it worked really well using instructions that I found here. Only prob I had was nividia installer crying about the li6 file but I managed to update that then get it installed. I think I ran into trouble when I started installing themes and icons heh heh.:oops:

---

