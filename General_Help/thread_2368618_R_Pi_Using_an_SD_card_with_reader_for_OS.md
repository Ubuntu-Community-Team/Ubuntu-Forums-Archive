---
title: "R Pi: Using an SD card with reader for OS"
date: 2017-08-13
forum: General Help
---

### Post by webmiester on 2017-08-13
Hi guys,

I am replacing our old computers with new Raspberry Pis (RPi)using ubuntu Mate.  Now the thing is, the old computers ran off Windows XP and I decided that I can run them off ubuntu Mate too with the same customiztions I did for the RPis so that we will have the same ecosystem throughout our company.  Now, these computers have old hard disks which are probne to crashing soon.  Also, I figured, I want to boot ubuntu off from a USB drive because 1) They are easier to clone than a harddrive, so I can customize 1 unit, then make clones for the others, 2) They are easier to replace in case of failure as compared to a harddrive 3) They consume much less energy which I hope may help the computers' power supplies to last longer.

Here are my questions:

1) The computers are Core2Duo's which means they are 64-bit, but they are also just have 2GB RAM.  Should I use the 32-bit Ubuntu or 64-bit ubuntu (64-bit because their processor is 64-bit, but 32-bit because of the RAM).

2) I will actually be using micro-SD Cards mounted on a USB card reader for booting.  Will this be equivalent to a USB pendrive or are their other complications I might encounter from this plan?

3) I plan to remove the hard disks and load the OS directly from the USB card reader.  Will there be any problems with doing this?

4) Lastly, if the micro SD card and reader is transferred to another computer with a different set of specs, will ubuntu be able to change its settings and boot up properly?  In my experience windows crashes on boot-up when the hard disk with Windows from a different computer is transferred to another one with a different setup.  How about ubuntu, will it do the same, or will it still be able to boot up properly?

5) Also, will the 32-bit ubuntu consume less space on the flashdisk than the 64-bit version?  I only have 16GB space per micro SD Card

Thanks so much?

---

### Post by QIII on 2017-08-13
As a general comment, the R Pi does not perform well enough to be a full blown PC replacement, particularly for a production environment.  It can perform passably for light tasks, such as web browsing, word processing and other office productivity.  Something like the ODROID XU4 or even the C2 would be more capable and they have more memory.  The C2 costs only about $10US more than the R Pi.

> **webmiester said:**
> 
1) The computers are Core2Duo's which means they are 64-bit, but they are also just have 2GB RAM.  Should I use the 32-bit Ubuntu or 64-bit ubuntu (64-bit because their processor is 64-bit, but 32-bit because of the RAM).

I would use the 64bit version.  

> 2) I will actually be using micro-SD Cards mounted on a USB card reader for booting.  Will this be equivalent to a USB pendrive or are their other complications I might encounter from this plan?

Can you mount from a USB device?  No, not out of the box.  But see my comment under your item 3.

Regardless, MicroSD cards do not last long under the sort of read/write conditions that would be encountered in a production environment.  The speed of SD cards is abysmal. Although the speed and data transfer rate of USB 2 devices is pretty slow, it is much faster than SD.  MicroSD cards are fine for storage of data files that are not moved often.  You would be better off simply using USB devices.  You can even use a powered USB disk enclosure with a mechanical laptop drive.  That's what I do. Don't use an SSD with a Pi.  Commands like TRIM cannot be passed via USB.  You would end up with write magnification and full erasure blocks that would be unusable.

> 3) I plan to remove the hard disks and load the OS directly from the USB card reader.  Will there be any problems with doing this?

Out of the box, the Pi *will not boot directly from a USB device and must boot from a microSD*.  However, many people, including me, run R Pis and other SBCs from USB devices.  That is often accomplished by modifying the image on the SD card to mount on /boot and then turn the operation over to / on a USB device.  You can go one step better on the R Pi Model 3 B by setting a bit in the firmware to allow them to boot directly from the USB.  That's what I have done with mine.

> 4) Lastly, if the micro SD card and reader is transferred to another computer with a different set of specs, will ubuntu be able to change its settings and boot up properly?  In my experience windows crashes on boot-up when the hard disk with Windows from a different computer is transferred to another one with a different setup.  How about ubuntu, will it do the same, or will it still be able to boot up properly?

Forget Windows experience for a bit.  Windows != Linux.  Provided you do not add any proprietary drivers (not really an issue with the R Pi), in the vast majority of cases you will have no problem using the same card on another SBC.

> 5) Also, will the 32-bit ubuntu consume less space on the flashdisk than the 64-bit version?  I only have 16GB space per micro SD Card

