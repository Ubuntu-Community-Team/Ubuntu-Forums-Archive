---
title: "My PC doesn't want to boot or start."
date: 2007-01-02
forum: General Help
---

### Post by jcroot on 2007-01-02
Hi Guys, I would like to know if my PC has any solution at all, I mean a solucition because I think this is a serius problem or maybe isn't for some of you guys who know about this better than I do.

Note: I know this problem have to do with windows but it is related with Ubuntu Linux, so I hope I can get any help. read the last section.

Well here is my Problem, I have 2 Hard drives (40 Gbs each) I installed Windows XP Pro in the primary master hard drive and Ubuntu 6.10 on the second hard drive, it was working very nice, I was able to load any OS (windows or linux) using the GRUB Linux Boot... After a few weeks I started to see some problems with my windows system, My windows system shut down by it self so I turn my pc on again and try start windows as I was doing it before but now I have this error message:

Windows XP could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM 

To repair windows use the orginal CD and start the recovery console.

I don't know what to do guys, I boot my pc from my windows system and enter the recovery console but I only see a black screen to type some commands and I don't know what to do next.

In other forum I read about this type of problem and I followed this guys:

Boot from the cd. Do NOT do a repair using recovery console. proceed like you were doing a fresh install but BEFORE you select which disk to install to it will look for previous installs and ask if you want to repair it. DO NOT INSTALL A NEW COPY! Hit "r" to repair bt only when it shows you the previous install disk/directory not at the revovery console prompt!

So I followed the instruction but it din't work because I boot my PC from the windows xp pro CD and I procced like I was doing a fresh install so I look for the prevous installs but it didn't ask me if I want to repair windows so I cancel the instalation.

Now the other problem that I have is with ubuntu, my GRUB is not working, I think when I tried to install windows xp pro it deleted the linux boot or something like that, so now everytime I turn my pc on it says:

Windows XP could not start because the following file is missing or corrupt: \WINDOWS\SYSTEM32\CONFIG\SYSTEM 

To repair windows use the orginal CD and start the recovery console.

Note: None of my hard drives were formatted, I would like to solve this problems without deleting any file in my windows and linux systems, I would be waiting for any reply.

Thanks guys.

---

### Post by d3v1ant_0n3 on 2007-01-02
You were on the right track with the repair install of Windows.

When you insert the Windows cd, you procede as if you were going to do a fresh install of Windows, up to the point where you tell the installer where to put windows. When it brings up the partitions, it should recognise the windows partition and the fact that it has windows already there. There should be an option to perform a repair install at this point.

It will look like a regular install of windows, but should take much less time.

After you have repaired windows, you will need to restore GRUB. I've not done this before, but there are plenty of guides floating around these forums.

