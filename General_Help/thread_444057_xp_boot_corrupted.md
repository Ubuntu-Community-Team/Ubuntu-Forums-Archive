---
title: "xp boot corrupted"
date: 2007-05-15
forum: General Help
---

### Post by HossTB27 on 2007-05-15
I'm going to begin this by saying that I am entirely new to Linux all together, but have been playing around with with PC's and Windows for over 10 years now.  I was curious and foolish and decided to install Kubuntu late last night with near disastrous results.

My hard drive is 320 gigs, but for some reason, Windows only partitioned something like 137 gigs of the HD for the operating system and my various files.  Therefore, I had about 190 gigs of space to use for Linux.  I created another partition and used one part of it for the installed files and the other portion for the swap file.  Kubuntu installed and ran perfectly.  Grub worked perfectly as well.

However, I wanted to test XP in order to make sure that it worked.  I selected the OS and was greeted warmly with the blue screen of death.  I wasn't too worried as it's happened before.  I ran chkdsk in the recovery console and was told that everything seemed to check out.  However, when I ran chkdsk /p in order to do a full check, the console said that something was corrupted and wasn't fixable.  I rebooted, but I automatically booted to Windows rather than Grub, only to be greeted by "NTLDR missing".  I looked up the message on these forums and on Google, tried to replace the file via the recovery console and also tried to run fixboot as well as bootcfg.  I still see the same error message when I boot to XP.  I do not understand why I recieved the fatal error message at first and then the new error message (NLTDR).

The final bit of information that I have found truly puzzling is this: I have another hard drive which also has XP on it.  I wanted to see if I could boot from that HD and manually view the files through My Computer.  However, when I explore the drive, there are only a few inaccessible files and folders present.  More interestingly enough, the properties for the drive only indicate a max space of 10 MB compared to the 320 gigs that it should say.  Or at least 90 gigs, which was the smallest partition.

I almost left out anther piece of information.  I booted my 320 using the Kubuntu boot disk in order to see if there were manual boot options that I was missing.  When I tried booting from the disk,my computer froze.  Even worse, when I was browsing through the system recovery, the partitioner didn't recognize any partitions, even the original NTSF partition.  I have absolutely no idea where to proceed from here.  If anyone has any suggestions as to how to restore XP or at least allow me to recover what I can from the C drive, it would be most extremely appreciated.

Thank you in advance to any one who responds to this.  I'd like to be able to move on from this incident unscathed and enjoy Kubuntu to it's full potential and not have this leave a bad taste in my mouth!

---

### Post by joe.turion64x2 on 2007-05-15
A few days ago a friend told me his 300GB drive failed. I don't want to scare you but if I were you I would try to recover the files through Ubuntu (it reads NTFS, doesn't it?) and reinstall everything (just in case).

Have you moved something in the BIOS? I remember I saw that same message some day I moved in the BIOS the setting AUTO to MANUAL in the IDE devices section for my hard drive.

Joe.

---

### Post by luis.torres.gomez on 2007-05-15
First to all install automatix

