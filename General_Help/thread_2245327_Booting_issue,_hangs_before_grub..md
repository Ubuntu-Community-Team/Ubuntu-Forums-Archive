---
title: "Booting issue, hangs before grub."
date: 2014-09-22
forum: General Help
---

### Post by Spud37 on 2014-09-22
9.721120] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[    9.721381] ata7.00: BMDMA stat 0x25
[    9.721523] ata7.00: cmd a0/01:00:00:20:00/00:00:00:00:00/a0 tag 16 dma 16416 in
[    9.721523]              res d1/f0:d3:d0:f0:d00/00:00:00:00:00/f0 Emask 0x2 (HSM violation) 
[    9.722068] ata7.00: status: { Busy }

It then hangs. 

EDITED

Okay so not completly new, just never had an issue where i needed help and googling didn't do me any good. Alright my questions come in two different flavors, one I would like to make a portable ubuntu by that I mean install ubuntu onto a portable hard drive and take it with me, so i can boot up using the external usb on different computers. Different from a live install USB. I googled and wasn't able to find anything that could help or answer my question with that. I would like to re-partition my 2TB portable hard drive into one section for ubuntu and the other an NTFS for the personal data so that I can access it on other computers easily. 

Second problem perhaps more serious is that I am trying to install ubuntu onto my desktop computer but after installing from a live USB it gives me 

"
Verifying DMI Pool Data .........
error: attempt to read or write outside of disk 'hd0'.
Entering rescue mode...
grub rescue>
"

I have tried to reboot from the Live USB again but it stills brings this up. I thought the installation had gone down fine but then this came up.


I have used ubuntu off and on for awhile but this is something i couldn't find an answer for.
Thanks.

---

### Post by grahammechanical on 2014-09-22
See the section Install and run USB Creator. Note you will have use the slider to set the amount of persistent storage space.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Edit the thread title to a more appropriate one and I may consider offering advice on the other problems. But at the moment all my good will have been used up.

---

### Post by Spud37 on 2014-09-22
I am not sure how to change the thread title. Isn't that just makeing a liveUSB, instead of a full ubuntu installation with an option to install onto the computer?

---

### Post by oldfred on 2014-09-22
A full install to any external or second drive is just another install. But you must use Something Else which requires you to manually partition. I do prefer to use gparted to create partitions in advance, but you still use Something Else to mount which partition is / (root), /home, and swap. It usually finds swap if it exists. And only with Something Else can you choose which drive to install grub2's boot loader into. Default is always sda with auto installs and even default in Something Else. You normally want to change to sdb or external drive if not sdb.

Is system UEFI or BIOS?

Several examples of Something Else installs:
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Spud37 on 2014-09-23
thanks oldfred. Now I have 

[    9.721120] ata7.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[    9.721381] ata7.00: BMDMA stat 0x25
[    9.721523] ata7.00: cmd a0/01:00:00:20:00/00:00:00:00:00/a0 tag 16 dma 16416 in
[    9.721523]              res d1/f0:d3:d0:f0:d00/00:00:00:00:00/f0 Emask 0x2 (HSM violation) 
[    9.722068] ata7.00: status: { Busy }



When I boot, and then it hangs.

---

### Post by oldfred on 2014-09-23
I think it is BIOS that releases a drive from frozen.

 Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
sudo lshw -class disk
udisks --dump

What setting do you have drive in BIOS, AHCI? But not IDE nor RAID.

May be best to see all details:
      Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by vasa1 on 2014-09-23
> **Spud37 said:**
> I am not sure how to change the thread title. ...
You can edit your own posts, so click the **edit** button just below the first post (yours) and then click on "**advanced**" which will appear below the post body. Then you should be able to click in the title box above the post body and make whatever changes you want to the title to make it more descriptive of the issue you want help with. Then click "save" below the post body. Note that this will affect only the title in the first post but that is enough to let people know what your question is about.

The second point is that it is preferable to address one issue per thread as that will be helpful to others who have the same interest. Here, you have two distinct issues in the same post.

A third point is that this forum shows viewers the first few lines of the first post in the thread when the mouse pointer is over the thread title. If those lines describe or point to what the issue is, that helps people know immediately whether they can help you or not without needing to open the thread itself.

---

### Post by Spud37 on 2014-09-25
> **vasa1 said:**
> You can edit your own posts, so click the **edit** button just below the first post (yours) and then click on "**advanced**" which will appear below the post body. Then you should be able to click in the title box above the post body and make whatever changes you want to the title to make it more descriptive of the issue you want help with. Then click "save" below the post body. Note that this will affect only the title in the first post but that is enough to let people know what your question is about.

The second point is that it is preferable to address one issue per thread as that will be helpful to others who have the same interest. Here, you have two distinct issues in the same post.

A third point is that this forum shows viewers the first few lines of the first post in the thread when the mouse pointer is over the thread title. If those lines describe or point to what the issue is, that helps people know immediately whether they can help you or not without needing to open the thread itself.

Thanks


> **oldfred said:**
> I think it is BIOS that releases a drive from frozen.

 Hard drive info - will show locked frozen status or not:
sudo hdparm -I /dev/sdd
sudo lshw -class disk
udisks --dump

What setting do you have drive in BIOS, AHCI? But not IDE nor RAID.

May be best to see all details:
      Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://paste.ubuntu.com/8428784/](http://paste.ubuntu.com/8428784/)

using the boot repair disk it seemed to let me be able to boot to ubuntu that I have installed. Thanks

---

### Post by Spud37 on 2014-09-25
It seems to be working now, not sure why, or what I may have done to fix it, but just running the boot repair for info and nothing more seems to have fixed it. 

Thanks, if you know why its working let me know. Just in case it does happen again in the future

---

