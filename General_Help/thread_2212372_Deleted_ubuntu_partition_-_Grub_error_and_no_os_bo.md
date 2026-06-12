---
title: "Deleted ubuntu partition - Grub error and no o/s boot"
date: 2014-03-20
forum: General Help
---

### Post by Ace..... on 2014-03-20
I got a call from my 15 year old son tonight: "I've deleted a partition and now my PC wont boot.... I think I deleted ubuntu. It was an unrecognised file system".
If he'd called me first.......

Who started this myth that 15 year old kids know everything about computers?

Anyway, we all make mistakes; and then we learn, so:

1. His is the only PC in the house.
2. He does have the full Win7 install disk.
3. Ideally he would benefit from getting the grub sorted, to boot into win, so that he is up and running.
4. He is here with me over the weekend, so I can burn a CD if required.
5. Is it possible to revert to the standard boot into win, so that he can follow standard procedure to reinstall ubuntu?
6. Any help - step by step guide, would be appreciated.

:)

---

### Post by deadflowr on 2014-03-20
He should be able to run the windows disk to repair the boot loader for that.
[http://www.techsupportalert.com/content/how-repair-windows-7-system-installation-disc.htm](http://www.techsupportalert.com/content/how-repair-windows-7-system-installation-disc.htm)

---

### Post by Ace..... on 2014-03-20
Thanks deadflowr,
That looks to be a good link.
I'll follow up next week, when he has had a chance to follow the guide.
:)

---

### Post by Ace..... on 2014-03-24
No... it didn't work.

It may be that it can only repair multi-boot created in Windows.
This GRUB was created by Ubuntu.

Anybody got any other suggestions?
:)

---

### Post by oldfred on 2014-03-24
That should have worked.

BIOS based systems boot from MBR which is tiny by today's standards.
The grub boot loader has a bit of code in the MBR that looks for partition with rest of grub install usually the / (or /boot) partition.
The Windows boot loader has code to find Windows partition. It uses boot flag to find that partition.

Is boot flag on Windows partition. Usually Windows 7 has a separate (hidden) 100MB boot partition that should have boot flag.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

But if son is randomally deleting stuff from system who knows what he has done. I hope you have good backup procedures in place.

---

### Post by Ace..... on 2014-03-24
Thanks for the response.

I'm fairly certain that he was not deleting stuff randomly.... he saw 200Gb that he thought was unused and decided to delete what he thought was just empty.
It may seem daft to us..... he didn't even need to do it, cause he'd just installed a 500Gb H/drive.

It seems to be part of human character:- "I've got the tools to clean up so I'm gonna clean up".
He's not the first and he won't be the last.
I didn't come down on him at all - the problem he created was, and is, a sufficient whack on the backside ;)

I believe he re-formatted the free space, and only discovered a problem when he switched off, and tried to switch on.

He told me he ran the utility 3 times.
It suggested removing cameras, which he did.

I will study the links Old Fred provided.

I'm sure we can get him through this :)

To be continued......

---

### Post by oldfred on 2014-03-24
One of the issues always is that Windows does not correctly see Linux partitions.

---

