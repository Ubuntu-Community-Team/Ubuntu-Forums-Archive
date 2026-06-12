---
title: "help 4 the 5th time"
date: 2007-06-05
forum: General Help
---

### Post by ReaLitaliano on 2007-06-05
i installed ubuntu and something happened and now i cant boot to windows or linux and i just want my windows files back and i dont care about my Linux right now.No one was able to help me let.i tried fixmbr and it dont work.i get a message that says strike F1 to retry boot, F2 for setup utility How can i recover my files back they r very important

---

### Post by confused57 on 2007-06-05
I saw in one of your other threads that you had a copy of Super Grub Disk.
Boot your pc with the SGD inserted, after SGD has booted, select:
1.)English Super Grub Disk
2.)Windows
3.)Fix Boot of Windows

I saw you have a Dell Dimension 2400, so I assume you have to press "F12" at the Dell logo screen during bootup to select  boot from cd.

---

### Post by ReaLitaliano on 2007-06-05
yea i will try it soon

---

### Post by strabes on 2007-06-06
Check the link in my signature.

---

### Post by ReaLitaliano on 2007-06-06
i tried to fix it using Super Grub Disk but i get error 29 disk write error

---

### Post by H.E. Pennypacker on 2007-06-06
Since most of us can't be expected to check out your older posts, I am going to have to ask you that you please be very detailed.  Start your story from the very beginning.  Tell us what you were doing on your computer, what happened, and where you are now.  Please do not skip anything.  Be VERY detailed.

Also, provide hardware information.  

No one can help without all this.

---

### Post by ReaLitaliano on 2007-06-06
i just tried to fix it with Using the Desktop/LiveCD while preserving Windows Bootloader the first one when i typed su in the terminal it will not let me type the password.

---

### Post by H.E. Pennypacker on 2007-06-06
> i just tried to fix it with Using the Desktop/LiveCD while preserving Windows Bootloader the first one when i typed su in the terminal it will not let me type the password.

Again, you're not following what I have asked.  Please see my earlier post asking for more information.

Ubuntu does not use "su."  Ubuntu uses sudo.  Other distros use su, we don't.  Whenever you need administrative priviliges, type sudo, and whatever command you need.

Please, this time, provide thorough information.

---

### Post by ReaLitaliano on 2007-06-06
well i installed ubuntu with wubi it was a bit slow when i booted up but work 4 two days.i then wanted to use my xp so i restarted ubuntu then i get a black screen saying strike F1 to retry boot, F2 for setup utility.
i am using a dell dimension 2400,2.4ghz,80gig hard drive,1 gig or ram

---

### Post by H.E. Pennypacker on 2007-06-06
> **ReaLitaliano said:**
> well i installed ubuntu with wubi it was a bit slow when i booted up but work 4 two days.i then wanted to use my xp so i restarted ubuntu then i get a black screen saying strike F1 to retry boot, F2 for setup utility.
i am using a dell dimension 2400,2.4ghz,80gig hard drive,1 gig or ram

Thank you for posting this.  At this time, we're still not very clear on everything.  In another post, you explain that you no longer get this error message, and that you now have a different problem:

> ok i dont get the message 2 hit F2 anymore. now it says error on trying to load operating system.


Can you please be more clear?  Exactly what is going on at this time?  Are you still getting the F1/F2 error anymore, or is it gone?  Are you now getting a different error?  If you are getting a different error, you will not to reproduce that EXACT error.

Please do not cut corners when asking for help.  I have repeatedly asked for clarifications and more information, but you are hesitant.  It is in your own best interest to provide answers to questions.

Three line answers are not enough.

---

### Post by ReaLitaliano on 2007-06-06
yes i am getting the same error

---

### Post by ReaLitaliano on 2007-06-06
looks like no one is able to help.i told people how it happen, i told u the error messages that i am getting but nothing. what more could u want? stop leaving me in the dust and help me out i am not asking 4 much.i should of never install this crap in the first place because there is no help when its needed.i been posting  about the same problem from the start and i am at the same place as i started. i don't want to format my hard drive because i have some important files that i must keep.well i will be here posting more crap about the same thing forever and ever until u people get tired of reading this and maybe just maybe u will finish what u started and not just leave me in the dust.

---

### Post by confused57 on 2007-06-06
> **ReaLitaliano said:**
> looks like no one is able to help.i told people how it happen, i told u the error messages that i am getting but nothing. what more could u want? stop leaving me in the dust and help me out i am not asking 4 much.i should of never install this crap in the first place because there is no help when its needed.i been posting  about the same problem from the start and i am at the same place as i started. i don't want to format my hard drive because i have some important files that i must keep.well i will be here posting more crap about the same thing forever and ever until u people get tired of reading this and maybe just maybe u will finish what u started and not just leave me in the dust.
You need to help us to help you find a solution, as H.E. Pennypacker has mentioned....

