---
title: "Repaired Win7 and now cannot load GRUB and UBUNTU..."
date: 2014-11-01
forum: General Help
---

### Post by bik-npl77 on 2014-11-01
&#8203;Hello,

I had dual boot in my system with Ubuntu and Windows 7. Few weeks ago my windows crashed, it was unable to boot and I had access to Ubuntu only...I posted about in Win7 forums here: [http://www.sevenforums.com/general-discussion/349755-dual-boot-win7-boot-manager-status-0xc000000f-boot-selection-failed.html ]("http://www.sevenforums.com/general-discussion/349755-dual-boot-win7-boot-manager-status-0xc000000f-boot-selection-failed.html(There's") and got the problem solved and now I can run Win7 as before but the GRUB menu no longer loads while booting and I can't run Ubuntu...I ran "boot-repair" and  it gave me this error:

```
 The sda3 (Ubuntu 14.04.1 LTS) partition is nearly full. This can prevent to start it. Please use the file browser that just opened to delete unused files (or transfer them to another disk). Close this window when you have finished.
```
I clicked ok and it began to "Purge and reinstall the GRUB of sda3(upd)" and after that it showed this:
```
 Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 14.04.1 LTS (sda3). Then try again. 
``` But I can't access Ubuntu, so how do I do that!!?? 

_**The boot info summary gave this link: paste.ubuntu.com/8773221**_

I really love Ubuntu and want to use it again like before...so any help would be much appreciated. Thanks in advance!! :)

---

### Post by kc1di on 2014-11-01
Down load a copy of[ boot-repair ]("https://help.ubuntu.com/community/Boot-Repair")from here burn it to cd and run it. should find ubuntu and win 7 and reistall grub in mbr for you. 

Or you can also reinstall Grub from Ubuntu Live disk but it's a little more complicated.[ Instructions here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

### Post by bik-npl77 on 2014-11-01
That is the same link from where I downloaded Boot-repair previously and after I run that during boot then I encountered all those errors and messages that I posted earlier!!!!!

---

### Post by Bucky Ball on 2014-11-01
This message:

```
The sda3 (Ubuntu 14.04.1 LTS) partition is nearly full. This can prevent to start it. Please use the file browser that just opened to delete unused files (or transfer them to another disk). Close this window when you have finished.
```

... suggeset /dev/sda3, your 14.04 partition, is full. Is it? The next message:

```
Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 14.04.1 LTS (sda3). Then try again.
```

... suggests you have some repositories switched off or not installed in 14.04. Have you recently installed 14.04? Tweaked the Software Sources?

First things first, perhaps, from a live boot, launch Gparted and take a screenshot of sda. We can see clearly what's going on. Attach it to a post here using 'Adv Reply'>paperclip icon.

PS: We can get to the software sources.list via a live boot from USB and enable/disable repos, but lets check the disk full error first. ;)

---

### Post by oldfred on 2014-11-01
Clicky link to your boot summary report:
[http://paste.ubuntu.com/8773221/](http://paste.ubuntu.com/8773221/)

this says your partition is almost full.
 /dev/sda3      ext4       6.2G  5.7G  193M  97% /mnt/boot-sav/sda3

Boot-Repair saves its own backups and copy of the summary report and that uses some space. Is system if full then it does not have room to work. And system probably wants to download new updates along with a grub reinstall and that requires space.

Not sure what this issue is, but it may just be the lack of space.

 Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty-updates_universe_i18n_Translation-en
It looks like Boot-Repair makes a copy of the sources list, and tries to read that. But if no space then it may not write the file and then errors occur?

 Warning: unknown mime-type for "/mnt/boot-sav/sda3/etc/apt/sources.list" -- using "application/octet-stream"

You have a very large swap of 17GB and your / (root) is only 13GB. While 13GB should be enough if you do not save much data into /home and do regular house cleaning, you could make / a bit bigger. Unless hibernating which normally is not recommended, you only need 2 or 3GB for swap, especially if you have over 4GB of RAM.

---

### Post by bik-npl77 on 2014-11-01
> **Bucky Ball said:**
> This message:

```
The sda3 (Ubuntu 14.04.1 LTS) partition is nearly full. This can prevent to start it. Please use the file browser that just opened to delete unused files (or transfer them to another disk). Close this window when you have finished.
```

... suggeset /dev/sda3, your 14.04 partition, is full. Is it? The next message:

```
Please enable a repository containing the [grub2] packages in the software sources of Ubuntu 14.04.1 LTS (sda3). Then try again.
```

... suggests you have some repositories switched off or not installed in 14.04. Have you recently installed 14.04? Tweaked the Software Sources?

First things first, perhaps, from a live boot, launch Gparted and take a screenshot of sda. We can see clearly what's going on. Attach it to a post here using 'Adv Reply'>paperclip icon.

PS: We can get to the software sources.list via a live boot from USB and enable/disable repos, but lets check the disk full error first. ;)

