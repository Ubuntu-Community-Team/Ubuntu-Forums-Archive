---
title: "Ubuntu 7.10 Installation hangs at certain %"
date: 2007-10-21
forum: General Help
---

### Post by jaezcurra on 2007-10-21
7.10 installation using wubi stops at 45% copying files.
I downloaded the iso 386 file and last wubi.exe (347).  I put both of them in a freshly created directory named wubi, that I defragged.  I ran the exe, which found the iso and the installation began.  Everything seemed to go smooth and I could notice that the installation was going on until a stall in 45% copying files.
What am I supposed to do?

---

### Post by jaezcurra on 2007-10-21
Trying again the installation with wubi installer (rev 347), nothing happens when I doubleclick the exex file :confused:
I have been trying with the iso file in a wubi directory as well as with th iso CD.

---

### Post by nemo82 on 2007-10-21
Apparently I got the same problem: installation stopped at 53% with the latest alpha. Really need some hint about it! Thanks a lot for your great work guys!

---

### Post by ago on 2007-10-22
Can you send here /var/log/syslog?

---

### Post by franman on 2007-10-22
Same here - 45%. Unfortunately, I uninstalled wubi an deleted all virtual partitions including all logs :(

---

### Post by jaezcurra on 2007-10-22
> **ago said:**
> Can you send here /var/log/syslog?

The main problem, now, is that I am trying to run wubi installer (rev 358) and nothing happens: no way to even starting the installation :confused:

---

### Post by ago on 2007-10-22
> **jaezcurra said:**
> The main problem, now, is that I am trying to run wubi installer (rev 358) and nothing happens: no way to even starting the installation :confused:

Hmm do you have an error of some sort? Does it crash? Do you see a log in %TEMP%\wubi*.log?

---

### Post by jaezcurra on 2007-10-22
> **ago said:**
> Hmm do you have an error of some sort? Does it crash? Do you see a log in %TEMP%\wubi*.log?

I get this:

============ New Session ============
arch=i386
DetectCD
cddrive=
============ New Session ============
arch=i386
DetectCD
cddrive=
============ New Session ============
arch=i386
DetectCD
cddrive=
============ New Session ============
arch=i386
DetectCD
cddrive=
============ New Session ============
arch=i386
DetectCD
cddrive=
============ New Session ============
arch=i386
DetectCD
cddrive=

I am lucky that XP does not suffer at all; it just does not respond to my run of the wubi installer.

---

### Post by ago on 2007-10-22
It looks to me like it crashes. Is that correct? Windows should offer some more info on the crash itself when that happens.
On my side I'll add more logging so we can pinpoint the issue.

---

### Post by jaezcurra on 2007-10-22
What do you mean by "it crashes"?  I am asking that as I cannot notice anything on the side of the XP: I double click the exe wubi installer and nothing happens.  That's all and I remain stupefied (:confused:).

---

### Post by ago on 2007-10-22
[http://support.microsoft.com/kb/310414/EN-US/](http://support.microsoft.com/kb/310414/EN-US/)

see also docs on drwatson

---

### Post by garferi on 2007-10-22
Yesterday I tried to install Wubi-rev347 to my friend's machine, but it always stocked at about 30%
Today I tried Wubi-rev358 on mine, but the  installation is stocked at  24%
The logfile is attached.

---

### Post by ago on 2007-10-22
There are 2 relevant logs. 

If the error you refer to happens in windows, post here %TEMP%\wubi*.log

If the error you refer to happens in linux (i.e. after reboot), post here /var/log/syslog (press CTRL+ALT+F2 to get a shell)

---

### Post by barbulo on 2007-10-22
Forcing the 32 bit edition, installation hangs at about 30% after reboot. How can i acces the /var/log/syslog? System is completely freezed, no muose or keyboard support...

---

### Post by jaezcurra on 2007-10-22
> **ago said:**
> [http://support.microsoft.com/kb/310414/EN-US/](http://support.microsoft.com/kb/310414/EN-US/)

see also docs on drwatson

Well, my Error Reporting is enabled and I cannot see anything in the Event Viewer either.  The XP machine behaves 100% OK, as always (as far fas a Windows PC is concerned :)).

Regedit does not show any entry suggesting some kind of disturbing wubi element.

I am really confused, as it is clear that something is preventing wubi to even start.

BTW, 7.04 was installed with wubi without troubles in this same PC,and I have done it many times in many computers with no glitches at all.

---

### Post by ago on 2007-10-22
> **barbulo said:**
> Forcing the 32 bit edition, installation hangs at about 30% after reboot. How can i acces the /var/log/syslog? System is completely freezed, no muose or keyboard support...

What you do, is the following:

1 do a fresh installation
2 before rebooting, edit ubuntu/intsall/grub/boot/menu.lst and comment out "automatic-ubiquity"
3 when you reboot you are shown the LiveCD desktop
4 Open a terminal and type: tail -f /var/log/syslog
5 Open another terminal and type: top
6 Open another terminal and type: ubiquity --automatic (this starts the actual installer).

Keep the other 2 terminals (#4 and #5) visible
Now when it hangs you should be able to see what Ubiquity it was doing. See if it runs out of memory (free memory=free memory+buffers+cached).
When it starts copying stuff, open another terminal and type: cat /proc/mounts (relevant entries have to do with /target, /host, /isodevice and loop based mount)

---

### Post by franman on 2007-10-22
Only warning in /var/log/syslog says "apt API not stable yet". Does this mean anything to you?

Franman

---

### Post by ago on 2007-10-22
Hmm no don't think that is relevant... You need to tell me what process is blocking, doing what exactly...

---

### Post by barbulo on 2007-10-22
> **ago said:**
> What you do, is the following:

1 do a fresh installation
2 before rebooting, edit ubuntu/intsall/grub/boot/menu.lst and comment out "automatic-ubiquity"
3 when you reboot you are shown the LiveCD desktop
4 Open a terminal and type: tail -f /var/log/syslog
5 Open another terminal and type: top
6 Open another terminal and type: ubiquity --automatic (this starts the actual installer).

Keep the other 2 terminals (#4 and #5) visible
Now when it hangs you should be able to see what Ubiquity it was doing. See if it runs out of memory (free memory=free memory+buffers+cached).
When it starts copying stuff, open another terminal and type: cat /proc/mounts (relevant entries have to do with /target, /host, /isodevice and loop based mount)

This is what i get:

MEM: 2075496kb  2021856kb used  53640kb free  566976kb buffers  1177592kb cached

from syslog:
/dev/loop2 /traget ext3 rw,data=ordered 00
/dev/loop3 /traget/home ext3 rw,data=ordered 00
/dev/sda6 /target/boot fuseblk rw,nosuid,nodev,noatime,user_id=0,group_id=0,allow_other=0

In cat the only warnings is apt api not stable yet.

Hope theese infos could be usefull...

---

### Post by ago on 2007-10-22
> **jaezcurra said:**
> Well, my Error Reporting is enabled and I cannot see anything in the Event Viewer either.  The XP machine behaves 100% OK, as always (as far fas a Windows PC is concerned :)).
New build has a bit more logging info.
Can you try again with rev361+ and post the logs?

---

### Post by jaezcurra on 2007-10-23
This is what I get when I unsuccessfully run wubi installer (rev 363):
============ Installer ============
PLUGINSDIR=C:\DOCUME~1\JOSEAN~2\CONFIG~1\Temp\nss17E.tmp
detect_all
Parsing cmdline "C:\Wubi\Wubi-7.10-alpha-rev363.exe" 
DetectProcessorArchitecture
arch=i386
DetectCD
isvalidcd D:\
isvalidcd E:\
isvalidcd C:\
isvalidcd F:\
DetectCD Finished cddrive=
CheckIfinstalled
DetectInstallationDrive
isInstallationDrive C:\ubuntu
CheckFreeSpace c:
DetectBackupFolder
DetectGMT
DetectCountry
DetectLocale
DetectLayoutCode
DetectTimeZone
DetectDomain
DetectHostName
DetectComputerName
DetectUserName
DetectUserDomain
DetectUserInfoName
DetectUserProfileFolder
DetectUserProfileName
ShowMainPage

I really don't understand why I could began a 7.10 wubi installation two days ago and now the installer simply refuses to move ahead just one millimeter.

---

### Post by jaezcurra on 2007-10-23
Ah! I have just found an "Ubuntu" and an "Ubuntu-save" directories both in my C drive.  I have swapped them off off and the launcher seems to work.  I am going to start the installation of 7.10 and report later here.

---

### Post by alagu on 2007-10-23
> **ago said:**
> What you do, is the following:

1 do a fresh installation
2 before rebooting, edit ubuntu/intsall/grub/boot/menu.lst and comment out "automatic-ubiquity"
3 when you reboot you are shown the LiveCD desktop
4 Open a terminal and type: tail -f /var/log/syslog
5 Open another terminal and type: top
6 Open another terminal and type: ubiquity --automatic (this starts the actual installer).

Keep the other 2 terminals (#4 and #5) visible
Now when it hangs you should be able to see what Ubiquity it was doing. See if it runs out of memory (free memory=free memory+buffers+cached).
When it starts copying stuff, open another terminal and type: cat /proc/mounts (relevant entries have to do with /target, /host, /isodevice and loop based mount)

Hi,
The problem that raises on doing above is,

Invalid file system for this mount point

The file system type ntfs cannot be mounted on / because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2.


I removed the ubiquity-automatic from the menu.lst and typed ubiquity --automatic in the terminal.

Thanks
Allagappan

---

### Post by ago on 2007-10-23
> **alagu said:**
> Hi,
The problem that raises on doing above is,

Invalid file system for this mount point

The file system type ntfs cannot be mounted on / because it is not a fully-functional Unix file system. Please choose a different file system, such as ext2.

That's because ntfs is marked as dirty. You need to run chkdsk /r from windows and then run wubi again.

---

### Post by ago on 2007-10-23
> **jaezcurra said:**
> Ah! I have just found an "Ubuntu" and an "Ubuntu-save" directories both in my C drive.  I have swapped them off off and the launcher seems to work.  I am going to start the installation of 7.10 and report later here.
Hmm not sure what is happening here. What you mean by "you swapped them off"? Did you figure out the reason of your hang?

---

### Post by alagu on 2007-10-23
> **ago said:**
> That's because ntfs is marked as dirty. You need to run chkdsk /r from windows and then run wubi again.

Woah! that is instant-reply :) Checking Windows now.

Thanks
Alagu

---

### Post by jaezcurra on 2007-10-23
> **ago said:**
> Hmm not sure what is happening here. What you mean by "you swapped them off"? Did you figure out the reason of your hang?

I really don't know.  the facts are:
* where there used to be "wubi" directories, there are now "ubuntu" directories.
* now wubi uninstaller works 100%, without the need to run regedit.
* now it hangs at 30% copying files installation phase, but all the ubuntu structure was created into the XP disk.

So we are again facing the first problem: the installation hangs at xx% of the copying files phase :confused:

---

### Post by ago on 2007-10-23
> **jaezcurra said:**
> I really don't know.  the facts are:
* where there used to be "wubi" directories, there are now "ubuntu" directories.
* now wubi uninstaller works 100%, without the need to run regedit.
That is as planned

> * now it hangs at 30% copying files installation phase, but all the ubuntu structure was created into the XP disk.

So we are again facing the first problem: the installation hangs at xx% of the copying files phase :confused:

I need to know what process is running on the Linux side when that happens and possibly what process is hanging.

---

### Post by ago on 2007-10-23
Also, is this a complete system hang, or can you use keyboard/terminal? 
What is the available memory (including cache and buffers)?

---

### Post by jaezcurra on 2007-10-23
> **ago said:**
> I need to know what process is running on the Linux side when that happens and possibly what process is hanging.

How do I know?

---

### Post by jaezcurra on 2007-10-23
> **ago said:**
> Also, is this a complete system hang, or can you use keyboard/terminal? 
What is the available memory (including cache and buffers)?

i could exit by hitting Ctrl+F2 and then "sudo reboot". I don't know how to retrieve this piece of information.

---

### Post by ago on 2007-10-23
> **jaezcurra said:**
> How do I know?

By running commands such as ps -ax/top/free in a terminal (assuming there is no total system hang) and looking at the logs in /var/log

---

### Post by ago on 2007-10-23
> **jaezcurra said:**
> i could exit by hitting Ctrl+F2 and then "sudo reboot". I don't know how to retrieve this piece of information.

Then it's not a system hang.

---

### Post by alagu on 2007-10-23
> **ago said:**
> Also, is this a complete system hang, or can you use keyboard/terminal? 
What is the available memory (including cache and buffers)?

It is a complete system hang,few minutes after it reaches the XX%

---

### Post by ago on 2007-10-23
Keep up terminals with the following command while you run ubiquity (simply press ctrl+alt+f2)

sudo tail -f /var/log/dmesg

Look if there is any unionfs error message when it hangs

---

### Post by alagu on 2007-10-23
> **ago said:**
> That's because ntfs is marked as dirty. You need to run chkdsk /r from windows and then run wubi again.

It turns out that i have to give a chkdsk /r from windows everytime an installation is aborted.

1.I cleanup everything.
2.Run wubi-installer
3.Restart and goes to linux
4.Hangs at 34%.
5.Force reboot
6.Remove the ubiquity grub parameter and continue with Live CD
7.Run ubiquity --automatic
8.Raises the above mentioned error.
9.Go to windows, and run chkdsk again.

These were my earlier steps.

I'm now running chkdsk, I'll try to go to LiveCD directly withouth running the installer.

Thanks
Allagappan

---

### Post by jaezcurra on 2007-10-23
> **alagu said:**
> It is a complete system hang,few minutes after it reaches the XX%

Yes, now it has been a complete hang at 33%.  The mouse could work, but I tried Ctrl+Alt+F2 and nothing; and then no commands worked.
I had to hard reset the machine.

---

### Post by ago on 2007-10-23
As mentioned, one way to address that is to start a console and use 

tail -f /var/log/dmesg

Then sign down any error you may see once the system hangs. 

Unionfs is a prime suspect.

---

### Post by jaezcurra on 2007-10-23
I am attachin 2 jpg files taken with my phone (pls forgive for the poor quality)

---

### Post by alagu on 2007-10-23
I did as you said,

/var/log/dmesg in one terminal, /var/log/syslog in the other, and top in another.

This is what resulted:


1.The installation dialog is hung (it stopped at 27%), and X is also hung (Keyboard and mouse work though)
2./var/log/dmesg : cs : IO Port probe 0xa00-0xaff: clean (this was there even before installation started)
3./var/log/syslog : Futurewarning: apt API not stable yet (this is same as someone else told in this thread)
4.top: ubiquity process is not consuming the memory. Xorg and init are top in the list.
5.Ctrl+Alt+F1,F2,etc all are enabled, i am able to type in it, but on pressing enter, nothing works. it is hung.

Please let me know what could be done. I love ubuntu and wubi. It is really disappointing to see wubi crash so bad.

Thanks
Alagu

---

### Post by ago on 2007-10-23
> **jaezcurra said:**
> I am attachin 2 jpg files taken with my phone (pls forgive for the poor quality)

That means you have to clean up ntfs by running chkdsk /r from windows and then booting into Ubuntu

---

### Post by ago on 2007-10-23
> **alagu said:**
> I did as you said,

/var/log/dmesg in one terminal, /var/log/syslog in the other, and top in another.

This is what resulted:


1.The installation dialog is hung (it stopped at 27%), and X is also hung (Keyboard and mouse work though)
2./var/log/dmesg : cs : IO Port probe 0xa00-0xaff: clean (this was there even before installation started)
3./var/log/syslog : Futurewarning: apt API not stable yet (this is same as someone else told in this thread)
4.top: ubiquity process is not consuming the memory. Xorg and init are top in the list.
5.Ctrl+Alt+F1,F2,etc all are enabled, i am able to type in it, but on pressing enter, nothing works. it is hung.

Please let me know what could be done. I love ubuntu and wubi. It is really disappointing to see wubi crash so bad.

Thanks
Alagu


Hmm not much there for me to get a good guess...

---

### Post by ago on 2007-10-23
Just checking, are you guys using the FINAL desktop ISO correct?

---

### Post by jaezcurra on 2007-10-23
> **ago said:**
> That means you have to clean up ntfs by running chkdsk /r from windows and then booting into Ubuntu

I have done it at least once.  Last time I did it it really took looooong and it found nothing wrong nor repaired any errors in my ntfs.  Now, I have left th pc making a defrag.  I will see tomorrow again.

---

### Post by jaezcurra on 2007-10-23
> **ago said:**
> Just checking, are you guys using the FINAL desktop ISO correct?

My iso file was downloaded last Sunday, Oct 21.

---

### Post by alagu on 2007-10-23
> **ago said:**
> Just checking, are you guys using the FINAL desktop ISO correct?

I am using the version 7.10 downloaded after the public release, from ubuntu website.

Thanks
Alagu

---

### Post by franman on 2007-10-23
I'm using the actual (desktop) iso, too. 
Here's a screenshot of wubi installation stopping right at the beginning. 
Just started chkdsk /r. I will try to take another screenshot when it stops around 45%.

---

### Post by franman on 2007-10-23
> **franman said:**
> Just started chkdsk /r. I will try to take another screenshot when it stops around 45%.

Sorry, didn't work. Now, ubiquity crashes after I selected my correct timezone in the worldmap.

---

### Post by MrTq on 2007-10-23
> **ago said:**
> What you do, is the following:

1 do a fresh installation
2 before rebooting, edit ubuntu/intsall/grub/boot/menu.lst and comment out "automatic-ubiquity"
3 when you reboot you are shown the LiveCD desktop
4 Open a terminal and type: tail -f /var/log/syslog
5 Open another terminal and type: top
6 Open another terminal and type: ubiquity --automatic (this starts the actual installer).

Keep the other 2 terminals (#4 and #5) visible
Now when it hangs you should be able to see what Ubiquity it was doing. See if it runs out of memory (free memory=free memory+buffers+cached).
When it starts copying stuff, open another terminal and type: cat /proc/mounts (relevant entries have to do with /target, /host, /isodevice and loop based mount)
This is what i get:
MEM: 1034812k total	1020560k used	14252k free	 271668k buffer
Swap: 488272k total	44616k used	                    443656k free	 571236k cached

And from syslog:
ubuntu ubiquity[8604]: debconffilter done:partmancomit (current:none)
ubuntu ubiquity[8604]:/usr/lib/python 2.5/site-package/apt/ --init--py:18: Future warning: apt APT not stable yet
warnings.warn("apt APT not stable yet", Future warning.:(
I used Wubi-7.10-alpha-rev364.exe.

---

### Post by alagu on 2007-10-24
As I can see, there isn't much information to make out from all these error logs, it seems mysterious why it stops loading at 34%.

Btw, for all those who got invalid ext2 error, it is because of the incomplete installation previous time. You have to delete your previous installation, give a chkdsk /r and go along with installation again.

Ago, did you check this yourself, are you encountering these problems?

-Alagu

---

### Post by jaezcurra on 2007-10-24
After a 1,5 hour of chkdsk /r, I tried again wubi installer (rev 364) and now the freeze was at 31%.
I think that  I am giving up until wubi 7.10 works as it used to do with 7.04: greatly!!!
I will be checking this forum from time to time to check wubi's progress.
Good luck, Ago :)

---

### Post by ago on 2007-10-24
> **alagu said:**
> As I can see, there isn't much information to make out from all these error logs, it seems mysterious why it stops loading at 34%.

Btw, for all those who got invalid ext2 error, it is because of the incomplete installation previous time. You have to delete your previous installation, give a chkdsk /r and go along with installation again.

Ago, did you check this yourself, are you encountering these problems?

-Alagu

I haven't been able to reproduce that. Another thing to try is to uninstall, run chkdsk /r and reinstall on a 4GB virtual drive. It might be that the virtual images are not zeroed though. I will add zeroing code tonight.

---

### Post by MrTq on 2007-10-24
> **jaezcurra said:**
> After a 1,5 hour of chkdsk /r, I tried again wubi installer (rev 364) and now the freeze was at 31%.
I think that  I am giving up until wubi 7.10 works as it used to do with 7.04: greatly!!!
I will be checking this forum from time to time to check wubi's progress.
Good luck, Ago :)

The same to me. 31% :(:confused::(

---

### Post by molk on 2007-10-24
I was getting a freeze at 31% also. I am installing on a Dell D820 laptop. What's interesting is that the WI/FI light flashes and continues to flash intermittently when the WUBI installation completely freezes. This laptop has a way to turn off the builtin wireless with a switch on the side of the laptop. I need to try to turn off wireless that way and re-run the installation again to see if this changes anything.

---

### Post by jaezcurra on 2007-10-24
> **ago said:**
> I haven't been able to reproduce that. Another thing to try is to uninstall, run chkdsk /r and reinstall on a 4GB virtual drive. It might be that the virtual images are not zeroed though. I will add zeroing code tonight.

OK. I will give wubi a last chance tomorrow morning with a 4GB size. Just, please, make the necessary tweaks tonight ;)

---

### Post by cdinz on 2007-10-24
umm....happens to me at too... I had it happen at 33%.... 26%..... 45%

Will try to install again and post the logs here....

---

### Post by cdinz on 2007-10-24
> **cdinz said:**
> umm....happens to me at too... I had it happen at 33%.... 26%..... 45%

Will try to install again and post the logs here....

Ok ran the installer again.... And it got stuck at 23%

Here r the pics that I took:

---

### Post by ago on 2007-10-24
Are you all on FAT?

---

### Post by cdinz on 2007-10-24
> **ago said:**
> Are you all on FAT?

nope....not at all... All my disks are NTFS....

I was wondering too when I saw the FAT error and checked out jus to be sure and all my disks are NTFS indeed

---

### Post by hisea on 2007-10-24
I have similar problem.
I use windows vista with NTFS.

---

### Post by cdinz on 2007-10-24
I tried doing the installation once again but now on a 4GB disk and the installer got stuck at 28%.....

**_My System Info:_**
Intel Pentium D 2.80 GHz (64 bit processor)
1.5 GB of RAM
Samsung **SATA** HDD (160GB)

***The other thing I want to point out is that I have a 64bit system where as the ISO I downloaded is for a 32 bit system... ***

Here r the pics again:

---

### Post by ago on 2007-10-24
Try the 365 build please
Ignore the warning about missing swap and click continue.

---

### Post by molk on 2007-10-24
I am using NTFS as well

---

### Post by cdinz on 2007-10-25
Woo Hoooo.... ***Rev 368 works***....:guitar:

I was able to install Ubuntu successfully and login into it....

The installation went on smoothly except for the swap error....

But /var/log/syslog and /var/log/dmesg gave the same errors as I reported before....

Thanks a lot **ago**.... If u need anymore info lemme know... and how do I create the swap space now :confused:

---

### Post by loddfor on 2007-10-25
Well,I install rev 368,
after reboot and ignore swap error,
I still stacked at 32%.

I am using NTFS as well,and useing ubuntu-7.10-desktop-amd64.iso.
Can I use i386 version instead?

---

### Post by ago on 2007-10-25
You need to run wubi with --32bit argument

---

### Post by molk on 2007-10-25
368 is the first Wubi 7.10 revision which allowed me to install Gutsy Gibbon on my system. With previous revisions Ubiquity would freeze on copying files at 30%. Thank you Ago for all of your hard work!

---

### Post by ago on 2007-10-25
> **cdinz said:**
> and how do I create the swap space now :confused:

I'll try to fix that tonight, but it should not be to difficult to add it manually. 

Create an empty file inside /host/boot/disks with 

dd if=/dev/zero of=/host/ubuntu/disks/swap.disk bs=1M count=500

Then you run: sudo mkswap /host/ubuntu/disks/swap.disk

Then add the swap entry to /etc/fstab

---

### Post by jaezcurra on 2007-10-25
> **loddfor said:**
> Well,I install rev 368,
after reboot and ignore swap error,
I still stacked at 32%.

I tried once again, in a different computer, with rev 368 and the freeze happened with 25%.

BTW, I got the swap file message too.

I wonder how/why wubi 7.10 is working in some machines and freezing in others :confused:

---

### Post by ago on 2007-10-25
mee too...

---

### Post by esox_hu on 2007-10-25
Hi All,

I tried to installed wubi millions of time, following alpha revisions from version 347 to 368, but with no luck at all.

I have Pentium 4 (3.2Ghz HT) Asus P5LD2 motherboard + 2 Gb of RAM, XP SP2 on NTFS. Target HDD is SATA (Samsung 200Gb)

I downloaded "ubuntu-7.10-desktop-i386.iso".

I tried to installed it with -32bit parameter....but stucked again...
I had:
- Copying files 27% - than whole system stopped working ALT+CTRL+F1 as well
- Copying files 28% - than whole system stopped working ALT+CTRL+F1 as well
- Copying files 30% - than whole system stopped working ALT+CTRL+F1 as well

I've run chkdsk /r on the target drive, used different size of virtual disk from 8 to 10 gig...

But from now - after reboot - , i got BusyBox v 1.1.3 console and that's it. What should I do?

I really fan of Ubuntu but now I'm starting to hate it :)

Kind Regards,
Esox

---

### Post by ago on 2007-10-25
Same issue with 4GB? Is the drive compressed or heavily fragmented?

---

### Post by esox_hu on 2007-10-25
Hi ago!

You are pretty fast :)
I havent tried with 4 gigabytes.
At the moment i use live cd because i got @the file system type ntfs....# error again.
I had to kill the tty7 Xorg - which was the installation on - than I got this live cd xorg window where i could start firefox to write my post for you. So that disk is really big. It is about 160gig and i think yes it is heavily fragmented.

Should I try with 4 gig of virtual disk size?

Regards,
Esox

---

### Post by ago on 2007-10-25
I'd try the following

1. Uninstall wubi
2. Run checkdsk /r
3. Restart windows
4. Install latest wubi version selecting 4GB

If you are in trouble try to kill the processes nicely or use Alt+SysRQ+type R E I S U B

---

### Post by esox_hu on 2007-10-25
Thx.
I'll give it a go... I'll be back soon to tell what's all about with 4Gb.
Esox

---

### Post by ago on 2007-10-25
Defragmenting would not hurt either...

---

### Post by ago on 2007-10-25
Can you guys be specific in what did work and what did not? 
Any pattern you can think of (SATA, FAT, fragmentation, 32/64 bits, installation size...)?
Also do you have the same error logs when it worked as well?

---

### Post by esox_hu on 2007-10-25
Stucked again :( (4Gb, NTFS, non compressed, Dynamic type EIDE)

During checking installation...a popup window appears telling me, i forgot the specify swap partition...go back and specify it... clicking on 'back' popup window disappears, but no way to specify swap size.
Shouldn't be partitioned by the installer itself?

My next try with SATA, non compressed Basic disk 4GB virtual drive)

Esox

---

### Post by franman on 2007-10-25
My specs: 
[LIST]
[*]AMD Athlon 64 x2 3800+ 
[*]1GB RAM
[*]160GB Samsung SATA
[*]ntfs
[*]did a fresh defrag
[*]ran chkdsk /r
[*]installed with --32bit
[*]virtual drive size 15GB
[*]language: german
[/LIST]
BTW: haven't tried the latest rev, yet. Will check it out this evening.

---

### Post by esox_hu on 2007-10-25
I got ntfs error again..."The file system type ntfs cannot be mounted on..." I think i need to defragment my disks...:(

Esox

---

### Post by loddfor on 2007-10-25
To Esox ,
You should run "chkdsk /r" before rebooting.

I tried "chkdsk /f"...
It can also solve ntfs error but faster than "chkdsk /r"...

---

### Post by mayo2000 on 2007-10-25
> **esox_hu said:**
> I got ntfs error again..."The file system type ntfs cannot be mounted on..." I think i need to defragment my disks...:(

Esox

Hi same problem here. I think that ntfs-ng (or whatever is used) is causing the problem and yes it looks like  issue of drive fragmentation. Before I defragmented drive wubi stucked at 37% and after on 49%. However Windows defrag doesn't fully defragment drive. I'am not sure if initrams or ubuntu iso, but one of them definitely should be updated to latest version. I don't think that we can fully defragment disk to get largest free space extent more than few gigs.

```
C:\Users\mayo>defrag d: -a
Windows Disk Defragmenter
Copyright (c) 2006 Microsoft Corp.

Analysis report for volume D: DATA

    Volume size                         = 86.79 GB
    Free space                          = 44.45 GB
    Largest free space extent           = 819 MB
    Percent file fragmentation          = 4 %

    Note: On NTFS volumes, file fragments larger than 64MB are not included in t
he fragmentation statistics

    You do not need to defragment this volume.

C:\Users\mayo>
```

Solution may be to use contig file defrag - [http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx](http://www.microsoft.com/technet/sysinternals/utilities/contig.mspx) on loopback drives (actually files). But wubi doesn't allow to use already created ones.
I created new free 5 gig empty partition and will try to install wubi on it. Let you know if I was succesfull.

---

### Post by ago on 2007-10-25
Can you guys try this?

1. remove "automatic-ubiquity" from /ubuntu/install/boot/boot/menu.lst
2. you will end up in a LiveCD session desktop
3. sudo dd if=/dev/zero of=/isodevice/ubuntu/disks/root.disk bs=1MB count=4000
4. sudo ubiquity --automatic
5. let me know if that fixes it or not

#3 takes a while...

---

### Post by mayo2000 on 2007-10-25
> **mayo2000 said:**
> Solution may be to use contig file defrag - [http://www.microsoft.com/technet/sys...es/contig.mspx](http://www.microsoft.com/technet/sys...es/contig.mspx) on loopback drives (actually files). But wubi doesn't allow to use already created ones.
I created new free 5 gig empty partition and will try to install wubi on it. Let you know if I was succesfull.

Actually I was wrong. At least wubi rev368 creates those images so we can use contig on them. I'll test this aproach rather then dd.

Update: contig says that root.disk fragmentation is low/zero. So I went wrong way. Let's try the sudo dd if=/dev/zero of=/isodevice/ubuntu/disks/root.disk bs=1MB count=4000

---

### Post by mayo2000 on 2007-10-25
> **ago said:**
> Can you guys try this?

1. remove "automatic-ubiquity" from /ubuntu/install/boot/boot/menu.lst
2. you will end up in a LiveCD session desktop
3. sudo dd if=/dev/zero of=/isodevice/ubuntu/disks/root.disk bs=1MB count=4000
4. sudo ubiquity --automatic
5. let me know if that fixes it or not

#3 takes a while...

i tried, but without success. It stucked at same % as before

---

### Post by franman on 2007-10-25
Hmmm...rev 368 did it to me :)

Just passed the swapspace error and continued installing without any problems. Lateron I created a swapspace manually as abo described earlier and added following line to my fstab ```
/host/ubuntu/disks/swap.disk none swap sw

```
I'm not a linux geek - is there anything I missed? I can hardly believe that it works now :lolflag:

---

### Post by ago on 2007-10-25
/host/ubuntu/disks/swap.disk none swap sw 0 0

---

### Post by ago on 2007-10-25
> **mayo2000 said:**
> i tried, but without success. It stucked at same % as before

Most helpful and most disappointing at the same time...
Unfortunately I cannot reproduce on my machine, so it's kind of  difficult for me. But it starts to look like a kernel issue...

---

### Post by ago on 2007-10-25
Are all of you using SATA devices by any chance?

---

### Post by jaezcurra on 2007-10-25
All my attempts until today were made with my office Dell computer, with SATA disks.  Today's one, i am not sure, but it could be SATA too.  I can check tomorrow morning.
One thing is sure: not all the attempts have been the same.  Once I even was asked if I wanted to have my "Documents and Settings" imported.

---

### Post by esox_hu on 2007-10-25
Hi again!

I decided to create brand new primary partition for wubi. If the installation fails again i can use this new partition as a normal linux ext3 partition later on.
So i installed wubi onto that drive (size 7GB). Before reboot, i ran chkdsk.
After reboot, everything went fine...till it says swap partition not recognized or sth like that, but i ignored that...installation could continue....till 44%. 
I waited for 20-25 minutes but nothing happened... Could it be some SATA thing???

I've just found rev370. What's new in this revision ago, please?

Regards,
Esox

---

### Post by ago on 2007-10-25
Can you re-download rev370 and try again one more time please?

---

### Post by esox_hu on 2007-10-25
Hi,
yepp... Not a problem.

I thought this time I could shout because of my installation was successful, but unfortunately not. I've changed my partition type from NTFS to FAT32. Installed wubi, chkdsk, reboot.
"you have not select any partition for use as swap space" but i skipped that... and the progress bar just telling me less than one minute left (never seen this before...just when installed ubuntu 6.06 anno) but after 62% installation has stopped. "Sorry, the program "ubiquity" closed unexpectedly".

But now i'll download 370 again...

Esox

---

### Post by esox_hu on 2007-10-25
tailed my syslog:
[http://esox.atw.hu/syslog_v370_old.txt](http://esox.atw.hu/syslog_v370_old.txt)

---

### Post by ago on 2007-10-25
Ah that's much better:

Oct 25 22:42:31 ubuntu ubiquity[11464]: IOError: [Errno 28] **No space left on device**

Was that with newly downloaded rev370? Did you noticed anything different on your side?
Also can you check the files in /host/ubuntu/disks? How big are they?
Can you also check the amount of free disk space with df? Anything at 100%?
In particular how much free space is in /target? And do you see /target in /proc/mounts?

---

### Post by esox_hu on 2007-10-25
Hi ago,

It was happened with old v370, but happened the same with new 370 version.[SIZE="1"]
ubuntu@ubuntu:~$ df -a -h
Filesystem            Size  Used Avail Use% Mounted on
proc                     0     0     0   -  /proc
sysfs                    0     0     0   -  /sys
tmpfs                1014M   16M  999M   2% /lib/modules/2.6.22-14-generic/volatile
tmpfs                1014M   16M  999M   2% /lib/modules/2.6.22-14-generic/volatile
varrun               1014M   92K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   84K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
devpts                   0     0     0   -  /dev/pts
tmpfs                1014M   16K 1014M   1% /tmp
/isodevice            7.1G  3.1G  4.0G  44% /host
/dev/loop2            1.4G  1.4G     0 100% /target
/dev/loop3            462M   11M  428M   3% /target/home
/host/ubuntu/disks/boot
                      7.1G  3.1G  4.0G  44% /target/boot

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw,mode=0755)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
/isodevice on /host type none (rw)
/dev/loop2 on /target type ext3 (rw)
/dev/loop3 on /target/home type ext3 (rw)
/host/ubuntu/disks/boot on /target/boot type none (rw,bind)


[/SIZE]

If i remember, i set virtual disk siye to 6Gb, but when I had a ook on the disks, they were 500, 500, 1500.
I'll login to XP in a minute and continue this post with correct disk sizes...

See you...

---

### Post by esox_hu on 2007-10-25
Here again.
Disk sizes: home,swap 500, root 1500mbytes.

screenshot:  [http://esox.atw.hu/hc_075.jpg](http://esox.atw.hu/hc_075.jpg)

Is that why ubiquity closed, isn't that?

Esox

---

### Post by ago on 2007-10-25
Yes, root of 1500 is far too low!
Can you check the file size on the windows side before rebooting?
And post here the wubi log that you find in %TEMP%
I uploaded rev371 by the way, you may just want to use that

---

### Post by esox_hu on 2007-10-25
of course.
I think I'll be available for 30 more minutes. It's midnight in Hungary...need some sleep now :)
Esox

---

### Post by mayo2000 on 2007-10-26
> **ago said:**
> Are all of you using SATA devices by any chance?

yes, i'am SATA positive. I'll give rev370 try

---

### Post by mayo2000 on 2007-10-26
> **ago said:**
> Can you re-download rev370 and try again one more time please?

Hi no progress with rev377. When I check syslog dmp there some errors. Could Vista be the reason of freezing?

```
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
ma-search-users: Error.  Could not find ProfilesDirectory.
Error: Could not find the path /mnt/migrationassistant/Documents and Settings/mayo/NTUSER.DAT
Fatal: Could not find the USER registry hive at /mnt/migrationassistant/Documents and Settings/mayo/NTUSER.DAT
.
```

---

### Post by ago on 2007-10-26
Much better!

Reinstall and disable migration-assistant by commenting it out in ubuntu/install/preseed.cfg before rebooting

---

### Post by mayo2000 on 2007-10-26
> **ago said:**
> Much better!

Reinstall and disable migration-assistant by commenting it out in ubuntu/install/preseed.cfg before rebooting

bingo. issue resolved (stupid vista). thank you very much ago. BTW: are you involved into wubi development somehow? (stupid question). And is there any possibility for wubi to do installation part (copying files) directly in windows and only hardware detection (configuration) after windows restart?

---

### Post by mayo2000 on 2007-10-26
Ubuntu installed, but now I'am getting grub error:

Filesystem type is NTFS, partition type 0x7
kernel /boot/vmlinuz-2... root=/dev/hda1 ro quit splash locale=en_US

Error 17: File not found

---

### Post by ago on 2007-10-26
I wrote most of wubi and lupin, but many others have helped too. See the faq in the website.

---

### Post by ago on 2007-10-26
Mayo2000 almost there....

Edit ubuntu/disks/boot/grub/menu.lst

root(x,y) is probably wrong. 
X=disk 
y=partition

---

### Post by esox_hu on 2007-10-27
Hi ago!

I almost there...
Installation completed, but after reboot (I removed quiet splash) I got mount errors:

[I]mount: Mounting /dev/disk/by-uid/8Ab9-D0DC on / root failed: No such device
mount: Mounting /root on /host failed Invalid argument
ALERT! /host/ubuntu/disks/root.disks does not exist Dropping to shell...[/I]

Then dropped me to BusyBox shell.

Here is my menu.lst:
title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        (hd1,1)/ubuntu/disks
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=8AB9-B0DC loop=/ubuntu/disks/root.disk ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root        (hd1,1)/ubuntu/disks
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=8AB9-B0DC loop=/ubuntu/disks/root.disk ro single
initrd        /boot/initrd.img-2.6.22-14-generic

title        Ubuntu 7.10, memtest86+
root        (hd1,1)/ubuntu/disks
kernel        /boot/memtest86+.bin

Kind regards,
Esox

---

### Post by esox_hu on 2007-10-27
Hi ago,

I started v377 against NTFS partition. Virt. disk size 8 Gb.
But usr.disks has not been created.
Here is my directory structure:

Volume in drive D is SAMSUNG_180G
 Volume Serial Number is BC19-455C

 Directory of D:\ubuntu\disks

2007.10.27.  15:37    <DIR>          .
2007.10.27.  15:37    <DIR>          ..
2007.10.27.  15:35    <DIR>          boot
2007.10.27.  15:36     1.000.000.000 home.disk
2007.10.27.  15:36     6.000.000.000 root.disk
2007.10.27.  15:35    <DIR>          shared
2007.10.27.  15:36     1.000.000.000 swap.disk
               4 File(s)  8.000.000.000 bytes
               4 Dir(s)   5.222.412.288 bytes free


and of course, after reboot it hangs at 32% copying files...

Esox

---

### Post by jaezcurra on 2007-10-27
Hi Ago,

What about creating a new thread yourself with a kind of survey where you could ask ONLY people that have succeeded with the installation of 7.10 using Alpha wubi 7.10 (unfortunately I would not be included among those people) questions that maybe could lead you to guess why so many people are failing in their installation?

Maybe the answers of successful installers can make understand why not everyone is succeeding.

---

### Post by ago on 2007-10-27
I can get fairly good guesses from error reports... At the moment there are 2 bugs outstanding: update-grub generates a menu.lst with the worong device and large setups on FAT fail to create a usr.disk.

esox_hu replace root=... with root=/dev/sdXY

replacing X,Y for disk, partition of where you installed wubi. e.g. /dev/sda2

I will check the algorithm for 8GB, it is different from the one of 6GB, but probably similar issue. Should be a quick one.

If you are around tomorrow I can do with some help testing why grub gets the wrong device

---

### Post by xtreme777 on 2007-10-27
I was also having a problem with the 45% hang.  I deleted the user migration settings for the MADEV section but now when I click Forward it stays on screen 5 of 7.  I've also tried deleting the entire Migration assistant section but it does the same thing.  Any sugestions?

---

### Post by esox_hu on 2007-10-28
HI there,

Thx for your reply, I'll try to eedit menu.lst and write my progress later on...

Esox

---

### Post by evan d on 2007-10-28
> **mayo2000 said:**
> Hi no progress with rev377. When I check syslog dmp there some errors. Could Vista be the reason of freezing?

```
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
Unable to open the registry file at '/mnt/migrationassistant/WINDOWS/system32/config/software'
2: No such file or directory
ma-search-users: Error.  Could not find ProfilesDirectory.
Error: Could not find the path /mnt/migrationassistant/Documents and Settings/mayo/NTUSER.DAT
Fatal: Could not find the USER registry hive at /mnt/migrationassistant/Documents and Settings/mayo/NTUSER.DAT
.
```


Did you happen to save the full log file?  That bit alone would not cause the installer to fail.

Thanks!

---

### Post by garferi on 2007-10-28
Hi!
Installation stocked at 31%
Before the installation I used chdsk and disk defragment.

---

### Post by ago on 2007-10-28
> **garferi said:**
> Hi!
Installation stocked at 31%
Before the installation I used chdsk and disk defragment.

I need /var/log/syslog (from linux) 
ctrl+alt+f2 to get command line

---

### Post by xtreme777 on 2007-10-28
I am having the same issue of the install stopping at 31%, sometimes 30% after uncommenting the Migration Assistant Wizard in the config file.  I don't understand what you mean by getting the syslog.  How can you get a syslog when the install fails?  I am definitely a Linux noob.  Sorry.

---

### Post by ago on 2007-10-28
ctrl+alt+f2
sudo cp /var/log/syslog /isodevice || cp /var/log/syslog /host

this will get the log into the windows drive, then post it here

---

### Post by Alterno on 2007-10-29
I'm Using Wubi-7.10-alpha-rev377 . Ubuntu 7.10 Installation (Ubuntu 7.10-desktop-amd64.iso) hangs at 47%.

My sistem specs are:

Installing from Windows Vista
Intel Pentium D, Dual Core 3.2GHZ Sock 775
Kingston DDR667 2GB of Memory
EGVA Nvidia Gforce 7600GS
Intel Mother Board D946GZIS

---

### Post by ago on 2007-10-29
I'd need the syslog: [http://ubuntuforums.org/showpost.php?p=3657620&postcount=117](http://ubuntuforums.org/showpost.php?p=3657620&postcount=117)

---

### Post by garferi on 2007-10-29
When it stocked I tried Ctrl+Alt+F2 but it didn't respond...

---

### Post by ago on 2007-10-29
Are you using a SATA drive? With ntfs? Can you try on a different drive and/or a FAT partition?

---

### Post by Alterno on 2007-10-29
> **ago said:**
> I'd need the syslog: [http://ubuntuforums.org/showpost.php?p=3657620&postcount=117](http://ubuntuforums.org/showpost.php?p=3657620&postcount=117)

When Should I use ctrl+alt+f2 ?

---

### Post by ago on 2007-10-29
When it stops, assuming it's not a complete system freeze

---

### Post by Alterno on 2007-10-29
> **ago said:**
> When it stops, assuming it's not a complete system freeze

Anyone knows how I make these two colums:  | | ? alt + what? 
and where I should suppose to find the .log file?

---

### Post by ago on 2007-10-29
> **Alterno said:**
> Anyone knows how I make these two colums:  | | ? alt + what? 
and where I should suppose to find the .log file?

You can just issue 2 separate commands, one of the 2 will fail but you can ignore that. be aware that there are spaces in there... sudo [space] cp [space] source [space] destination

sudo cp /var/log/syslog /isodevice 
sudo cp /var/log/syslog /host

The log file is just called syslog. When you reboot in windows you will see that in C:\. You can view that with wordpad, and attach it to your post here.

NOTE: you have to start with a clean installation, uninstalling wubi first, and then installing again

---

### Post by PointyWombat on 2007-10-29
that's two pipes used as a list OR statement.

which in this context means that "cp /var/log/syslog /hostsudo" will only run if "cp /var/log/syslog /isodevice" returns something other than a successfull run (status 0)

a pipe is the vertical bar, typically above the enter key along with the back slash.

---

### Post by Alterno on 2007-10-29
It totally freezes at 47% even with rev 387.... :(. With the previous version of ubuntu I couldn't get to installation process like now. Maybe the next version is the charm? :D. Help I'm deseperate...

---

### Post by ago on 2007-10-29
What hard disk model do you have, what is the filesystem in there

---

### Post by Alterno on 2007-10-29
> **ago said:**
> What hard disk model do you have, what is the filesystem in there

Right now is NTFS 250GB
WDC WD2500BB-00RDAO ATA DEVICE
Western Digital

---

### Post by ago on 2007-10-29
> **Alterno said:**
> Right now is NTFS 250GB
WDC WD2500BB-00RDAO ATA DEVICE
Western Digital

That's an EIDE HD isn't it?

PS merging the thread

---

### Post by Alterno on 2007-10-29
> **ago said:**
> That's an EIDE HD isn't it?

PS merging the thread

Yeah is EIDE, so?

---

### Post by ago on 2007-10-29
I am trying to isolate patterns, most people experiencing the same problem until now were on sata.

---

### Post by Alterno on 2007-10-29
> **ago said:**
> I am trying to isolate patterns, most people experiencing the same problem until now were on sata.


Ok, I hope you find a solution. peace.

---

### Post by xtreme777 on 2007-10-29
I cannot post the log because my system complete freezes as well.  I'm trying this install on a HP dv9500 if that makes any difference.  All drives are SATA.

---

### Post by esox_hu on 2007-10-29
Hi ago,

is any new stuff in v381 that could be complete my installation?
You know mounting problems...etc.

Esox

---

### Post by ago on 2007-10-29
rev381 should (hopefully) generate a menu.lst  that grub4dos can use without trying to boot off the wrong device. I did not add anything specific for your mounting issues (which I still haven't been able to figure out) but I guess there is no harm in trying...

---

### Post by esox_hu on 2007-10-29
thanks ago,
I installed rev381, now I try it out...
Esox

---

### Post by Alterno on 2007-10-30
Any news about the problem with EIDE / SATA Hardisks?

---

### Post by ago on 2007-10-30
It might well be a problem with loopfiles in general rather than a missing driver, that would require a patched kernel, and it might be a bit more complex.

---

### Post by Alterno on 2007-10-30
> **ago said:**
> It might well be a problem with loopfiles in general rather than a missing driver, that would require a patched kernel, and it might be a bit more complex.
Yikes... so that means thatI'll have to wait till Ubuntu 8.0 to install it? I was able to run it from the live CD btw.

---

### Post by madduffy on 2007-10-30
I am having the 'installation sticks at %' plus the system hung when I tried to access the terminal. I will run the logging later, but here are my specs

2 Opteron 244
1 gig ECC ram
Harddrive is 300 gig total, IDE,
part 1 is 261 gigs of ntsf
part 2 is probably like 17.5 gigs of backup, also ntsf.
On the same IDE channel I have a DVDrw drive.

Side note: Immediately after installation and reboot, my computer would hang during boot and the screen would go black. Swapping my graphics card (Radeon 9800pro to nVidia GeForce2) got my screen back, but then I ran into the other problem. I'll try dealing with this later, as that card has always been a pain.

---

### Post by mayo2000 on 2007-10-30
> **evan d said:**
> Did you happen to save the full log file?  That bit alone would not cause the installer to fail.

Thanks!

Hi,
I realized that I had luck which probably won't repeat again soon.
I thought that MIGRATION section was the issue so I commented it out. Ubuntu installed succesfully. I also had to correct the root param in menu.lst. But Ubuntu didn't start. So I decided to reinstall it. But this time  ubiquity hang again at 40% (actually this percentage is different for every attempt). So I don't think it is migration issue anymore.

And that was full syslog which I posted. I gave up trying wubi, I'll rather use Lubi/Bubackup this time.

My drive nfo: Seagate Momentus 5400.3, SATA SerialATA/150

---

### Post by madduffy on 2007-10-30
> **madduffy said:**
> I am having the 'installation sticks at %' plus the system hung when I tried to access the terminal. 

Good news! After successfully booting to Windows (and re-inserting my 9800), my second attempt to boot into Ubuntu and complete my installation went smoothly. No hanging or halting, it was quite quick. I did not do a checkdsk or change my wubi settings or reinstall wubi, I just selected it from the boot menu and it succeeded.

The only thing different from before is that I took out my second disk, which is SATA. I don't know if that is related but its the only thing I haven't plugged back in since my boot problems. That and I did switch IDE ports on my motherboard. I'll be trying to add that hard drive back soon and I will report back if there are any issues.

Wubi is an excellent product, I cannot wait to recommend this newest version to my friends once the kinks are worked out.

* also, ntsf = ntfs , heh

---

### Post by madduffy on 2007-10-30
Ah ha!

Plugging and unplugging the SATA drive leads me to believe that it was the problem all along.

Putting it back in caused a busybox prompt at start up.
Removing it allows me to boot into ubuntu normally.

---

### Post by madduffy on 2007-10-30
edited

---

### Post by ago on 2007-10-31
> **Alterno said:**
> Yikes... so that means thatI'll have to wait till Ubuntu 8.0 to install it? I was able to run it from the live CD btw.

No, that means that we have to ship a patched kernel and that might delay the release a bit

---

### Post by cheddarmakerman on 2007-11-01
I also get to about 45% and freeze... /var/log/syslog is attached

It looks like the migration assistant fails, could that be it?  If so maybe I could disable it?

---

### Post by cheddarmakerman on 2007-11-01
fixed, I noticed that the wubi install was creating a wubi.mbr in my V: (virtual) drive as well as in the root of C:\.  uninstalled wubi and removed the virtual drive subst /d v: and reinstalled.  worked like a charm.  I doubt that many others have the same problem but hopefully this will help somebody

thanks and keep up the great work! :KS

---

### Post by ahecht on 2007-11-02
Do you think that the installer could run a ```
fsutil dirty query X:
``` on the installation drive before a reboot and then if the drive is dirty offer to run chkdsk (or schedule chkdsk for a reboot if Wubi is being installed on a system drive)? At least provide a warning before rebooting -- it's kinda annoying to start an install, reboot, wait for ubuntu to load, and then find out that your drive is dirty and that you have to reboot, uninstall, chkdsk, and then reinstall.

Also provide a warning that chkdsk may screw things up. I just ran chkdsk /R so that I could try installing Wubi, and it screwed up my system enough that I had to reinstall Windows.

---

### Post by molk on 2007-11-02
> "Do you think that the installer could run a fsutil dirty query X: on the installation drive before a reboot and then if the drive is dirty offer to run chkdsk (or schedule chkdsk for a reboot if Wubi is being installed on a system drive)?"


I agree that a check for the partition being dirty should be done in Windows before reboot. I do, however, want to point out that the fsutil command is not available on Windows 2000 and below. XP is the OS in which it first appeared.

---

### Post by ago on 2007-11-02
> **ahecht said:**
> Do you think that the installer could run a ```
fsutil dirty query X:
``` on the installation drive before a reboot and then if the drive is dirty offer to run chkdsk (or schedule chkdsk for a reboot if Wubi is being installed on a system drive)?
That is a good idea and we will implement that. The issue as highlighted is that fsutil is not widely available. 

> Also provide a warning that chkdsk may screw things up. I just ran chkdsk /R so that I could try installing Wubi, and it screwed up my system enough that I had to reinstall Windows.
First time I hear that, 
That's a microsoft problem though, i am certainly not going to fix their programs.. :P

---

### Post by ahecht on 2007-11-02
> **ago said:**
> That is a good idea and we will implement that. The issue as highlighted is that fsutil is not widely available.

I believe chkntfs is available in NT4, 2000, and XP, and will also identify dirty volumes (it just doesn't have the ability to set the clean bit without running chkdsk). So, for compatibility, you could instead run ```
chkntfs x:
```


> **ago said:**
> First time I hear that, 
That's a microsoft problem though, i am certainly not going to fix their programs.. :P

I wasn't saying you should fix their problem, just that you should warn the user before scheduling a chkdsk on the system drive.

---

### Post by ago on 2007-11-02
> **ahecht said:**
> I believe chkntfs is available in NT4, 2000, and XP, and will also identify dirty volumes (it just doesn't have the ability to set the clean bit without running chkdsk). So, for compatibility, you could instead run ```
chkntfs x:
```

I'd need that as a library call (for instance to be able to add progressbar), possibly compatible with different windows versions (also 64bit). Haven't had time to investigate that yet.

> I wasn't saying you should fix their problem, just that you should warn the user before scheduling a chkdsk on the system drive.

makes sense

---

### Post by xtreme777 on 2007-11-02
Just wanted to let you know that revision 383 solved the issues I was having installing Ubuntu on my HP dv9500 laptop.  You are awesome!  Thanks for all your hard work!

---

### Post by KDE-fan on 2007-11-03
I had the same problem the first time I tried to install Kubuntu 7.10 to my new 320 GB hard drive, but it worked perfectly the second time I tried. This is what I did differently the second time:

1. Left 300 GB of free space at the end of the hard drive
2. Surfed Internet during installation with Konqueror. (reading this thread actually)
3. Opened and closed a window by pressing a button named "Advanced". You can see this button on this picture: [COLOR="DarkRed"][http://i.zdnet.com/gallery/171011-525-393.jpg](http://i.zdnet.com/gallery/171011-525-393.jpg)[/COLOR], although the colors in Kubuntu are obviously much more beautiful.

Edit: I do not use wubi at all.

---

### Post by ahecht on 2007-11-05
> **ago said:**
> I'd need that as a library call (for instance to be able to add progressbar), possibly compatible with different windows versions (also 64bit). Haven't had time to investigate that yet.

I'm not that familiar with NSIS (I haven't looked at using it in years), but couldn't you use something like the ExecDOS plugin to run chkntfs and parse the output from stdout?

---

### Post by ago on 2007-11-05
> **ahecht said:**
> I'm not that familiar with NSIS (I haven't looked at using it in years), but couldn't you use something like the ExecDOS plugin to run chkntfs and parse the output from stdout?

Chkdsk is slow, so I need a progress bar or most people would think that the installer has jammed. To get a progress bar I need a library.
There is [http://msdn2.microsoft.com/en-us/library/aa384915.aspx](http://msdn2.microsoft.com/en-us/library/aa384915.aspx) but still haven't had time to play with it.

---

### Post by Gilean on 2007-11-05
Hi Ago, i tried to to install on my pc the wubi rev 383. The 64 bit edition of gutsy was ok, but the 32 bit stop when copying files at about 32%

---

### Post by ago on 2007-11-06
Couple of options. If you are on a 32 bit system, try to replace /ubuntu/install/boot/initrd.gz with the following: [http://wubi-installer.org/devel/test/initrd.gz](http://wubi-installer.org/devel/test/initrd.gz) . Then reboot into Ubuntu.

Also, some bugs have been reported for NVIDIA hardware. 

[https://bugs.launchpad.net/ubuntu/+bug/157777](https://bugs.launchpad.net/ubuntu/+bug/157777)
[http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

Can you pls confirm one way or the other?

---

### Post by elfejoyeux on 2007-11-07
Hi ago !
I've just tried this initrd, and... it doesn't work :'(
It stucks at 33, 44 or 46% (it changes at each try) in ubuntu.

If it helps you :
SATA HD, P4HT, intel GMA, WIN XP NTFS...
I've access to internet through a (*******) proxy, so I downloaded the desktop 7.10 iso.
I don't know if it's an internet or a SATA or another problem...

---

### Post by Gilean on 2007-11-08
> **ago said:**
> Couple of options. If you are on a 32 bit system, try to replace /ubuntu/install/boot/initrd.gz with the following: [http://wubi-installer.org/devel/test/initrd.gz](http://wubi-installer.org/devel/test/initrd.gz) . Then reboot into Ubuntu.

Also, some bugs have been reported for NVIDIA hardware. 

[https://bugs.launchpad.net/ubuntu/+bug/157777](https://bugs.launchpad.net/ubuntu/+bug/157777)
[http://ubuntuforums.org/showthread.php?t=585714](http://ubuntuforums.org/showthread.php?t=585714)

Can you pls confirm one way or the other?

Ei ago, i'm italian can i speak in italian to u? (u are italian :P). if not, plz check this. I used wubi on my laptop, i started in verbose (caused by bluetooth bug we speak early). then i wrote startx and started the live. I opened terminal and wrote ubiquity --automatic , wubi starts to install but it freezes at 15% checking systema configuration..:confused:

---

### Post by ago on 2007-11-08
> **Gilean said:**
> Ei ago, i'm italian can i speak in italian to u? (u are italian :P). if not, plz check this. I used wubi on my laptop, i started in verbose (caused by bluetooth bug we speak early). then i wrote startx and started the live. I opened terminal and wrote ubiquity --automatic , wubi starts to install but it freezes at 15% checking systema configuration..:confused:

Si sono italiano. System freeze o solo ubiquity? Cosa vedi in /var/log/syslog? Puoi usare tail -f /var/log/syslog mentre fai girare ubiquity ed avviare ubiquity con --debug.

---

### Post by Gilean on 2007-11-08
> **ago said:**
> Si sono italiano. System freeze o solo ubiquity? Cosa vedi in /var/log/syslog? Puoi usare tail -f /var/log/syslog mentre fai girare ubiquity ed avviare ubiquity con --debug.

ti postero' il piu' presto posssibile i logs, in ogni caso non freeza, posso sempre usare la live, semplicemente il check del file systema rimane a 15%

p.s.ma non avete un forum ufficiale su wubi?

---

### Post by ago on 2007-11-08
> **Gilean said:**
> p.s.ma non avete un forum ufficiale su wubi?

Questo e' il forum ufficiale!

---

### Post by Gilean on 2007-11-08
> **ago said:**
> Questo e' il forum ufficiale!

ops non avevo notato sorry :P

---

### Post by adromidon on 2007-11-09
I am having a similar issue it freezes at 46% on the laptop during the install.

When I installed it on the desktop it installed completely but the screen was black up until it restarted then it worked fine.

How can I check the /var/log/syslog if ubuntu is not installed completely?

Edit/Update: Upon letting it sit frozen for about 30 minutes I restarted the computer and ran the Ubuntu part of the install again this time it went past the part it usually froze at and completed the install. I am not sure what made it hang the first time but just a simple restart back into Ubuntu fixed it :) I am not sure if this help but I figured I would post what happened upon restart

---

### Post by Scoty on 2007-11-11
with Buil 384 Ubuntu 7.10 hang on 22%, with Build 383 is ok.

---

### Post by ago on 2007-11-11
> **Scoty said:**
> with Buil 384 Ubuntu 7.10 hang on 22%, with Build 383 is ok.

That's more likely because the hangs are random... They are due to some issues with current kernel, I am waiting for the next SRU.

---

### Post by adromidon on 2007-11-12
> **ago said:**
> That's more likely because the hangs are random... They are due to some issues with current kernel, I am waiting for the next SRU.

Hey Ago is this issue more present with a specific architecture then another?

I used a i386 gutsy ISO and Wubi to force a 32bit install on my laptop and it worked with the exception of the freeze mentioned a few posts above. However a friend of mine has used Wubi to download the 64bit on the same laptop and got a whole new series of problems. I was just not sure if this error was specific to 32bit installs or if it can happen with 64bit as well

---

### Post by ago on 2007-11-12
So far most people seem to be affect when using SATA, I did not get much in terms of architectures, it would help to gather the results of a few stats (lspci -v, uname -r, hdparm -I...) and post it.

---

### Post by maravena on 2007-11-12
Hi!!

I installed Kubuntu with WUBI in my PC (IDE disk), then I installed KUBUNTU with WUBI in my notebook and it stopped at 48%, then copied all files form my pc to  my laptop (Dell Inspiron 6400 with SATA disk), and finally, i modified menu.lst:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
find		--set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
kernel		/ubuntu/disks/boot/vmlinuz-2.6.22-14-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/ubuntu/disks/boot/initrd.img-2.6.22-14-generic

/dev/sda2 is the partition where I copied the files. Now, I am posting this in my notebook  :)

Bye!!!

---

### Post by gubemton on 2007-11-12
What about sharing those files with other less fortunate? :)

---

### Post by maravena on 2007-11-12
Hi!!

When I say "all files ", I mean configuration files and virtual disk file. The size of virtual disk  file is 15GB.

sorry .

Bye!

---

### Post by Scoty on 2007-11-13
with last Build 366 i can not install Ubuntu. i see only the first Boot Screen and after this only black Screen and nothing working.

---

### Post by ago on 2007-11-13
366 is a bit old, you might want to try more recent builds
You can press esc during countdown and select "safe graphic mode"

---

### Post by Scoty on 2007-11-13
> **Scoty said:**
> with last Build 366 i can not install Ubuntu. i see only the first Boot Screen and after this only black Screen and nothing working.

sorry 386, not 366 ;) .

---

### Post by linux_newby on 2007-11-13
The update too for ever but it went through eventually. But I lost the DSL connection and got some Internal Error: Failed to initialize HAL. Since I am a total newby I didn't figure out how to solve the problems and uninstalled everything again.

I wonder if Ubuntu 7.4 installed with Wubi is not meant to be updated to 7.10 or if I should try again.

Also I read only after the install that Linux doesn't like NTFS partitions. Must I reformate the partition where I want Linux to be to FAT32 or does the install program take care of this?

---

### Post by ago on 2007-11-13
> **linux_newby said:**
> I wonder if Ubuntu 7.4 installed with Wubi is not meant to be updated to 7.10 or if I should try again.
No upgrades from 7.04 to 7.10 are not supported at the moment. Upgrades will be supported from 7.10 -> 8.04

> Also I read only after the install that Linux doesn't like NTFS partitions. Must I reformate the partition where I want Linux to be to FAT32 or does the install program take care of this?
That's not correct.  What happens is that new users tend to hardreboot to get out of trouble, and because of that they end up with a corrupted ntfs partition.

---

### Post by syarost on 2007-11-18
Any solution yet?   I have tried revision 386 and am still hanging at 47%.  I am running on an Dell Inspiron 9400 with a Core 2 Duo 7400, 2GB Memory, NVIDIA 7900 GS with 256 MB, and a Hitachi Travelstar 7k200, 200 GB SATA.  I am running Windows XP Pro with all updates.

---

### Post by adromidon on 2007-11-19
> **syarost said:**
> Any solution yet?   I have tried revision 386 and am still hanging at 47%.  I am running on an Dell Inspiron 9400 with a Core 2 Duo 7400, 2GB Memory, NVIDIA 7900 GS with 256 MB, and a Hitachi Travelstar 7k200, 200 GB SATA.  I am running Windows XP Pro with all updates.

I got this working by hittting the power button on my machine which caused Ubuntu to shutdown gracefully then reboot into it this cause the install the finish at least for me

---

### Post by syarost on 2007-11-19
I tried that with earlier revisions, but have not tried that with the current revision.  When I restarted the system using earlier revisions, it would repeat the installation, stopping in the same place, while copying files.  I will report back after I have tried.  Thanks for the suggestion.  

 I don't want to create a separate partition, because using FIXMBR to remove the grub loader causes issues with the dell restore partition.

---

### Post by adromidon on 2007-11-19
> **syarost said:**
> I tried that with earlier revisions, but have not tried that with the current revision.  When I restarted the system using earlier revisions, it would repeat the installation, stopping in the same place, while copying files.  I will report back after I have tried.  Thanks for the suggestion.  

 I don't want to create a separate partition, because using FIXMBR to remove the grub loader causes issues with the dell restore partition.

There is an alternative to using fix MBR if you have Vista you can install Grub to the /boot partition of Ubuntu then use a program called EasyBCD in Vista to add Ubuntu to the Windows boot menu thus not affecting the MBR at all

---

### Post by syarost on 2007-11-20
I have not made the move to Vista on this laptop.   I am running Windows XP Pro.  

Is there a way of removing the GRUB loader on a Windows XP machine, and retaining the capability to use CTRL-F11 to do a Dell System Restore?   This was the reason I started using wubi 7.04. for the capability to back out without messing up my Windows XP installation.

---

### Post by adromidon on 2007-11-20
hmm Not sure about that one

---

### Post by syarost on 2007-11-25
I tried restarting my installation after it stalled, but this made no difference.  It stalled in the same place.  Any other suggestions?   Ago?

---

### Post by ago on 2007-11-26
The stall is a kernel issues, whish is difficult to fix for the time being.
You can install regular ubuntu, without installing grub in MBR, then boot it via grub4dos which is fired up from within ntldr (boot.ini).

---

### Post by syarost on 2007-11-26
Are there directions on how to do this?  Specifically, how do you install Ubuntu without installing the GRUB loader?

---

### Post by lvleph on 2007-11-27
> **syarost said:**
> Are there directions on how to do this?  Specifically, how do you install Ubuntu without installing the GRUB loader?

I think [this](http://lubi.sourceforge.net/unetbootin.html) will, and uses its own partition. Not exactly sure that it doesn't use GRUB, but it seems like it doesn't.

---