[http://getautomatix.com](http://getautomatix.com)

then install NTFS suport with automatix

next

try with 

```
sudo fdisk -l
```

and list the windows partition

maybe sda1 or sda2 etc..
next edit boot.ini

and change the number of partition.


reboot

---

### Post by HossTB27 on 2007-05-15
I don't really know how to install the software through Linux.  Grub doesn't load  when I boot.  I suppose whenever I tried rewriting the boot information, it ignored Grub and went straight for the XP settings.  How can I access Linux otherwise?  I tried the boot disk and my computer would just hang while it loaded and froze.  I browsed around and haven't been able to see anything that informs as to how to boot without the loader.

I have not changed anything in BIOS and my IDE cables are fine.  My other HD loads like it always has.  The problem occurred immediately after I installed Linux and Grub.

I am unable to install that program as I do not know how to get into Linux without Grub.  Like I said, I'm completely new and am in need of serious help.  Thanks for your speedy reply!  It is greatly appreciated!

---

### Post by joe.turion64x2 on 2007-05-15
> **HossTB27 said:**
> I don't really know how to install the software through Linux.  Grub doesn't load  when I boot.  I suppose whenever I tried rewriting the boot information, it ignored Grub and went straight for the XP settings.  How can I access Linux otherwise?  I tried the boot disk and my computer would just hang while it loaded and froze.  I browsed around and haven't been able to see anything that informs as to how to boot without the loader.

I have not changed anything in BIOS and my IDE cables are fine.  My other HD loads like it always has.  The problem occurred immediately after I installed Linux and Grub.

I am unable to install that program as I do not know how to get into Linux without Grub.  Like I said, I'm completely new and am in need of serious help.  Thanks for your speedy reply!  It is greatly appreciated!
I have experienced issues with BIOS before, perhaps you can try to load its setup defaults.

---

### Post by HossTB27 on 2007-05-15
I restored the default BIOS settings and rebooted, only to be greeted with the same message.  I believe the key is to restore Windows via Linux, but I don't know how to boot Linux without Grub...

---

### Post by joe.turion64x2 on 2007-05-15
Ok, it was not the BIOS. I remember years ago when I used a SUSE installation disk to boot my Linux system when I needed to recover it. The only drawback of this method is that it will load another kernel, but as far as I know it works. Another idea, if you have more disk space available is to install another Linux and use its grub, or perhaps there is method to reinstall GRUB for Ubuntu.

---

### Post by celticbhoy on 2007-05-15
did you install ubuntu from a live disk?

if so then you could re-install ubuntu over the same partitions you used before, which should sort the grub problem, leaving the NTLDR prob.

---

### Post by Herman on 2007-05-15
> My hard drive is 320 gigs, but for some reason, Windows only partitioned something like 137 gigs of the HD for the operating system and my various files. Therefore, I had about 190 gigs of space to use for Linux. I created another partition and used one part of it for the installed files and the other portion for the swap file. Kubuntu installed and ran perfectly. Grub worked perfectly as well. Could this possibly have anything to do with the famous 137 GB BIOS hard drive size limit?
Would it help to update your BIOS with a newer version from your motherboard manufacturer if there is one available?
                                      You can check the date of your computer's BIOS by going into 'setup' by pressing the appropriate key during the early stages of booting, something like this: [    Getting Product Information]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Getting_Product_Information").
                                     
                                     Here is a list of BIOS hard disk limits and some approximate dates when these ways to overcome these limits were invented. 
                                      2.11 GB or 4095 cylinder limit
                                      3.26 GB or 6322 cylinder limit
                                      4.22 GB or 8192 cylinder limit                                        .................(around 1997 or earlier)
                                      8.45 GB Standard INIT13 limitation (CHS[1024x256x512)....................(around late 1990s)
                                      33.8 GB or 66,060,287 LBAs limitation...........................................................(August 1999)
                                      137 GB or 268,435,455 LBAs limitation (28-bit limit)...............................(September 2001)
                                     
                                     You could check at your motherboard manufacturer's website, (find it with google), to see if there is a newer update for your machine's BIOS available. If so, you can download it and try 'flashing' your BIOS'.

Regards, Herman :)

---

### Post by HossTB27 on 2007-05-15
Booting from the local disk didn't work with the install CD.  I tried reinstalling both the OS and Grub but was hesitant when no partitions were shown.  When the partitioner is loaded during the installation, it only recognizes 320.1 gigs of space.  It doesn't recognize the original 137 from XP or either the partition in which Linux was installed or the swap partition.  I noticed that I had the option of installing Grub on the disk without partitioning the HD, but I wanted to confirm that it wouldn't mess anything up more than it's been already messed up.  Once Grub is loaded, I think I can start making some progress.

As for the BIOS settings, I really don't understand how that could be playing a role in this when they've been fine for a few years now, but immediately after Grub and Linux were installed, XP wouldn't boot.  It seems to me to be a problem related to the partitions and the boot files.

Thanks again to everyone who's responded!

---

### Post by joe.turion64x2 on 2007-05-16
> **HossTB27 said:**
> Booting from the local disk didn't work with the install CD.  I tried reinstalling both the OS and Grub but was hesitant when no partitions were shown.  When the partitioner is loaded during the installation, it only recognizes 320.1 gigs of space.  It doesn't recognize the original 137 from XP or either the partition in which Linux was installed or the swap partition.  I noticed that I had the option of installing Grub on the disk without partitioning the HD, but I wanted to confirm that it wouldn't mess anything up more than it's been already messed up.  Once Grub is loaded, I think I can start making some progress.

As for the BIOS settings, I really don't understand how that could be playing a role in this when they've been fine for a few years now, but immediately after Grub and Linux were installed, XP wouldn't boot.  It seems to me to be a problem related to the partitions and the boot files.

Thanks again to everyone who's responded!
I hope I am wrong but perhaps your hard drive is screwed. I replaced my laptop's hard drive because Linux detected some bad sectors, after that I disabled those sectors (deleted the Windows partition which contained them) and finally installed another Linux distribution in some of the freed space. The result was that the MBR was lost and although I could boot the machine using the latest GRUB PCLinuxOS installed, when I ran Gparted it showed me an empty hard drive (just like yours). Perhaps the best idea would be to boot with a LiveCD and back up everything (if you can see the partitions of course).

Joe.

---

### Post by xzero1 on 2007-05-16
Give this a try, it worked for me. Still, I have to use a cd to boot windows.
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

---

### Post by Herman on 2007-05-16
> for some reason, Windows only partitioned something like 137 gigs of the HD for the operating system and my various files> As for the BIOS settings, I really don't understand how that could be playing a role in this when they've been fine for a few years now, Okay sir, whatever you say. :)
I can only take the information you provide and try to work with that. 

By the way, what kind of computer is it anyway? And what is the BIOS version? if you can provide more information it could be useful. 

I agree with xzero1, I recommend that link for too, for those who are having severe problems booting Windows, download on of the NTLDR CDs from that site, they are very good.  [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Regards, Herman :)

---

