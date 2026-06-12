---
title: "Req. Help to Start Over using Ubuntu"
date: 2013-01-05
forum: General Help
---

### Post by fergie716 on 2013-01-05
Hey community, first off I would like to say thank you for everything on this site and all who have helped, I have learned so much by searching and reading.  This is my 1st post here, I waited weeks to install Ubuntu to make sure I have read enough and knew what I was doing.  Installation went fine (I have a Toshiba laptop, running Windows 8 (came packaged)).  I installed Ubuntu 12.10 a few days ago and have absolutely loved it.

Initially I only allocated 25 GB, I would like to allocate more space and also erase all of my current data on my Ubuntu partition.  I was also thinking about downgrading to 12.04 for stability reasons. I have read a bit on how to do this but I just wanted to make sure I was on the right path.  Here are the steps I was going to take (I don't need to backup any data from my current Ubuntu setup, all of my media and docs are on my Windows partition)

-Burn Ubuntu 12.04 to a DVD
-Reboot into GRUB and it'll automatically pick up on the CD (?)
-Make sure I am booted into the live CD, use "Try Ubuntu" option
-Download gParted and delete (or format?) my Ubuntu partition
-Un-Mount my swap partition I created then delete it as well
-Reboot
-When computer reboots click "Install Ubuntu" and select the same partition I had before, as well as the same swap partition
-Let it install, if any issues run Boot Repair

Now, I didn't do anything with increasing the partition size because I think that's a bit above me.  However in the near future I would like to allocate more space to my Ubuntu partition but for now this will suffice

Here is a link of my current partitions if it could be of any help, the ext4 partition is my Ubuntu partition

[http://imgur.com/TOIUg](http://imgur.com/TOIUg)

Again, I really do appreciate any insight and thank you for posting all of this information

---

### Post by Bucky Ball on 2013-01-05
[QUOTE=fergie716]-Reboot into GRUB and it'll automatically pick up on the CD (?)[/QUOTE]

You need to change the boot order in the BIOS or by clicking the appropriate key(s) to bring up a screen to do that. On many machines this is F12, but it varies. The machine will not automagically boot from the CD (and grub has nothing to do with it).

If you are booted into the liveCD there is no reason to download Gparted. It is already there by default.

You don't need to do anything with /swap. Leave it where it is as the new install will pick it up and use it (if you manually partition when you get to that bit of the install then 'Use partition' but don't format, not that it matters).

You can install 12.04 right from the Try Ubuntu desktop, no reason to reboot. There is an icon on the desktop to do it.

From your diagram, there is nowhere to expand the EXT4 partition to. You would need to delete /swap, shrink /dev/sda4, expand the beginning of the EXT partition into the free space you have created and shrink it from the other end to recreate /swap (2Gb fine). This can all be done from the liveCD (as the partitions you are working with need to be unmounted.

---

### Post by fergie716 on 2013-01-05
> **Bucky Ball said:**
> You need to change the boot order in the BIOS or by clicking the appropriate key(s) to bring up a screen to do that. On many machines this is F12, but it varies. The machine will not automagically boot from the CD (and grub has nothing to do with it).

If you are booted into the liveCD there is no reason to download Gparted. It is already there by default.

You don't need to do anything with /swap. Leave it where it is as the new install will pick it up and use it (if you manually partition when you get to that bit of the install then 'Use partition' but don't format, not that it matters).

You can install 12.04 right from the Try Ubuntu desktop, no reason to reboot. There is an icon on the desktop to do it.

From your diagram, there is nowhere to expand the EXT4 partition to. You would need to delete /swap, shrink /dev/sda4, expand the beginning of the EXT partition into the free space you have created and shrink it from the other end to recreate /swap (2Gb fine). This can all be done from the liveCD (as the partitions you are working with need to be unmounted.
Thank you very much for the clarifications, I will go into BIOS and look for the boot order to change it

Once booted into the Live CD I can format my Ubuntu partition?

And after I delete (or format lol) my Ubuntu partition from inside the live cd I can just go to Install Ubuntu from the desktop without the intermediate reboot?

Thanks again for the help

---

### Post by Bucky Ball on 2013-01-05
> **fergie716 said:**
> 
Once booted into the Live CD I can format my Ubuntu partition?

And after I delete (or format lol) my Ubuntu partition from inside the live cd I can just go to Install Ubuntu from the desktop without the intermediate reboot?

Yes and yes. When you get to the partitioning section of the install choose 'Something Else' and you can partition manually. The EXT partitions are your Ubuntu ones, avoid everything else and check they are not set to be used or formatted as the last thing you do before finally confirming the changes (you can, of course, do a little resizing while you're there, though ... possibly better to do now that later while your heads in that zone ...).

And BTW; welcome to the forums. ;)

PS: One very important point in case you are intending this; **DON'T** resize the partition Win is installed on with Gparted. ***Always*** use the Win software to do this. You can end up with a real mess otherwise because it doesn't play nice with Linux (although XP was fine, anything after that isn't). Fine to resize other NTFS or FAT partitions but not the Win install. Cheers.

---

### Post by fergie716 on 2013-01-05
Thank you so much for the information sir, you have no idea how much I appreciate it lol.  Feel a lot more comfortable now.  I think I'll just do a clean install of 12.04 and go from there.  I'll do the resizing after in Win to be safe.

Gonna try and get into my BIOS and get it started.  Thanks again!

---

### Post by Pjotr123 on 2013-01-05
> **Bucky Ball said:**
> One very important point in case you are intending this; **DON'T** resize the partition Win is installed on with Gparted. ***Always*** use the Win software to do this. You can end up with a real mess otherwise because it doesn't play nice with Linux (although XP was fine, anything after that isn't). Fine to resize other NTFS or FAT partitions but not the Win install. Cheers.
I have used Gparted for resizing Windows system partitions for years and years, on hundreds of different machines. For Windows XP, Vista and 7. It was never a problem.... 

The underlying ntfsresize is a mighty tool for us mortals:
[http://linux.die.net/man/8/ntfsresize](http://linux.die.net/man/8/ntfsresize)

Reliable as can be, at least in my experience. :)

The only thing is, that Windows always wants to run CHKDSK upon first boot after a resizing. That's cool and expected, and never yields errors.

---

### Post by fergie716 on 2013-01-05
I have one last question, after I install 12.04 from the DVD to my hard drive I have to immediatly get back into BIOS and re order my boot order right?

---

### Post by Bucky Ball on 2013-01-05
> **fergie716 said:**
> I have one last question, after I install 12.04 from the DVD to my hard drive I have to immediatly get back into BIOS and re order my boot order right?

At the end of the install you should be asked to remove the CD and the machine will restart. You can set the BIOS back to booting from the hard drive then.

---

### Post by fergie716 on 2013-01-05
Bad news, towaards the end of the install I got this error

The grub-efi package failed to install to /target

The error said I wouldnt be able to load into system, I cant connwct to wifi on my laptop so  doing this on my phone

I have no idea whaf to do

---

### Post by fergie716 on 2013-01-05
I took the cd out, shut down PC and turnd it bk on

At a screen that says error: file /boot/grub/x86_64-efi/normal.mod not found.

grub rescue>

Its a command prompt wndow

---

### Post by fergie716 on 2013-01-05
Sorry Im blowing up this thread

If anyone xan help here is my pastebin

paste.ubuntu.com/1501608/

Thanks! I tried boot repair a few times to no avail

---

### Post by fergie716 on 2013-01-05
Hey guys, so 12.10 installs fine, it doesn't error out when installing grub (using USB Stick)

However, after installation is complete and I'm prompted to reboot it goes to the main ubuntu black selection screen (Try Ubuntu, Install Ubuntu etc)

I tried going back to the BIOS, changing the boot order then rebooting but it doesn't work it just goes back to that main black window

So, I installed 12.10 one more time, rebooted into a Live version on my USB stick and ran Boot Repair again.

Here is my most recent log

[http://paste.ubuntu.com/1502030/](http://paste.ubuntu.com/1502030/)

I also get this after boot repair finishes 

Please do not forget to make your BIOS boot on sda2/EFI/ubuntu/grubx64.efi file!

Now I noticed this, the /boot/efi label is missing from /dev/sda2, I compared my partitions that I'm seeing in this Live CD to the ones in the OP that I posted before this mess lol

If anyone could help me I would really appreciate it thanks guys and I'm sorry for posting so much kinda freaking out

---

### Post by Bucky Ball on 2013-01-05
Take the USB stick out, set BIOS to boot from the hard drive. Sounds like it is still just booting from the USB. Make that impossible.

---

### Post by fergie716 on 2013-01-05
> **Bucky Ball said:**
> Take the USB stick out, set BIOS to boot from the hard drive. Sounds like it is still just booting from the USB. Make that impossible.

Hey man thanks for your help, much appreciated.  I did try that (turn computer off, take out USB stick, enter BIOS and change boot order to Hard Drive) However I get a black screen that says File not found then right below it it says 

grub rescue>

I tried to read that error log and unfortunately it didnt make too much sense too me.  Through my searches I've found a few threads with similar things (Please make sure you set BIOS to load ...)

I've been at this for a few hours.. 12.04 didn't install but 12.10 did but after reboot it goes straight back to the main Ubuntu selection screen (Try First, Install, OEM Install)

I'm not too sure what to do.. On the bright side on my Live CD here I can access my Windows files and whatnot so that's not messed up

Trying to find someone smarter than me to decode that log.. But i do wonder if I edited the labels of /dev/sda2 to include /boot/efi like it previously did would do any good.. Or any harm lol

---

### Post by Bucky Ball on 2013-01-05
Well, you sound like you're heading in the right direction but EFI stuff is not my area, sorry ...

Have you tried Boot Repair from this point? You can make a bootable CD of that or install it to the Ubuntu LiveCD (yes, it will install there):

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That should enter all installed OSs to the grub menu and you're good to go ...

---

### Post by fergie716 on 2013-01-05
Ughh.. Yea me either lol. Say, do you think a computer repair shop or Best Buy could do the job? I have no more ideas besides adding those labels and I doubt that would do any good

---

### Post by Bucky Ball on 2013-01-05
Adding labels will help but most computer shops will shirk and cringe if you mention Linux ...

Perhaps post a new thread with a descriptive title addressing this current problem and as much info as you can muster. You might include a link back to this one.

---

### Post by fergie716 on 2013-01-06
This is true lol. Well Im gonna keep trying here, I'll try the labels thing and then run boot repair who knows. 

Ill keep searching the forums and keep anyone posted. And please if anyone has an odea or a link to another similar situation please share lol

But if i somehow fix it or come up with a breakthrough Ill update

Thanks again, means alot lol Im so upset that I cant figure this out #fail

---

### Post by fergie716 on 2013-01-06
> **Bucky Ball said:**
> Adding labels will help but most computer shops will shirk and cringe if you mention Linux ...

Perhaps post a new thread with a descriptive title addressing this current problem and as much info as you can muster. You might include a link back to this one.
Yea that's a good idea I didn't want to clog the forums tho.  I appreciate all the help sir, gonna start a new thread for my issue

---

### Post by fergie716 on 2013-01-06
Forum Staff:  Thank you so much for your help and suggestions.  I started a new thread here:  [http://ubuntuforums.org/showthread.php?p=12440841#post12440841](http://ubuntuforums.org/showthread.php?p=12440841#post12440841)

I really appreciate all the help, thank you

---