I couldnot take a screenshot from "boot-repair" cd...showed error with "scrot" i tried to install scrot but was unable to do so...even "apt-get update" showed error...so **I've attached old screenshots of sda** that I had on the Win7 forum. However, unlike in the screenshot, currently when viewed in GParted there's no error sign next to sda3 as that's for Windows and that's running efficiently but there's that sign next to sda2 and the information on sda2 is same as that seen on the screenshot....so basically the information on the screenshot is not correct for sda3 and correct for others...because this "boot-repair" that I'm currently running (which is showing Lubuntu btw) cannot take screenshots!!

---

### Post by oldfred on 2014-11-01
If you encrypted /home, then it is normal that gparted does not see swap as swap is also encrypted.

And system will boot even if swap not working, but just with error messages.

You also have a red icon on your Windows. Is it hibernated or needs chkdsk?
If Windows 8 it always is hibernated unless you specifically turn off fast boot.

---

### Post by Bucky Ball on 2014-11-01
Yep, your sda4 Ubuntu partition is full. I'd jump into Windows and shrink that hog. You've only given Ubuntu 6 and a bit Gb! Give it 15 or 20. 

Take note: if it is not XP, DON"T shrink the Windows partition using Gparted. That will probably screw things. ALWAYS use the software in Win for resizing partitions in 7 and up. Good luck.

---

### Post by bik-npl77 on 2014-11-01
> **oldfred said:**
> If you encrypted /home, then it is normal that gparted does not see swap as swap is also encrypted.

And system will boot even if swap not working, but just with error messages.

You also have a red icon on your Windows. Is it hibernated or needs chkdsk?
If Windows 8 it always is hibernated unless you specifically turn off fast boot.

Please read my last post carefully...there's the red icon on my Windows 7 because it is not the current screenshot of sda that can be seen on GParted , it is old screenshot but it basically looks like that currently except for the sda3 i.e. Windows partition. There's that error on sda2 only which I'm pretty sure I used for Ubuntu partition.