### Post by HossTB27 on 2007-05-16
Okay, first I'll start by saying that I haven't checked the BIOS type and updates.  I had a bunch of stuff to do today and just didn't have the chance.  However, I did get the idea to test the partitions via the XP boot disk.  XP recognized one partition on the disk, a small, FAT partition (ironic, right?).  I'll research my BIOS and try flashing the update and also try the other boot disk.  I'm still clinging to a very small ounce of hope that my system can be recovered, but my hope is slowly dwindling.

Secondly:

> **Herman said:**
> Okay sir, whatever you say. :)
I can only take the information you provide and try to work with that. 

By the way, what kind of computer is it anyway? And what is the BIOS version? if you can provide more information it could be useful. 

I agree with xzero1, I recommend that link for too, for those who are having severe problems booting Windows, download on of the NTLDR CDs from that site, they are very good.  [http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Regards, Herman :)

I don't mean to sound the way I might have come off.  My apologies if my frustration over XP is flowing into my fingertips and onto this thread.  I only mean harm to Bill Gates and Microsoft; the antithesis of Linux users.

---

### Post by strixy on 2007-05-16
> I only mean harm to Bill Gates and Microsoft; the antithesis of Linux users.

I beg to differ... I love how he/they continue to push their users away from their product by making them criminals without their knowledge or permission. Once my wife started researching the new Vista OS, she came to me and asked if I could teach her how to use Linux.

See... silver lining :) 

As for your problem, I would have suggested using two HD's, one for each OS, had I gotten to your curiosity to try Linux earlier.

I'm pretty positive your BIOS needs to be updated and Linux needs to be reinstalled. let us know how that goes.

> I'm still clinging to a very small ounce of hope that my system can be recovered, but my hope is slowly dwindling.

No worries! it might not be an easy solution, but there is a solution. Remember how you felt the first time you booted into Windows? did you expect a different experience the first time you booted into Linux? Honestly now... I thought I knew Windows inside and out, and that somehow my mad Windows skills would translate to Linux. I admit, I was wrong 100%.

I've been using Linux since new years eve 2000, and while I almost threw my Red Hat CD's out the window every day for a year, I stuck with it and now you have to pay me to use Windows (which they do ;) ) - and I mean that literally.

I don't mean to sound preachy or like a some Linux hot head, but I'm willing to bet your frustration isn't so much with Linux, but rather with being a newbie all over again. If you learned Windows as well as you did you'll discover that you can do the same with Linux. Once you reach that point you'll never want to go back.

Stick with it man. The Kernel wasn't built in a day.

---

### Post by xzero1 on 2007-05-16
One thing that may help is using Ubuntu to explore your windows partition. There may be a log sitting on the drive that could help you resolve your problem. As a last resort, before you decide to reformat or reinstall windows, copy important data files into Ubuntu for safe keeping.

---

### Post by HossTB27 on 2007-05-17
> **strixy said:**
> I beg to differ... I love how he/they continue to push their users away from their product by making them criminals without their knowledge or permission. Once my wife started researching the new Vista OS, she came to me and asked if I could teach her how to use Linux.

See... silver lining :) 

As for your problem, I would have suggested using two HD's, one for each OS, had I gotten to your curiosity to try Linux earlier.

I'm pretty positive your BIOS needs to be updated and Linux needs to be reinstalled. let us know how that goes.



No worries! it might not be an easy solution, but there is a solution. Remember how you felt the first time you booted into Windows? did you expect a different experience the first time you booted into Linux? Honestly now... I thought I knew Windows inside and out, and that somehow my mad Windows skills would translate to Linux. I admit, I was wrong 100%.

I've been using Linux since new years eve 2000, and while I almost threw my Red Hat CD's out the window every day for a year, I stuck with it and now you have to pay me to use Windows (which they do ;) ) - and I mean that literally.

I don't mean to sound preachy or like a some Linux hot head, but I'm willing to bet your frustration isn't so much with Linux, but rather with being a newbie all over again. If you learned Windows as well as you did you'll discover that you can do the same with Linux. Once you reach that point you'll never want to go back.

Stick with it man. The Kernel wasn't built in a day.

I agree with everything you're saying.  My frustration isn't from Linux.  Rather, it's from my inability (thus far) to solve the issue.  I've been frustrated with Windows so long, I don't even notice the feeling anymore :)

Even though Linux isn't seeing any partitions when I boot from the install CD, would it be okay to install it in open space on the drive?  Again, I can see one FAT partition from the Windows boot disk and no partitions from the Linux boot disk.  It wouldn't make sense for the OS to be written over something else, but I just want to reassure some of my feelings.  I'll check into updating the BIOS shortly and get back later.

Thanks again!

---

### Post by HossTB27 on 2007-05-22
Hello all who are helping me.  I'm still here and I still have my problem.  I've been caught up with work etc in the past few days, basically leaving no time to do much at home.  However, I did manage to convince my father to install the 32-bit version of Kubuntu on one of his old computers and viola!  It worked!  Even though this version of Kubuntu is running fan-freakin-tastic on a machine that's over seven years old, I still have yet to flash the BIOS and try some of the other suggestions posed.  I will definitely get to it this weekend.  I just didn't want everyone to think that I've given up already!

---