You might want to boot up the Ubuntu live cd, open a terminal(Applications---Accessories---Terminal), enter & post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

If you're having problems booting the live cd, post back what they are...if for some reason you don't have a copy of the live cd, you might want to download & burn one...you say you have a copy of the SGD, it's the same method for burning an iso as you used to burn the SGD.  With the live cd and a USB pen drive or external drive, you can recover your Window's data.  Did your dual boot work at one time?  If so, do you remember possibly what you may have downloaded & installed or anything you reconfigured before your boot problems started.

From what I've read in your other threads, people have made suggestions or asked you to post the output of commands in the terminal...your replies were usually a line or 2 saying it didn't work, or you didn't post the requested commands.  People helping in the forums are volunteering their time & experience, unless the checks in the mail, to assist other users to find solutions to their problems.  The patience of some trying to assist other users with their problems  is verging on saintly. 

A good start would be to post the output of the "sudo fdisk -l" command...then we can go from there.

---

### Post by ReaLitaliano on 2007-06-06
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System

---

### Post by ReaLitaliano on 2007-06-06
ubuntu has worked for 2 days and i used wubi to install it on the same drive as windows

---

### Post by ReaLitaliano on 2007-06-06
H.E. Pennypacker has not given me the command.u think i know linux commands?

---

### Post by confused57 on 2007-06-06
Being a beginner, I realize you don't know terminal commands...boot the live cd & post the output of:
```
blkid
```
and
```
lspci
```
copy & paste these commands into your terminal in the live cd...please post(copy & paste) the output you receive.

OK, since you have a copy of the live cd, you might want to try reinstalling Ubuntu with it.  Boot the live cd, start the installation & see what gparted shows for your partitions on your hard drive.  Just don't select to format any of your partitions or continue the partitioning part of the install.

---

### Post by ReaLitaliano on 2007-06-06
when i typed blkid nothing happened but this is what happened when lspci


00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:04.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
01:05.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

---

### Post by ReaLitaliano on 2007-06-06
i try to reinstall it but i get this message You need to specify a partition for the root file system (mount point "/") with a minimum size of 2 GB, and a swap partition of at least 256 MB. You may also set up other partitions if you wish.

---

### Post by confused57 on 2007-06-06
OK, that's kind of what I expected...try the other suggestion to see what the live cd's gparted shows for the partition(s) on your hard drive.

Added:  I see you've already started the install...did gparted show your Window's partition?

Here's an excellent website for installing with the live cd:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Here's some excellent screenshots of what you should see in gparted:
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

The gparted live cd is an excellent partitioning tool, similar to Partition Magic, and it's free(45 Mb download):
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by ReaLitaliano on 2007-06-06
gparted says unallocated 74.50 gib

---

### Post by confused57 on 2007-06-06
You might want to wait for a second opinion, but looks like your Window's installation has been deleted?

I found this on Microsoft's website, if you have a Window's install cd, you can boot it & enter recovery console:
[http://support.microsoft.com/kb/307654](http://support.microsoft.com/kb/307654)

Maybe a chdsk will reveal something...if you know someone that has more than a casual knowledge of Windows and computers, you might want to have them take a look.

As I mentioned, you might want to wait for someone else in the forum to verify this or they may be able to shed some light on what might be the cause of your "invisible" Windows...Good Luck with it.

---

### Post by ReaLitaliano on 2007-06-06
thanks

---

### Post by H.E. Pennypacker on 2007-06-07
> stop leaving me in the dust and help me out i am not asking 4 much

I have been more than willing to help, as you will see in other threads where I have provided others help.  Unlike others, you actually don't provide all the answers I need beforehand.  This makes me very frustrated, and makes me want to move on to someone else's problems.

At this time, please install GParted while you're logged into Ubuntu (through Synaptic), and paste a screenshot of GParted's main window.  I need to know which partitions exist on your computer, and what may have been lost.  

Your screenshot should look something like this:

[http://knowledge76.com/images/Gparted.png](http://knowledge76.com/images/Gparted.png)

Take the screenshot by pressing on "Prnt Screen."  

Notice how my posts are much longer than yours, eventhough you're the one who should be providing me with information.

---

### Post by ReaLitaliano on 2007-06-07
gparted says unallocated 74.50 gib

---

### Post by ReaLitaliano on 2007-06-07
sorry i cant upload screen shot

---