That difference is negligible.  But again, I would highly recommend against the use of SD cards in a production environment.

---

### Post by C.S.Cameron on 2017-08-13
I have not tried any heavy benchmarking yet, but it seems to me that there is not much difference running an OS from a micro SD card in an USB card reader and from a flash drive. I think nowadays Ubuntu, (Puppy and other OS's), mainly run in RAM, (if there is enough RAM).

Occasionally the screen goes grey and freezes up when using memory intensive programs and browsers, but I have seen this happen when installed on mechanical hard drives also.

My RPi runs Kodi great but I would not try it as a CAD workstation.

Flash drives are said to be good for a minimum 10000 writes and have wear leveling but I have not heard about the life span of a SD card.

---

### Post by vocx on 2017-08-13
> **webmiester said:**
> Hi guys,

I am replacing our old computers with new Raspberry Pis (RPi)using ubuntu Mate.  Now the thing is, the old computers ran off Windows XP and I decided that I can run them off ubuntu Mate too with the same customiztions I did for the RPis so that we will have the same ecosystem throughout our company.  Now, these computers have old hard disks which are probne to crashing soon.  Also, I figured, I want to boot ubuntu off from a USB drive because 1) They are easier to clone than a harddrive, so I can customize 1 unit, then make clones for the others, 2) They are easier to replace in case of failure as compared to a harddrive 3) They consume much less energy which I hope may help the computers' power supplies to last longer.

Here are my questions:

1) The computers are Core2Duo's which means they are 64-bit, but they are also just have 2GB RAM.  Should I use the 32-bit Ubuntu or 64-bit ubuntu (64-bit because their processor is 64-bit, but 32-bit because of the RAM).

2) I will actually be using micro-SD Cards mounted on a USB card reader for booting.  Will this be equivalent to a USB pendrive or are their other complications I might encounter from this plan?

3) I plan to remove the hard disks and load the OS directly from the USB card reader.  Will there be any problems with doing this?

4) Lastly, if the micro SD card and reader is transferred to another computer with a different set of specs, will ubuntu be able to change its settings and boot up properly?  In my experience windows crashes on boot-up when the hard disk with Windows from a different computer is transferred to another one with a different setup.  How about ubuntu, will it do the same, or will it still be able to boot up properly?

5) Also, will the 32-bit ubuntu consume less space on the flashdisk than the 64-bit version?  I only have 16GB space per micro SD Card

Thanks so much?
I'm not sure I follow you correctly. You want to replace the Windows computers running XP, with Raspberry Pi computers? You have used a Pi before? You do understand they boot from an SD card, not from a hard drive. Although you would probably need to attach an USB drive to increase the hard drive space, as with an SD card you probably will have less than 64 GB of space.

Also, about the architecture. You are confusing me. The RPi uses an ARM microprocessor and system on chip. This means it is not a 32-bit (x86) or 64-bit (x86_64) computer like the common desktop or laptop with an Intel or AMD CPU. The processor it has is similar to a mobile phone processor. This means all software needs to be available specifically for the ARM architecture. The ARMv7 in the RPi I think it's a 32-bit processor, while other mobile phones use the newer ARMv8 which is 64-bit. This refers to the low level instruction set, which requires recompilation of programs for the ARM CPU. So, you cannot just dump a .deb from the normal Ubuntu repository and install a program there, it will not work as it's binary incompatible.

It is hard for me to comment more, because I am not sure you understand everything about the requirements for running the RPi. If you want to run generic stuff like Python programs, or even LibreOffice, it should work, because there are ARM versions of those programs for the Raspberry Pi. But running more things, specially heavy programs that require a lot of RAM, the RPi is not a good solution.

> **C.S.Cameron said:**
> ...
Flash drives are said to be good for a minimum 10000 writes and have wear leveling but I have not heard about the life span of a SD card.
All flash drives, USB memory drives, RAM sticks, SD cards, etc. use the same basic technology which is called "solid-state memory". It is based on transistors instead of rotating magnetic materials like traditional hard drives. So, unless the technology is widely different, I'd expect they all have about the same lifetime and degradation behavior.

---

### Post by cariboo on 2017-08-13
I'd suggest if you are planning on using the older systems, you look around for some used hard drives, I have several sitting in a box in the 400GB - 500GB range that I haven't found a use for yet. Check out local LUGS or other computer clubs to see if there is anyone willing to help you out.

---

### Post by C.S.Cameron on 2017-08-13
I guess it depends what your company does with the Win XP / RPi computers, If you are making lots of money at it, please let me know of any IPO.

