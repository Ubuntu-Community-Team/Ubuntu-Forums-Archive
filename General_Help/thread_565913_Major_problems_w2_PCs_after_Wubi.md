---
title: "Major problems w/2 PCs after Wubi"
date: 2007-10-02
forum: General Help
---

### Post by ZenWarrior on 2007-10-02
My Wubi feedback starts here:  [http://ubuntuforums.org/showpost.php?p=3456076&postcount=180](http://ubuntuforums.org/showpost.php?p=3456076&postcount=180)

To quickly catch you up, I installed Wubi on two PCs. Both installations seemed to go without a hitch. However, I now have significant and potentially catastrophic problems on both machines.

On the first, where I installed Wubi/Ubuntu, I have no video while in Wubi/Ubuntu. That occurred after enabled the restricted driver(?) needed for my ATI graphics card. The computer now simply freezes at a black and empty window during startup.

On the second, where I installed Wubi/Kubuntu, my backup hard drive's data is no longer visible or accessible by XP. (Unfortunately, it also contains some data not backed up.) I receive an error message when the OS attempts to access the drive. The folders are still visible on the drive, but all report as empty now. They were fine less than 24 hours ago when I last used Wubi/Kubuntu. Also, Check Disk will not run on the drive. An error message simply states that Check Disk cannot be started.

However, I'm praying there's hope. A Properties check of the drive correctly shows the free and used space allocations. That's although the only data visible on the drive are two files, wubildr and wubildr.mbr--which take only a few hundred KB. As I have said before, it's as if the data is still there, but XP has no idea how to get to it, nor can it read or write from or to the drive.

Help would be most appreciated. Please? TIA.

---

### Post by ZenWarrior on 2007-10-03
Additional info: Although I could see all my external storage devices (inc. my backup drive) before there seemed any problem (prior to shutdown only 24 hours ago), I cannot see them anymore--after simply starting up with XP Tablet this morning. I also cannot navigate to any external drives via any menu. 

So in sum, I can see my external devices in XP, but cannot see or access the data on them. In Wubi/Kubuntu, everything external appears to have vanished. 

Question: Will simply uninstalling Wubi/Kubuntu and Wubi/Ubuntu resolve my stated problems? At this point, I'm very much willing to go back in time.

---

### Post by ago on 2007-10-03
> **ZenWarrior said:**
> On the first, where I installed Wubi/Ubuntu, I have no video while in Wubi/Ubuntu. That occurred after enabled the restricted driver(?) needed for my ATI graphics card. The computer now simply freezes at a black and empty window during startup.
Ctrl+Alt+F2 
sudo dpkg-reconfigure xserver-xorg

> On the second, where I installed Wubi/Kubuntu, my backup hard drive's data is no longer visible or accessible by XP.
Boot from rescue CD ([http://www.tweakxp.com/article36941.aspx](http://www.tweakxp.com/article36941.aspx)) and run chkdsk from there.

You can also try to access the drive from within Linux.

---

### Post by ZenWarrior on 2007-10-03
First, thank you so very much for the assistance. Pretty much freaking out here--especially about my backup hard drive. 

As for the machine with the video problem, I have no true rescue disk. You know, it's one of those all or nothing recovery disks that will leave my machine in a "new, pristine" state--with none of my data, programs, or settings.

That said, just moments ago (before seeing your reply) I attempted to uninstall Wubi/Ubuntu from the machine with the video problems. From a first glance, it appears to have uninstalled properly--except for Wubi remaining in the Add/Remove program list. Am rebooting now and hoping I reboot in the pre-Wubi past. <fingers crossed>

EDIT:  Thanks for the link to the "Install Recovery Console without an XP CD." I'll get my courage up a little later this morning, cross my fingers, and hope for the very best. Truly, thank you again.

---

### Post by ZenWarrior on 2007-10-03
Update: After restarting the PC witch had Wubi/Ubuntu installed, all appears well at first glance with the exception of Wubi remaining in the Add/Remove programs list. And, clicking it brings up the usual dialog asking if the Wubi files should be backed up. It appears Wubi doesn't know it has been removed and is no longer alive. 

That said, I'll extricate the Add/Remove program entry manually. Thanks to help here, that should restore this PC to its pre-Wubi/Ubuntu state. I'll just install Ubuntu the old-fashioned way when my courage returns. Thanks again for the help. 

(Again, I'll have to have a few stiff drinks before risking the complete lost of my backup drive's data. Any file viewer says there is no data but as I said, Properties does show the correct allocations of free and used space on the drive. Mucho thanks again.)

---

### Post by ZenWarrior on 2007-10-03
First, my most humble thanks again. 

One computer is now again well and all appears as it should. However, I am a tad sad about having to uninstall Wubi/Ubuntu. I've been swearing to get away from Microsoft for years now and thought I had. Oh well, moving on...

...I am now fully awake and have found the courage to attempt restoring my other computer, the one which no longer recognizes any external drives, particularly my backup drive and its much-needed data.

How do I go about running Check Disk from within Wubi/Kubuntu when I cannot even see the external drives? Or, are you saying I should run it on my primary  C: drive? And if a command line process, might someone be a little more specific about the entire process? Please? I'm clueless here.

And once again, thanks. 

(I really hate to be doing this. You have no idea how happy I was when I first thought all had proceeded without any problems. I'm really bummed--it's back to Microsoft, at least for the foreseeable future.) 

Oh, and just to be certain--are you saying that simply uninstalling Wubi/Kubuntu from the other computer will *not* restore all functionality and allow my external drives to be properly seen and accessed? If it would, I'd really just rather do a simple uninstall so I can quickly get the computer back to work--and hopefully as it was before Wubi/Kubuntu.

---

### Post by ZenWarrior on 2007-10-03
Update: I just tried to download the RC.iso, but received:

[I]Page URL Not Found!!
The requested page does not exist on this server. The URL you typed or followed is either outdated or inaccurate. [/I]

Might it be elsewhere? Or, am I  looking at trying to recover my external hard drive and data without it?

---

### Post by ago on 2007-10-03
[http://www.thecomputerparamedic.com/files/rc.iso](http://www.thecomputerparamedic.com/files/rc.iso)

---

### Post by ZenWarrior on 2007-10-03
Thanks again. I found and have downloaded the image.

However, I want to be certain about the question I asked. That is, will simply uninstalling Wubi/Kubuntu restore all to as it was pre-Wubi/Kubuntu? Or, is using the RC.iso an absolute must at this point? 

Again, thanks--especially for responding so quickly this morning. I may just get some real work done today!

(Damn. No blank CDs. So much for the work needed for today getting done. Bummer.)

---

### Post by ago on 2007-10-03
> **ZenWarrior said:**
> However, I want to be certain about the question I asked. That is, will simply uninstalling Wubi/Kubuntu restore all to as it was pre-Wubi/Kubuntu? Or, is using the RC.iso an absolute must at this point?

Some of the issues you have were likely due to a hard reboots more than wubi. Hard reboots do corrupt the file system and you need to run chkdsk to fix them. Whether wubi (ntfs-3g) makes things worse in this respect is an open question.

Uninstalling wubi does not fix a corrupted filesystem. An uninstallation does 3 things: removes the wubi folder, removes the wubi registry key, removes the bootloader entry and related files (wubildr*). Hence an uninstallation gives back the disk space and registry settings as they used to be.

---

### Post by ZenWarrior on 2007-10-03
Thanks again for helping.

As a bit of an update, I just looked at the Wubi/Kubuntu PC and where I could see my backup drive just last night (but not access it), it now has also disappeared from view in XP. So, I now cannot see the drive either in XP or Wubi/Kubuntu. Will this be an issue after I burn the RC.iso and attempt to run it?

Oh, and there were no hard crashes/reboots on the PC after Wubi/Kubuntu was installed and used the first night. And, I ran defrag and chkdsk on it right before installing Wubi/Kubuntu. That's why my initial review raved about it. At that time, absolutely nothing looked or acted amiss from either OS. It was the next morning, when I turned the machines back on after clean shutdowns the night before, that problems began.

---

### Post by ZenWarrior on 2007-10-03
**ago**, I finally found a blank CD, burned the image, started up my PC, arrived at C:\Windows, and ran chkdsk. Maybe I'm not following you, but that came back as I expected--clean. (I ran it on C: drive.)

I'm not having a problem with my C: drive at all, but instead cannot see my external hard drives at all now, neither in XP nor Wubi/Kubuntu--although I could at least see them in XP last night. I shamefully admit it's been eons since I last used command line in either PC/MS-DOS or VAX. (That's actually part of why I'm trying Linux--to remember again.) So, my memory there is more than a tad rusty.

Might you tell me what to do next? I attempted to run chkdsk on what I thought was my backup drive's designation ( F: ), but was told such a drive was not valid or did not have a disk. 

So, just to refresh, I'm now in DOS at C:\Windows, but still have no idea how to go about getting my backup/external drives/data back. 

More help? Please?

---

### Post by ZenWarrior on 2007-10-03
**ago**, you're a genius! All is well again. My drives and data are back after I shut everything down and rebooted the PC and external drives. ***Thank you.***

With that out of the way, what might you advise? I do wish to give Wubi/Kubuntu a real try. As I said, crashes nor reboots occurred to create the problem. I've decided to just leave Wubi/Ubuntu off this system entirely, but am still daring enough to risk a system to your cause.

In your best estimation, is this something which is likely to occur again? What can I do to minimize my exposure? The external drives were synched so I thought I was keeping two extra copies of everything--only to find them both seemingly MIA there for a while.

So, I'll get back up on the horse, but please pass along any advice you might have. Thanks again. Truly, if Wubi is your baby, you've got a real winner when we work out the kinks. The world is waiting for this big time. And, I'd still like to think it might not be too great a risk to install Wubi/Edubuntu on 4 other computers. (There is an Edubuntu version, right?)

---

### Post by ago on 2007-10-03
It's quite simple really: don't hard reboot and you'll be fine.

---

### Post by ZenWarrior on 2007-10-03
> **ago said:**
> It's quite simple really: don't hard reboot and you'll be fine.

Again, there was **_never_** a hard reboot or crash after installation. After the initial install and using it for an hour or so, I shut down the PC (actually, both of them) via the Start menu. So, that could **_not_** have caused the problem. If you think that is the **_only_** way the problem could manifest, I assure you it is not.

Many, many thanks! :guitar:

---

### Post by ago on 2007-10-04
Hmm never seen that before, all reported cases of filesystem corruption so far were due to hard reboots. If you'd be able to replicate that, it might be very useful.

---

### Post by ZenWarrior on 2007-10-04
I was wondering when you'd get around to the replication issue. :) That is something I usually do for myself, just to know and/or confirm. That said,...

...there is a bit of an update. After declaring all was well yesterday, and it was, I worked in XP (Tablet) for a while and then decided to play around in Wubi/Kubuntu a bit more. Get this...

...the problem was there again! My external drives were again "gone." And as before, no crash or hard reboot ever occurred. Had I your phone number, you would have received a phone call letting you know the problem had replicated itself. :)

So, I again went through the repair routine you suggested. However, I took two additional steps. First, as soon as all was well again, I promptly uninstalled Wubi/Kubuntu. But, I decided to be daring and then installed **Ubuntu** with Wubi the second time around. 

There may or may not be just a little something different, but the problem has not at all manifested with the Wubi/Ubuntu combination. I cannot imagine what the difference might be, but my [admittedly minor and essentially clueless] sleuthing seems to point to something with **Kubuntu** since all continues without a hitch using **Ubuntu** and Wubi. My gut tells me it's not Wubi in-and-of itself that has the problem, but is either Kubuntu-specific or a Wubi/Kubuntu *interaction*. 

I'm certain that tells you almost nothing, and I'm sorry I cannot report anything more. However,  I have come to a personal conclusion to avoid the Wubi-**Kubuntu** combo and only install Wubi-**Ubuntu**. 

And once more for good measure, ***thanks a bunch!***--for both Wubi and your help. I'm still onboard and will duly report anything else amiss that I might see.

---

### Post by ZenWarrior on 2007-10-04
Something relatively minor--after using Add/Remove Programs to uninstall Wubi, the line entry remains although the report states Wubi has been uninstalled. If you click it again, it again attempts to uninstall Wubi (which is no longer there), but there is no error message. (You know, like the one that typically says the program already seems to have been uninstalled and you are asked if you'd like to just go ahead and remove the line entry.) It even asks again if you want to save the backup files. Clicking yes or no makes no difference at this point. I've seen this three times now so it doesn't seem to be a random occurrence.

---

### Post by ZenWarrior on 2007-10-05
Just FYI, **ago**. Regarding the uninstall remnant mentioned above, I just noticed the Wubi uninstall file remains in the Windows folder after Wubi is uninstalled. 

Also, did anyone see the article by Larry Magid in today's New York Times (Circuits section) about Linux? It touted Ubuntu's present ease of use. Unfortunately, no mention was made of Wubi. Therefore, I took it upon myself to write the article's author letting him know about Wubi. If lucky, maybe he'll throw in a follow-up mention. :guitar:

NYT article URL:  [http://www.nytimes.com/2007/10/04/technology/circuits/04basics.html?ref=circuits](http://www.nytimes.com/2007/10/04/technology/circuits/04basics.html?ref=circuits)

---

### Post by GrayMatter on 2008-12-12
Sorry to bump this old thread but I have just experienced something similar.

I installed Ubuntu 8.10 using Wubi.  All went fine the first time I had a look at it.  The second time (this evening) I was trying to get my wireless network up and running and the networking seemed to hang.  I killed the task and decided to try again later.

I shut down Ubuntu and restarted the PC (without turning off).  The machine refused to boot into Windows.  After a bit of research and troubleshooting it seemed like my main drive had dissapeared.  My second drive was still visible.  The strangest thing is that my second drive which was an old Windows XP installation was not showing the wubildr.* files and the machine was asking if I wanted to go into XP or Ubuntu at startup.  This despite me never installing Ubuntu on this drive in any way shape or form.  My main drive would not even show up in the BIOS.

After much panicing I eventually powered off the machine.  When I turned it back on, everything was back to normal.  Both drives were visible and XP started just fine.

Some additional comments:

1) Both drives are Seagate SATA drives.
2) I shut down Ubuntu properly and did not just reset or power off.
3) There was no data corruptions on the main drive.  I have disconnected the secondary drive and will take a look at it later.

It's almost like Ubuntu shut down the drive until I rebooted yet some of the data was being cached by the machine.

---