### Post by Hodevah on 2014-03-24
This is what is best to do if you want a return of GRUB. It is an easy fix if you can spare approx 10 mins or so after you have all your provided softwares.   (1) Install Ubuntu-Remix. You can do so via CD or USB.  If done via USB, go to Pendrivelinux.com.    (2)Install the latest YUMI on either your USB or HDD.  YUMI is cross-platform. So since you will be using Windows as a result of not having access to Ubuntu, use the Windows installer of YUMI.   (3)Start up YUMI. Select from the list your USB stick that you will be using to boot your computer with eventually. Select to install the UBUNTU-REMIX.  You can, if you want, also get the UBUNTU-Remix from here: " https://wiki.ubuntu.com/UbuntuGNOME/ReleaseNotes/12.10"    (4)After the install of Ubuntu-Remix on your USB, boot your HDD from USB.   (5)Go to BIOS to ensure your computer boots USB first, not the usual hard-drive.    (6)When Ubuntu-Remix starts, go to the Unity Panel. Select  BOOT REPIAR.      (7)Ensure that your wifi is connected. Fix and re-install GRUB using BOOT REPAIR from  your UBUNTU-REMIX.    (8)Do not interrupt the process.   (9)Follow the commands to re-install the GRUB.   (10)When done, boot into Ubuntu after re-boot occurs.    (11)Do the following commands after re-booting into Ubuntu:   . . ```
 sudo os-prober
```    . .```
 sudo update-grub
```       . DONE.      . PS. If Terminal reports back to say that you don't have os-prober installed,  do the following:  ```
sudo apt-get install os-prober
``` Use right away post install.     PPS. You can also do all of the above via the UBUNTU-REMIX cd is you don't want to use USB.   . . PPPS. When using the BOOT REPAIR program from your UBUNTU-REMIX, use the TAB, SPACE, and ENTER function keys to select the options that BOOT REPAIR provides for you via it's own program initiative opening up TERMINAL.

---

### Post by Ace..... on 2014-03-24
Thanks also to Hodevah.

From what I can gather (from examining the suggested links) is that 'boot-repair' is the next utility choice, in line for useful service.
I note that it is included in the ubuntu-remix, however, the primary goal is to get the PC to boot into an O/S.
It is available here: [http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)

By using this utility (without installing anything else), we do have a measure of control, or at least knowledge, of what we have done.

If it works, then we can say conclusively that it works when the Ubuntu O/S and it's partition have been deleted.
If it doesn't work, then we move forward.
Once (if, when) we have the computer booting, we can look at the best distro to be installed.

This seems like a boring method, but I've found that 'progress through elimination' does result in progress.

Thanks also for the introduction to YUMI.
At this moment in time, it is not clear to me how this fits or replaces or improves, the current multi-boot system.
Both of us have used the multi-boot as provided by Ubuntu 12.04. (which worked well until an O/S was deleted.... maybe YUMI would not have failed at this point?)

The home page of YUMI: [http://www.pendrivelinux.com/yumi-multiboot-usb-creator/](http://www.pendrivelinux.com/yumi-multiboot-usb-creator/)
states that it is for creating [I]"a Multiboot USB Flash Drive containing multiple operating systems, antivirus utilities, disc cloning, diagnostic tools, and more."
[/I]Yet your post states it also works with HDD.

Perhaps YUMI is the way forward, but it is definitely not clear to me why.

Anyway... one step at a time :)

---

### Post by Hodevah on 2014-03-24
My apologies Ace. I did not read all of your post in it's entirety. I thought that I had read that you weren't able to access Ubuntu and hence lost GRUB. As evident, you lost more than GRUB. Please disregard my post as my posted info won't be of much help to you. :)

---

### Post by oldfred on 2014-03-25
You may also be able to recover Linux partition with testdisk. 
If you have data in the Linux partition that you want to recover, you first try testdisk, then photorec which is also part of testdisk.

 repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

      
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by Ace..... on 2014-03-25
Thanks for that OldFred, that's a new utility to me, and am having a look at what they offer. :)

---

### Post by Ace..... on 2014-03-30
Success!
boot-repair-disk-64bit.iso was burned.

Watch out on boot up for a long period of blank screen (there should be something to show everything is loading correctly IMO)

Selected recommended repair.
The fix was completed in moments, with a comprehensive info file provided.
We weren't connected to the internet, so I've no url for it.

Funny story: I noted immediately that he had called his new partition:
SpaceMyDadNeverWarnedMeAb (or something like that) :D

At 15, he's at that age where he believes he 'owns me'; even in the face of stark reality :D
LOL he was sat next to me when I saw it, and I delighted in giving him a good friendly ribbing for being so cocky :D

Oh to be 15 again, with the whole world in front of you........

I think it would be wise to site Ubuntu on his newly acquired hard drive, so all eggs are not in one basket.
I'll start a new thread for that ;)

Thanks to everybody for the help :)

---