Good thread: [https://superuser.com/questions/17350/whats-the-life-expectancy-of-an-sd-card](https://superuser.com/questions/17350/whats-the-life-expectancy-of-an-sd-card)

For the record I bricked a 2TB and a 4TB mechanical drive plugged into my RPi a month ago, nothing is perfect.

---

### Post by webmiester on 2017-08-13
Hi guys,

I am so sorry.  I think my statements were kinda vague and confusing.  Even my title is wrong.  I dont remember typing in "R Pi" in the title.  I really appreciate your comments, but I think I wasnt able to send my question properly.  I am really sorry.

Thank you for bearing with me.  For clarification, the RPis are already in place and will be replacing old Microsoft XP based computers.  They will only use web browsers so it is fine.  I was able to get the printers to work, so they will do great.  So far, I have 1 installation which has been running for 3 months without problems, so I hope the others will follow suit.

OK, my question was about the old Microsoft XP computers.  I wanted to replace the Windows XP with Ubuntu Mate and customize them so they will look and feel just like the RPis.  The computers are Core2Duo with 2GB ram.  I want to remove their hard disks (Hard disks of the PCs not the RPi), and boot out of a USB MicroSD card reader with a 16GB Class 10 Micro SD card installed.  It will be easier to clone these Micro SD cards than it is to clone hard drives.  In case of SD card failure, I am hoping it wont be so hard to rebuild one from a stored image, so we will have all the cusotmizations and drivers already present upon rebuilding a card.  I will just need to stock up on enough of these microSD cards to last long since as mentioned, they might not last that long.

My questions were all directed to the Windows based PCs and not the RPi's.  The RPi's are already done.  What I want to do is make my PCs look and feel like the RPis so that the staff will have the same ecosystem throughout our system.

Thank you so much for your comments.  I really appreciate them.  I am sorry for the ambiguity of the way I wrote my question.  Illl try to be clearer next time.

webmiester

---

### Post by webmiester on 2017-08-13
> **QIII said:**
> As a general comment, the R Pi does not perform well enough to be a full blown PC replacement, particularly for a production environment.  It can perform passably for light tasks, such as web browsing, word processing and other office productivity.  Something like the ODROID XU4 or even the C2 would be more capable and they have more memory.  The C2 costs only about $10US more than the R Pi. 

Thank you, I considered the Odroid too.  In the end, I chose the RPi 3 because it has a larger community to draw experience from.

> **QIII said:**
> I would use the 64bit version.  

Thanks.

> **QIII said:**
> Can you mount from a USB device?  No, not out of the box.  But see my comment under your item 3.

Regardless, MicroSD cards do not last long under the sort of read/write conditions that would be encountered in a production environment.  The speed of SD cards is abysmal. Although the speed and data transfer rate of USB 2 devices is pretty slow, it is much faster than SD.  MicroSD cards are fine for storage of data files that are not moved often.  You would be better off simply using USB devices.  You can even use a powered USB disk enclosure with a mechanical laptop drive.  That's what I do. Don't use an SSD with a Pi.  Commands like TRIM cannot be passed via USB.  You would end up with write magnification and full erasure blocks that would be unusable.

Out of the box, the Pi *will not boot directly from a USB device and must boot from a microSD*.  However, many people, including me, run R Pis and other SBCs from USB devices.  That is often accomplished by modifying the image on the SD card to mount on /boot and then turn the operation over to / on a USB device.  You can go one step better on the R Pi Model 3 B by setting a bit in the firmware to allow them to boot directly from the USB.  That's what I have done with mine.

Thank you.  Although I was referring to the PCs not the RPi regarding booting from USB card reader (I think the way I wrote my question was quite vague, its my fault, I will word my questions better next time) this answer is quite useful.  I did see some youtube videos where their RPis would boot from USB, and was wondering how they did this.  Your response will be helpful for future projects :)

> **QIII said:**
> Forget Windows experience for a bit.  Windows != Linux.  Provided you do not add any proprietary drivers (not really an issue with the R Pi), in the vast majority of cases you will have no problem using the same card on another SBC.

That difference is negligible.  But again, I would highly recommend against the use of SD cards in a production environment.

Yeah, I am trying to get rid of windows.  One of my dreams before was to come up with a Linux-based Windows simulator for students who insist on learning windows, hahaha.  It wil run linux and have an environment which looks and feels just like windows.  Unfortunately, that project didnt pass with government school regulators, so I have to return to windows.  But this is still in my mind though.

---