[COLOR=#000000]> You have a very large swap of 17GB and your / (root) is only 13GB. While 13GB should be enough if you do not save much data into /home and do regular house cleaning, you could make / a bit bigger. Unless hibernating which normally is not recommended, you only need 2 or 3GB for swap, especially if you have over 4GB of RAM.

So can I change the swap and / spaces for Ubuntu (sda2) from Windows and if I can will it fix the problem?? [/COLOR]

---

### Post by bik-npl77 on 2014-11-01
> **Bucky Ball said:**
> Yep, your sda4 Ubuntu partition is full. I'd jump into Windows and shrink that hog. You've only given Ubuntu 6 and a bit Gb! Give it 15 or 20. 

Take note: if it is not XP, DON"T shrink the Windows partition using Gparted. That will probably screw things. ALWAYS use the software in Win for resizing partitions in 7 and up. Good luck.

Shrink!? Shouldn't I expand..to make more space as it is full? And how about sda2 error? Will it be fixed after that?

---

### Post by Bucky Ball on 2014-11-01
Boot into Windows> shrink sda4;
Boot from live Ubuntu media (disk, USB)> Try Ubuntu> when at desktop launch Gparted> expand sda3;
Close Gparted>hit 'Install Ubuntu' icon> see if it works.

---

### Post by bik-npl77 on 2014-11-01
> **Bucky Ball said:**
> Boot into Windows> shrink sda4;
Boot from live Ubuntu media (disk, USB)> Try Ubuntu> when at desktop launch Gparted> expand sda3;
Close Gparted>hit 'Install Ubuntu' icon> see if it works.

Cannot shrink sda4...I used "Minitool partition magic" and cannot drag the triangles to shrink sda4...cannot enter values too. However, there was no problem with shrinking sda3 i.e my C: where Win7 is installed...
Also, I only have one pendrive where I've mounted the "boot-repair"...if I install ubuntu live then I'd have to delete "boot-repair"...would I be needing "boot-repair" any longer?

---

### Post by Bucky Ball on 2014-11-01
If you've shrunk the Win partition successfully then follow the instruction I gave. Boot to a live desktop and launch Gparted. Expand the Ubuntu partition. Don't use third-party stuff. No need.

You can install Boot Repair in a live desktop with the code I gave in the last post so effectively no, you don't need it. You have the ISO somewhere anyway I imagine.

---

### Post by bik-npl77 on 2014-11-01
> **Bucky Ball said:**
> Boot into Windows> shrink sda4;
Boot from live Ubuntu media (disk, USB)> Try Ubuntu> when at desktop launch Gparted> expand sda3;
Close Gparted>hit 'Install Ubuntu' icon> see if it works.

hahaha you had me confused with sda3 and sda4....here above you meant to shrink sda3 (i.e. Win partition) and expand sda4 (i.e. Ubuntu partition [see screenshot]) and merge later to make the Ubuntu partition bigger...right??

---

### Post by westie457 on 2014-11-01
> Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1               2,048       206,847       204,800  de Dell Utility
/dev/sda2             206,848    17,614,847    17,408,000  82 Linux swap / Solaris
/dev/sda3          17,614,848    30,926,847    13,312,000  83 Linux
/dev/sda4    *     30,926,848 1,250,263,727 1,219,336,880   7 NTFS / exFAT / HPFS

Looking at the partition table above you cannot expand /sda3 in either direction without risking severe damage to either OS.
Cannot remember if the Windows partitioning tools will allow the start point of the partition to be moved on the fly - while booted into Windows (sda4).
Shrinking /sda2 and then resizing sda3 (using Gparted in a Live boot) will move the start point and change the UUID. System will fail to boot.

It might be possible shrink one and expand the other Ubuntu partitions using the 'Something Else' option in the installer and choosing to leave the format option unchecked.
This is something I have never tried so cannot reliably say it will work. Back up your data first before trying any partition work.

---

### Post by bik-npl77 on 2014-11-01
Yep, it doesn't seem to be able to shrink Win7 partition i.e. C: too using Minitool or Disk Management...Screenshot:

It doesn't allow shrinking sda1 i.e. Dellutility partition either...

---

### Post by westie457 on 2014-11-01
Looks like the Windows hiberfil.sys is blocking the operation. Give this a try.

Windows key > type in cmd > right-click - run as administrator.

Type in powercfg -h off


The hiberfil.sys will be deleted to allow adjustment of the partition. To re-enable again run powercfg -h on.

Edit.
Once the partition has been shrunk (the easy bit) you will then have to move the whole thing to the right (the risky bit). This operation will change the UUID for Windows and consequently might not boot first time. If at first boot after the resize chkdsk should kick in to reset the UUID for the Windows boot-loader. Have a Windows recovery CD or Installation DVD handy just in case you have to force repair the system.

---

### Post by bik-npl77 on 2014-11-01
> **westie457 said:**
> Looks like the Windows hiberfil.sys is blocking the operation. Give this a try.

Windows key > type in cmd > right-click - run as administrator.

Type in powercfg -h off


The hiberfil.sys will be deleted to allow adjustment of the partition. To re-enable again run powercfg -h on.

thanks for the reply westie but it still shows the same problem...

---

### Post by oldfred on 2014-11-01
You only show 24% free in Windows.
The Windows NTFS partition really needs 30% free to run well. And at 10% free it becomes very slow and defrag is about impossible as there is no working room. So you really do not have any free space unless you have a lot to houseclean out in the NTFS partition.

---

### Post by bik-npl77 on 2014-11-03
> **oldfred said:**
> You only show 24% free in Windows.
The Windows NTFS partition really needs 30% free to run well. And at 10% free it becomes very slow and defrag is about impossible as there is no working room. So you really do not have any free space unless you have a lot to houseclean out in the NTFS partition.

All right...I've freed up the space in Windows...what should be the next step to recover Ubuntu??

---

### Post by oldfred on 2014-11-03
First do you have good backups. Any partition changes can create issues that cannot be recovered from.
Do you have repair CD or flash drive for the current version of each system.
A Windows repairCD or flash drive.
An Ubuntu live DVD or flash drive.

My suggestion depending on how much space you have and where it is. 
I do not like moving the start of Windows. That almost always leads to major issues. Chkdsk at the minimum but it may have bigger issues. And since Windows repair do not always see Linux partitions, they often forget to include that when rewriting partition table. Data is still there and it can be recovered but another issue to resolve.

I would delete swap, move Linux partition all the way left and then expand it right. And create a new small 2 or 3GB swap after the Windows partition. 
If you shrank Windows a lot, I would make the space after the Windows partition an extended partition and use part for data and part for swap as logical partitions inside the extended.

You should be able to boot Linux, moving should not change UUID and it may be boot without additional repairs. It will give an error message as the old swap does not exist, but should still boot. Then you have to manually edit fstab with new UUID from new swap. If you need help with that once you boot we can provide that help.

Basically use Windows tools for Windows and Linux tools for Linux. Or only use Windows own disk tools to shrink Windows and use gparted to delete swap, move Linux partition and create new swap.

---