[ THIS](http://ubuntuforums.org/showthread.php?t=328799&highlight=windows+grub) was the first one I found (search keywords **GRUB Windows** )

---

### Post by smoker on 2007-01-02
you could try to repair the xp boot by entering the recovery console as you described above, then at the prompt type 'fixmbr' and then 'fixboot' without the quotes. just ignore any warning and 'y' to any questions.

you may have to replace some system files in xp if it will boot after the above, let me know if you get it booted up and i'll post instructions.

to reinstall grub, have a look at this link: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by jcroot on 2007-01-02
Thanks you guys for your reply, I'm reading carefully all your instructions and I will come with a reply as soon as possible, serious thanks for the help.

---

### Post by jcroot on 2007-01-02
> **d3v1ant_0n3 said:**
> You were on the right track with the repair install of Windows.

When you insert the Windows cd, you procede as if you were going to do a fresh install of Windows, up to the point where you tell the installer where to put windows. When it brings up the partitions, it should recognise the windows partition and the fact that it has windows already there. There should be an option to perform a repair install at this point.

It will look like a regular install of windows, but should take much less time.

After you have repaired windows, you will need to restore GRUB. I've not done this before, but there are plenty of guides floating around these forums.

[ THIS](http://ubuntuforums.org/showthread.php?t=328799&highlight=windows+grub) was the first one I found (search keywords **GRUB Windows** )

Thanks for your reply but it didn't work, boot my PC from the windows xp pro and I can't find an option that says: Press R for repair, I only found this option at the first windows setup screen but it is just for the windows recovery console.

---

### Post by riven0 on 2007-01-02
I'm not very knowledgeable about this, but... would it make a difference if unplug the hd with Ubuntu on it? Could it be that is messing things up?

---

### Post by jcroot on 2007-01-03
> **smoker said:**
> you could try to repair the xp boot by entering the recovery console as you described above, then at the prompt type 'fixmbr' and then 'fixboot' without the quotes. just ignore any warning and 'y' to any questions.

you may have to replace some system files in xp if it will boot after the above, let me know if you get it booted up and i'll post instructions.

to reinstall grub, have a look at this link: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

Thanks for your reply man but this didn't work, the fixmbr command and fixboot command work fine but it didn't make any difference at all, I still have the windows error message.

I'm not able to access my linux or windows system, I tried to restore the GRUB, I almost read all posts here: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)  

But none off all these options work, I don't know what else to do, I really don't want to losse any data in my windows or linux system, I will be waiting for any help.

---

### Post by jcroot on 2007-01-03
I also tried this: [http://support.microsoft.com/kb/307545](http://support.microsoft.com/kb/307545)
To solve my windows problem but it didn't work, my Local Disk in windows is: J insteaed of C so I did this:

delete j:\windows\system32\config\system
delete j:\windows\system32\config\software
delete j:\windows\system32\config\sam
delete j:\windows\system32\config\security
delete j:\windows\system32\config\default

and I get: Access denied

---

### Post by skwishybug on 2007-01-03
Assuming the issue for the Windows start is truly a corrupted or missing file, the following steps will replace it. The following assumes standardized drive letters, substitute your drive letters as appropriate

Load Windows install CD and open the recovery console. You should be at the D:\> prompt

Type in
*CD i386*

Then take a listing to see what system.xxx files are present

*dir system.**

The one we are most likely looking for here is system.ex_ as the destination file is a program.

Expand the program from the CD to the proper systemroot folder:

*expand system.ex_ c:\windows\system32\config*

If that does not work to replace the file, we will have to try something else.
If the file replaces, but it doesn't solve the boot problem for windows, you will have to look into the boot.ini file.

To restore GRUB go to:
[http://ubuntuforums.org/showthread.php?t=297548&highlight=restore+grubt](http://ubuntuforums.org/showthread.php?t=297548&highlight=restore+grubt)

and follow the instructions by seshomaru samma about half-way down. I had a similar problem with GRUB being knocked out by a win install and this worked perfectly for me.

---

### Post by jcroot on 2007-01-03
Thanks for the reply, but now I'm a little bit confuse about something...

Well, yesterday I decided to put my Ubuntu Linux Hard Drive (secondary master) as the primary master so I can reinstall Ubuntu Linux again, so I did it... I reinstall Ubuntu Linux again in this hard drive,  I just unplug the windows hard drive from the power until I fix it.

Now I have my Ubuntu Linux working very nice as a primary hard drive (the windows hard drive is not connect to the power) but I would like to solve the problem with my Windows System, do you think if I put my Ubuntu Hard drive back as a secondary hard drive and plug the power back of my windows hard drive this will not affect my ubuntu instalation or grub? because I don't really want to reinstall ubuntu linux.

One more thing, if I enter into the recovery console using the windows xp CD I get this:

C:\> prompt

Instead of D I get the letter D.

Loading the system recovery tool from the windows CD will not affect my GRUB? If the steps you gave me doesn't work can go back put my Linux Hard drive as a primary master?

Thanks a lot for your help me. I really appreciate it.

---

### Post by skwishybug on 2007-01-03
> Loading the system recovery tool from the windows CD will not affect my GRUB? If the steps you gave me doesn't work can go back put my Linux Hard drive as a primary master?

If you leave your linux drive as the primary drive, you will need to provide space for the windows boot information on it (similarly as you have to leave space on the primary drive for linux if it isn't the primary).  Any windows install will wipe out GRUB, but it can be recovered using the steps I pointed to earlier (at least for me).

If you use the recovery tool, you'll be fine so long as you do not use fixboot or fixmbr as these will rewrite the boot records and eliminate GRUB.

In the recovery tool, if you are not pointing at your CD-ROM drive when you start, you will need to switch to that drive.

To switch drives type in *<drive letter>:*  (i.e. *D:* to get to the 'D' drive)

To find out if you are in the right drive, do a quick *dir* and look for a file that says setup.exe (don't run it tho, just find it). Also see that a directory i386 is present. If those two things are there, you are pointing to your install CD.

Final note:
While it is annoying, doing a fresh install (not a repaired install) will not wipe out all your information. You will have to go through the hassle of reinstalling your software (so the new install of Windows can register it properly and use it) but your data and settings are not lost.

Your best bet in this case is to set up the new install with a different user name. Then find your favourites, e-mails, documents, and everything else saved under /Documents and Settings/[your old profile]/ and simply copy them over to the same folders on the new profile.

If you used Outlook (and possibly Outlook express, I haven't used it in several years) your .pst file (the one that holds all the information, mail, etc) can be tricky to find. If you need help restoring an Outlook file, I can provide the steps (as I have had to do it too many times, part of the drive to Ubuntu).

---

### Post by jcroot on 2007-01-03
Thanks man, I'm very happy that I get some help here, I coudn't fix my computer yet but I'm happy that I least somebody answer me...

Note: If I start the recovery tool (windows xp) I see the C letter promts instead of D.

I found something interesting here... I entered to my PC Bios and I have the following:

Title: Phoenix Award Bios
CMOS Setup Utility

Then it gives me to many options and I choosed the first one which is: Standard CMOS Features

and I see the following settings:

IDE Primary Master [IDE-CD R R/RW 48xC]

IDE Primary Slave [None]

IDE Secondary Master [ST34001A] (whis is my hard drive).

IDE Secondary Master Slave [None]

I setup my linux hard drive to be the master primary (I changed the pin or the little thing to make it master) and in the bios is setup as secondary master this is right? I think my linux hard drive is suppose to be at the IDE Primary Master right? I would like some help with this please.

---

### Post by skwishybug on 2007-01-03
> IDE Primary Master [IDE-CD R R/RW 48xC]

IDE Primary Slave [None]

IDE Secondary Master [ST34001A] (whis is my hard drive).

IDE Secondary Master Slave [None]

This tells me a couple of things.

1. You would get C:\> at the recovery console as your CD-ROM is technically set up as your primary drive (this can cause some problems).

2. If you changed your jumper setting from slave to master on your hard-drive, it might explain some of the other problems too.

I would first suggest getting your devices in the "proper" order (proper as in what Windows likes to see).

1. On one cable you have to have one device set as the "Master". If you attach a second device, it will have to be set to "Slave".

2. For your Primary Master it is preferred to have a hard-drive connected that contains your operating system(s).

3. If you have two seperate hard drives and you may be using both to boot from (by enabling device selection in the BIOS, if supported) then each should be a Master on seperate cables.

Now, with the arrangement at the device end of the cables figured out, its time to move to the motherboard end of the cable.

Each cable will plug into a connector on the motherboard and each will be labelled as either IDE1 or IDE2. IDE1 is the "Primary" and IDE2 is the "Secondary". (Currently it looks like you have your CD-ROM pluged into IDE1 and your HD into IDE2).

After that, run the install CD and open the recovery console.  Type in:
*diskpart*

And if you post the results, we might be able to get this on the way to working for you.


Note: I looked over the KB you posted and looked into it a bit more and I cannot pinpoint a reason for the access denied except that the command in the KB (delete) is not the same command availble in the recovery console (del) although that should have returned an error saying the command is not recognized. The other cause might be a permission on the file but I haven't had a chance to reboot into windows today to test this theory.

---

### Post by jcroot on 2007-01-03
It will be a good idea to have my Linux System (the hard drive) setup as the primary master? I changed the jumper to be setup as "Master ON- Slave Off" and I connect to my computer but I don't see any diferrence, I mean I still see my Linux Hard drive in the bios as the second primary.

So, you are saying that I have my CD Room cable (the big cable) connect as IDE1 (primary master)? How can I set up my Linux Hard drive to be the primary master? removing my cd room cable and connect it somewhere else and connect my hard drive cable to where my cd room was?

I'm getting C at the promt because like you said: My CD Room is setup as the primary master IDE1.

---

### Post by smoker on 2007-01-03
best way is to look at your motherboard, your two ide sockets should be marked ide channel 1 and ide channel 2, or maybe just have a 1 and 2 somewhere near the socket.

track your cable from channel 1 and disconnect it from any devices it is attached to and connect the other end of the cable to your master drive, if your cable has a connecter in the middle of the cable, as is usual, this is the connecter for the slave device on that channel.

the other ide channel and cable works the same way, one end of cable to motherboard, one end to the master device, and the middle is for the slave.

---

### Post by jcroot on 2007-01-03
I finally got my PC setup the right way... I mean the hardware. This is what I did with all your help.

1: I prepared both hard drives (linux and windows) to be a master (I changed the jumper).

2:I Connected my windows hard drive to the channel 1 (IDE1 Primary Master) because this will be the primary master hard drive.

3: I connected Linux Hard drive to the channel 2 (IDE2)

4: I also connected my CD ROM to channel 2 (using the same cable).

5: Now my bios recognizes my Windows Hard drive as the primary master and my linux hard drive as secondary master. My CD ROOM is recognized as IDE secondary slave.

So after all this I tried all the instructions that you gave me to see if I can get my windows system working but I didn't  have any luck.

The only command that worked for me is: diskpart

and the output of diskpart is:

38153 MB Disk 0 at Id 0 on Bus on atapi MBR

C: Partition1 [unkown]   38154 <38154> MB Free

Unpartitioned   8 MB

----------

38163 MB Disk 0 at Id 0 on Bus on atapi MBR

I: Partition1 [unkown]               36585 MB <36585> Free 
J: Partition2       1577 MB   <1577> Free


I can't give you the output for all the errors that I have while trying the commands you gave me (such as cd i386, <D>, dir system.* etc) because after the last command (diskpart) I'm not able to use the recovery tool any more, I mean everytime I start the recovery tool I see this message:

1 C:\windows

Which windows installation would you like to log onto? Press enter to cancel.


Can I be able to use my Windows hard drive as slave just to get all my files and save it? or I can't? because my windows hard drive is setup to be a primary master so I don't think this will work for me.

What else can I do?

One more thing, I guess the windows recovery tool wiped my GRUB too, I would to try to restore my GRUB after I finished with windows.

Thanks for your help...

---

### Post by jcroot on 2007-01-03
Good news guys, some how I got into the reinstall windows xp procedure (not a fresh copy but a repair copy).

This is how I did it: When I have the command promt (recovery tool) I typed: help and I see a list of all commands that I can use so I choosed one command that was familiar with me which is: chchks (something like that, I don't remember the command) so this command found some errors in my hard disk and tried to fix it, now when I restart my pc windows will boot but I'm not able to log in into windows because i don't see the login screen coming up.

Well I decided to try the repair thing with windows xp cd, I boot from the cd and follow the procesure like I was doing a fresh copy but now I see the option: If your windows instalation is damage you can repair by pressing R.

So I hit R and it copy some files to my hard disk and I got stop in the windows xp instalation because it says:

Cannot copy: Fetnd5.sys please make sure your Windows XP Professional Service Pack 2 is in the right place.

My Windows CD is alright, I even tried with other CD and I keep getting the message, I know don't what this file is: Fetnd5.sys or if I can download it form the internet, I searched google.com for this file but I coudn't find it. 

I don't know if I can just turn my pc off until I find this file and copy into a cd (if I'm able to do that) or I don't know what to do... Can I be able to copy this into a CD and start windows instalation again and put the cd with the file on it? What is this file and where can I found it?

---

### Post by jcroot on 2007-01-04
Any idea? Please? :-?

---

### Post by skwishybug on 2007-01-04
What comes up when windows starts if there is no log in screen or desktop?
 
I've looked into the file you mentioned, I have not been able to find information on it yet.

---