### Post by webmiester on 2017-08-13
> **C.S.Cameron said:**
> I have not tried any heavy benchmarking yet, but it seems to me that there is not much difference running an OS from a micro SD card in an USB card reader and from a flash drive. I think nowadays Ubuntu, (Puppy and other OS's), mainly run in RAM, (if there is enough RAM).

Occasionally the screen goes grey and freezes up when using memory intensive programs and browsers, but I have seen this happen when installed on mechanical hard drives also.

My RPi runs Kodi great but I would not try it as a CAD workstation.

Flash drives are said to be good for a minimum 10000 writes and have wear leveling but I have not heard about the life span of a SD card.

HI, the quality of the SD cards vary greatly from manufacturer to manufacturer I think.  In our case, we will only be using it for web browsing.  A local server runs a web application which does the heavy weight lifting.  The server runs on ubuntu server and LAMP :).

---

### Post by webmiester on 2017-08-13
> **vocx said:**
> I'm not sure I follow you correctly. You want to replace the Windows computers running XP, with Raspberry Pi computers? You have used a Pi before? You do understand they boot from an SD card, not from a hard drive. Although you would probably need to attach an USB drive to increase the hard drive space, as with an SD card you probably will have less than 64 GB of space.

Also, about the architecture. You are confusing me. The RPi uses an ARM microprocessor and system on chip. This means it is not a 32-bit (x86) or 64-bit (x86_64) computer like the common desktop or laptop with an Intel or AMD CPU. The processor it has is similar to a mobile phone processor. This means all software needs to be available specifically for the ARM architecture. The ARMv7 in the RPi I think it's a 32-bit processor, while other mobile phones use the newer ARMv8 which is 64-bit. This refers to the low level instruction set, which requires recompilation of programs for the ARM CPU. So, you cannot just dump a .deb from the normal Ubuntu repository and install a program there, it will not work as it's binary incompatible.

It is hard for me to comment more, because I am not sure you understand everything about the requirements for running the RPi. If you want to run generic stuff like Python programs, or even LibreOffice, it should work, because there are ARM versions of those programs for the Raspberry Pi. But running more things, specially heavy programs that require a lot of RAM, the RPi is not a good solution.


All flash drives, USB memory drives, RAM sticks, SD cards, etc. use the same basic technology which is called "solid-state memory". It is based on transistors instead of rotating magnetic materials like traditional hard drives. So, unless the technology is widely different, I'd expect they all have about the same lifetime and degradation behavior.


Thank you for bearing with me and sorry for my vague question.  I built a lot of RPi units to replace our Windows based XP computers.  They will only use browser, so its quite light work for the RPis and the PCs would be overkill...

Now, what would I do with the old Windows XP based computers?  Should I junk them?  Well, I decided that some of them can be reused by installing Ubuntu Mate on them and making them look and fell just like the RPis.  In this case, whether our staff uses the PCs or the RPis, they will have the same ecosystem.  So my questions were on the PCs converted to run Ubuntu.  Should I use 32-bit or 64-bit?  Is it adviceable to boot them off a USB card reader instead of a hard disk (since the micro SD cards are faster to setup are faster to setup), etc.

Thank you so much.  After going through some comments I realize that I should have versed my questions more clearly.

---

### Post by webmiester on 2017-08-13
> **cariboo said:**
> I'd suggest if you are planning on using the older systems, you look around for some used hard drives, I have several sitting in a box in the 400GB - 500GB range that I haven't found a use for yet. Check out local LUGS or other computer clubs to see if there is anyone willing to help you out.

Thanks, I have more then enough hard drives as of the moment.  The reason for choosing the micro SD cards were for the speed of setting up a unit.  It might be faster to clone a MicroSD card than a hard disk.

---

### Post by webmiester on 2017-08-13
> **C.S.Cameron said:**
> I guess it depends what your company does with the Win XP / RPi computers, If you are making lots of money at it, please let me know of any IPO.

Good thread: [https://superuser.com/questions/17350/whats-the-life-expectancy-of-an-sd-card](https://superuser.com/questions/17350/whats-the-life-expectancy-of-an-sd-card)

For the record I bricked a 2TB and a 4TB mechanical drive plugged into my RPi a month ago, nothing is perfect.

Thank you so much.  I am sorry to hear about your bricked devices.  Did you figure out what bricked your 2TB and 4TB hard drive?  Did you do a process (like a command) which broke it, or do you think the RPi just isn't suited for that kind of work?  I was kinda thinking that the RPi can work as a NAS... Just install SAMBA on it, then put in a large USB hard disk...  With your comment though, I am starting to think it might not be a good idea.

---

### Post by vocx on 2017-08-13
> **webmiester said:**
> Thank you for bearing with me and sorry for my vague question.  I built a lot of RPi units to replace our Windows based XP computers.  They will only use browser, so its quite light work for the RPis and the PCs would be overkill...

Now, what would I do with the old Windows XP based computers?  Should I junk them?  Well, I decided that some of them can be reused by installing Ubuntu Mate on them and making them look and fell just like the RPis.  In this case, whether our staff uses the PCs or the RPis, they will have the same ecosystem.  So my questions were on the PCs converted to run Ubuntu.  Should I use 32-bit or 64-bit?  Is it adviceable to boot them off a USB card reader instead of a hard disk (since the micro SD cards are faster to setup are faster to setup), etc.

Thank you so much.  After going through some comments I realize that I should have versed my questions more clearly.
LOL. Okay, now I understand.

So, eh, my official answer is, eh, install 64-bit Ubuntu, and run it from the hard drive. Why not SD card? Well, I don't know. Maybe it can be done as you wish but I haven't done it myself, so I wouldn't know if it'd be better in any way. As long as you keep your Ubuntu in a minimal state, that is, without too many packages, I think you should be able to clone the drive relatively fast.

There is an ubuntu-minimal image that probably you can try. You may start with no desktop, then add MATE, then the file manager, then the browser, and so on. That is, you start with the minimum, and build your system with only the things you need. Probably it will only take about 4 GB of hard disk space, or about the same as the basic Raspberry Pi image.

---

### Post by C.S.Cameron on 2017-08-14
> **webmiester said:**
> Thank you so much.  I am sorry to hear about your bricked devices.  Did you figure out what bricked your 2TB and 4TB hard drive?  Did you do a process (like a command) which broke it, or do you think the RPi just isn't suited for that kind of work?  I was kinda thinking that the RPi can work as a NAS... Just install SAMBA on it, then put in a large USB hard disk...  With your comment though, I am starting to think it might not be a good idea.

The Hard drives might have broke due to me not completely understanding if the RPi was running or not when yanking them out. 
Since then I have only connected Mechanical HDD's to the RPi through wireless and have not had any problems.

---

### Post by webmiester on 2017-08-19
I recently plugged in 2 USB hard drives into one of my RPi 3 to copy files from one hard disk to the other.  Now one hard disk was a Tourno brand USB hard disk while the other one was one was an older hard disk which I just  placed inside a USB casing.  What I noticed was that in many times, the Tourno hard disk would sound an alarm indicating that it wasn't receiving enough power.  The hard disk I assembled using the USB casing did not sound an alarm most probably because the USB kit it came in didn't have an alarm circuit and buzzer.  So its possible that my assembled hard disk may also be suffering from a low power state but did not give any indication.

Now a few years ago, I also encountered this problem with a seagate external hard disk.  All the files which I wrote on the Hard Disk when it was alarming due o low power also disappeared.

My theory is that prolonged use of these hard disks in low power states will end up destroying them, and this could have been what bricked your hard disks.  I miss those external hard drives with cables that had 2 USB male plugs on one end (1 or data and power plus a second only for power).  With these cables, we can plug the hard disk to a separate USB power supply.  The other option now would be to use a USB powered hub.

---

### Post by webmiester on 2017-08-19
This is very good.  Thanks so much.

---

### Post by efflandt on 2017-08-19
External drive enclosures that use laptop drives typically work fine powered by USB. But since a drive typically uses 5V 1A and USB 2.0 spec's only require it to provide 500 mA (0.5A), some include a USB cable with 2 USB plugs for the computer end (2x500 mA).

I think external desktop drives usually include a power supply. I have a USB/eSATA drive caddy that has its own power supply, but it is 2 slots, and can clone one drive to another without even being connected to a computer. But it is an old one and its PSU only provides 5V & 12V, so it does not work for 3.3V 1.7A mSATA SSD in SATA adapter (which works in any SATA PC or laptop).  If you clone any drive or SD/microSD, you should make sure that hostname on each is unique (and LAN IP if static). It would likely help to have unique UUID for partitions on them too if more than one is connected to same computer at a time at some point, but that would require updating that in /etc/fstab & /boot/grub/grub.cfg.

If you look at suggestions for what to do with SSD's it can give some clues that you might implement for SD/microSD, like disabling cache for firefox or something for chrome browser. For a tablet PC that came with Win7 Pro on 32 GB SSD, booting Ubuntu from 32 GB SD (slot internally USB connected), I have no swap and forget if I stuck to ext2 filesystem (no journal). But it is 2 GB with slow AMD C-50 2-core 1 GHz, so I do not use it very often (used to use it for field programming electronic controllers in awkward locations underground with Windows software). But I am unemployed or retired now (haven't decided).

---

