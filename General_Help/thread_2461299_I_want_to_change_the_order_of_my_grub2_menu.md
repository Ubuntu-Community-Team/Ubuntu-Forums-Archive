---
title: "I want to change the order of my grub2 menu"
date: 2021-04-28
forum: General Help
---

### Post by t5404tmz on 2021-04-28
I've tried 6 different methods from various posts and none of them worked.

In the /etc/default/grub file I've changed the GRUB_DEFAULT= value from "saved" to "6" to 6 without the quotes.  I run the update-grub command after the change but when I reboot, the menu is the same and the cursor is always at the top.

Please help.

Here is the whole /etc/default/grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=6
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_SAVEDEFAULT="true"
```

---

### Post by tea for one on 2021-04-28
Grub2 is not the easiest application to configure but you could try this:-

```
GRUB_TIMEOUT_STYLE=menu
```

```
sudo update-grub
```

---

### Post by oldfred on 2021-04-28
Is it in the sub-menu or the menu. 
Some just use the description as the default, but it must be exact, so copy from your default grub menu entry.
[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

Some also copy 40_custom to 06_custom and then copy entire boot stanza for entry you want as first. Scripts are processed in number order so 06_ will be first entry. You can also turn off os-prober, if desired when manually editing you added boot stanzas.
When you are finished putting all of your custom boot entries in your /etc/grub.d/06_custom file, it needs to be chmodded to make it executable,
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo cp -a /etc/grub.d/40_custom /etc/grub.d/06_custom
sudoedit /etc/grub.d/06_custom
sudo chmod 755 /etc/grub.d/06_custom
or
sudo chmod a+x /etc/grub.d/06_custom
sudo update-grub
 
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by coley9225 on 2021-04-28
I use Lubuntu 20.04 with the qt desktop. I use grub custmizer to configure my grub menu. Besides being able to change the order the entries appear in the grub menu, use can rename the entries, if you need to. I have lubuntu, which shows in menu as ubuntu, but also have ubuntu on my computer, so hard to know which is which unless I renamed  mine to lubuntu. I have used grub cusimizer in linux mint and lubuntu 18.04( with lxde desktop), and it works very well on all. Good luck.

---

### Post by ajgreeny on 2021-04-28
I suggest that you avoid grub-customiser as it makes changes to the complete grub configuration system making it much more difficult to get answers from this forum, and I know some users have found that it creates many more problems than it solves.

If you do decide to use it, I wish you well and hope it does what you want, but be aware that it may not be as simple to get away from it should you need to.

---

### Post by t5404tmz on 2021-04-28
I have an interesting observation and that is that when I change just the GRUB_TIMEOUT value in my /etc/default/grub, that doesn't work either. After the change I execute update-grub and that runs successfully.  Am I in the wrong file?

---

### Post by ajgreeny on 2021-04-28
If you have more than a single Linux OS installed are you sure you are dealing with the correct OS's grub?
Normally the OS with active grub will be the most recently installed Linux.

---

### Post by t5404tmz on 2021-04-28
I don't know very much about this.  How do I know if I am dealing with the correct OS?  Is there more than one /etc/default folder?

---

### Post by ActionParsnip on 2021-04-28
Do you dual boot and want Windows to be the default option? Is this the aim here?

---

### Post by t5404tmz on 2021-04-28
No, I have two ubuntus and the most recent (20.04) is at the bottom of the list.  I realize that I'm just trying to save a few down arrows, but I'm also learning in the process.

---

### Post by t5404tmz on 2021-04-28
It's possible that my grub is corrupted.  In my ignorance, I booted into a puppy linux because I remembered that I could use its grub config tool to rearrange the order of the menu.  I'm pretty sure that I used a grub version 1 in the puppy and my original grub was version 2.  Immediately after my changes, my ubuntu 20.04 wouldn't even load.  I recovered from my problem with boot-repair.  So I'm not sure what state my grub2 is in, but it seems pretty clear that the /etc/default/grub file is not being used in the update-grub process, because my changes to the GRUB_TIMEOUT don't even show up.  

Is there any way to start over with a clean slate?  Remove all the grub residue and start from scratch?

I realize I did some stupid things, and I'm fortunate to be able to even boot anything at all!

---

### Post by oldfred on 2021-04-28
A full reinstall of grub will reset everything to defaults.

Many use Boot-Repair, chroot into a non-working system, or boot manually or with something like Supergrub to get into system and then do a full reinstall of grub. Not the update which just updates the menu.

If an UEFI install you have to have ESP mounted. If old BIOS install you have / mounted & if /boot separate partition have it mounted. 
Exact commands vary depending on which way you are repairing system.

Best not to create confusion with grub legacy which was grub until about 10 years ago. When grub2 came out, old grub was renamed to grub legacy.
But packages in repository still have old names. Grub legacy is grub, grub2 is grub-pc for BIOS, or grub-efi-amd64 for UEFI (or others for systems that are not standard PCs).

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by t5404tmz on 2021-04-28
Here is the pastebin link.  

[https://paste.ubuntu.com/p/p4vZN3ZtZ6/](https://paste.ubuntu.com/p/p4vZN3ZtZ6/)

---

### Post by oldfred on 2021-04-29
Two issues I see immediately.
You installed grub to Windows PBR/BS or partition boot sector. Windows has essential boot info in that BS and now even Windows repairs will not work on sda2 as it sees it as RAW or unformatted. Boot-Repair sees a grub2 installed in BS and since grub in a BS can be correct it does not flag it. NTFS does have a backup BS and you normally can restore it unless you installed grub multiple times to the BS.

```
sda1: ____________________________________

    File system:       [COLOR=#ff0000]ntfs[/COLOR]
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Boot file info:      [COLOR=#ff0000]Grub2[/COLOR] (v1.97-1.98) in the file /sda_mbr.bak looks at 
                       sector 1 of the same hard drive for core.img. core.img 
                       is at this location and looks for 
                       fa1c08ed88ed08ec0fbdf0us in partition 97.
    Operating System:  
    Boot files:        /menu.lst /grldr /bootmgr /Boot/BCD /grldr


```

[http://www.ntfs.com/fat-partition-sector.htm](http://www.ntfs.com/fat-partition-sector.htm)
PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot 

And you show 16.04 which expires April 2021. Or is now expired.
And that is the install grub is trying to boot into.

It looks like you installed grub into sda7, better to just install it into the MBR.
Grub2 does not recommend installing into the PBR/BS. But you forced it into the BS to use grub4dos. It makes for a less reliable system.

---

### Post by t5404tmz on 2021-04-29
I was able to install testdisk and backup the BS without any problem.  When I try to boot the Windows partition it goes into Startup Repair and then fails.  I don't really care about Windows.  I'm hoping that if I ever really need it on that machine I can do a factory reset, which is accessible in the Windows Startup Repair sequence.  

> Also check for /boot/grub in addition to /Boot 

And you show 16.04 which expires April 2021. Or is now expired.
And that is the install grub is trying to boot into.

It looks like you installed grub into sda7, better to just install it into the MBR.
Grub2 does not recommend installing into the PBR/BS. But you forced it  into the BS to use grub4dos. It makes for a less reliable system.


I'm not sure how to also check for /boot/grub in addition to /Boot.  Is that something I do in testdisk?

As far as 16.04 expiring... I'm not sure what I need to do about that.

And how do I clean up the grub in sda7?  Is there a procedure to uninstall grub and reinstall it into the MBR?

Thanks for your help!  I thought for a minute I was going to see my long lost Windows boot up, but to be honest, I really don't miss it at all.

---

### Post by grahammechanical on 2021-04-29
Let us imagine that these two Ubuntu are on the same disk. The only disk. Load 20.04 and run

```
sudo update-grub
sudo grub-install /dev/sda
```

If you have more than one hard drive and Ubuntu 20.04 is on the second hard drive (sdb). Load 20.04 and run this

```
sudo update-grub
sudo grub-install /dev/sdb
```

Whenever you get a kernel upgrade in the non-ubuntu 20.04 then run update-grub again from 20.04 so that the new kernel appears in the Grub menu. Whenever you get a Grub upgrade in the non-ubuntu 20.04 then run grub-install from 20.04. Remember to use /dev/sda or /dev/sdb to point the install of the 20.04 grub to the right hard drive.

Regards

---

### Post by t5404tmz on 2021-04-29
> **grahammechanical said:**
> Let us imagine that these two Ubuntu are on the same disk. The only disk. _**Load 20.04 and run**_

```
sudo update-grub
sudo grub-install /dev/sda
```



Forgive my ignorance, but when you say to "load 20.04 and run" does that mean that I need to reinstall from scratch?  If I load 20.04 to the same partition, does it give me an option to keep my apps and files?

Thanks!

---

### Post by yancek on 2021-04-29
>  No, I have two ubuntus and the most recent (20.04) is at the bottom of the list.

The distribution which is installed to the MBR will put itself at the top of the Grub menu so the above quote would indicate that you're booting from 16.04 on sda5.  This is confirmed in the boot repair output (lines 5-7).  I notice also that you apparently incorrectly installed some Grub files to the windows partition as pointed out above.  You also have a menu.lst and a grldr file which would indicate you had Grub4dos installed.

I think what was meant by the suggestion to 'load' 20.04 was to boot it and run those commands.  If you can't boot 2.04 from Grub you can't do that.  You should be able to reinstall and not lose programs or data files if you select to NOT format the partition(s) during the install.  If you can boot 20.04, the commands above will be a lot simpler.

---

### Post by t5404tmz on 2021-04-29
> **yancek said:**
> The distribution which is installed to the MBR will put itself at the top of the Grub menu so the above quote would indicate that you're booting from 16.04 on sda5.  This is confirmed in the boot repair output (lines 5-7).  I notice also that you apparently incorrectly installed some Grub files to the windows partition as pointed out above.  You also have a menu.lst and a grldr file which would indicate you had Grub4dos installed.

I think what was meant by the suggestion to 'load' 20.04 was to boot it and run those commands.  If you can't boot 2.04 from Grub you can't do that.  You should be able to reinstall and not lose programs or data files if you select to NOT format the partition(s) during the install.  If you can boot 20.04, the commands above will be a lot simpler.

Sorry for being so dense.  Here is what I get:
```

master@master-Latitude-E6440:~$ sudo update-grub
sudo: update-grub: command not found
```

---

### Post by oldfred on 2021-04-29
With BIOS install, you can just mount / (root)  and then reinstall grub. 
Many prefer Boot-Repair, but it usually defaults to first install. You need to select advanced mode and then choose install & chose drive (MBR) to install grub into.
That grub is in PBR of ext4 partition will not matter. It just never will be used.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

You also can do full chroot.
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by t5404tmz on 2021-04-29
Ok, so the grub install command was not found so I went into advanced mode boot-repair and told it to install grub on my sda7 (20.04) partition.  Now it boots to a grub prompt.  I'm guessing that restoring my sda7 partition with clonezilla isn't going to help me.  Right now I can only boot from USB drive.  The pastebin url is [https://paste.ubuntu.com/p/CJcFVzMsxg/](https://paste.ubuntu.com/p/CJcFVzMsxg/)

---

### Post by t5404tmz on 2021-04-30
I was able to recover my grub2 menu by doing the following:

1. Boot using usb
2. Executed the following commands:
```


sudo mount /dev/sda5 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

sudo chroot /mnt

grub-install /dev/sda
```

(then I umounted everything that I mounted)

I tried using sda7 but it didn't bring back my grub2 menu.  I'm pretty sure I am back at square one.  Here is the pastebin url for my current state:

[https://paste.ubuntu.com/p/t4scsws6Zr/](https://paste.ubuntu.com/p/t4scsws6Zr/)

When I ran the boot-repair in advanced mode, it seemed like exactly what I wanted.  On the Grub Location tab, sda7 was the default and grub would be placed into sda.  In a perfect world, that would have changed the default so when the menu loaded and I hit enter the sda7 partition (20.04) would load.  But this is not a perfect world, and grub is scary stuff.  I'm close to just putting away these dangerous tools and living with a few down arrows from the grub menu.  But then again, maybe I've weathered the storm and with the new data you guys can save me from those down arrows.   :)

---

### Post by yancek on 2021-04-30
I'm not sure why your sudo update-grub command failed.  You could try running:  sudo grub-mkconfig -o /boot/grub/grub.cfg instead because that's all the update-grub script does.

In your last post, you indicate you run the chroot commands on sda5 and that you had done the same on sda7 and it failed, is that correct?
So where are you now in terms of booting?  Can you boot either 16.04 or 20.04 and if so which menu are you using, 16.04 or 20.04.

Your latest boot repair script indicates you are booted into sda7 (line 108).

If you simply wanted the 20.04 instance of Ubuntu to be the default boot when you were booting from 16.04, you could change that in the /etc/default/grub file of 16.04 by changing the line below in that file:

>  GRUB_DEFAULT=0 

You would change the zero (0) to the correct number for the 20.04 entry, counting from zero and run sudo update-grub or sudo gruc-mkconfig.

---

### Post by oldfred on 2021-04-30
Your boot into sda7 will be slow as you are mounting sdb1 which does not exist.
It will search for that UUID and keep searching until it times out.

Your Windows also shows errors, it may just need chkdsk from a Windows repair disk.

---

### Post by t5404tmz on 2021-04-30
Here is an update of my status.  For some reason, I ran the update-grub command from my sda7 load, just to see if it was working after my chroot change in sda5.  And it was working.  I think it was a bad thing to do though, because after that I would get a grub menu at boot, but the sda5 partition (16.04) would fail to load.  In addition to that, when I booted the sda7 (20.04) partition from the grub menu (after doing the dreaded down arrows), the boot experience was different.  It took much longer to boot and it was a different series of messages flashing across the screen.  But 20.04 would at least load and it was operational.

So in my supreme ignorance, I thought I could do the chroot thing again from my 20.04 load.  it all worked, but it made no difference, because 16.04 still failed to boot from the menu.  It tried, but had some errors and just hung.

So then I decided to do another boot-repair from the sda7/20.04 load I was in.  That had disastrous results which would not even load a grub menu.

So I booted from the usb and did the chroot thing again into sda5.  That restored my menu, but sda5/16.04 still had errors and would not load from the menu.  And sda7/20.04 stilll has the changed boot experience, taking longer and different messages flashing across the screen.

Then to make everything a little worse, I was running boot-repair while I was writing this post so that I could get a current pastebin, and somehow I fat-fingered something and it did another boot-repair.  I'm pretty sure that this is going to leave me with a grub prompt when I boot.

Here is the pastebin for the current state:  [https://paste.ubuntu.com/p/HHQkCsbSwp/](https://paste.ubuntu.com/p/HHQkCsbSwp/)

I'm guessing that the grub menu is pointing to different kernels which is producing the different boot experience.  

If this is true, how can I restore the old pointers so I can get back to square one with 16.04 being the default and both sda5/16.04 and sda7/20.04 loading without crashing?

---

### Post by t5404tmz on 2021-04-30
Here is my flawed thinking which created this mess:

I was under the impression that my hard drive, sda, had only one root directory.  The / folder, I thought was common to all of the partitions which were installed on the sda device, and all of the system folders for the installed partitions were in the /media folder somewhere.

I now think I understand that each partition has its own / folder, so there are multiple /etc/default/grub files.  I thought there was only one and that regardless of which system I loaded I was always updating the only /etc/default/grub file.  

I think I understand that part now.  I could have saved myself all of this trouble by just updating the sda5/16.04 /etc/default/grub file to change the default.  This was recently pointed out in one of the replies.

But I didn't do that and I got tangled up in my shorts, and I've made a bit of a mess now since I can't even load my sda5/16.04 partition.

The good news is that I think I understand the grub system a little better.  

The bad news is that I don't understand the grub system enough to know what changed in the kernel pointers (if that is the correct terminology) when I updated grub in my sda7 load, because that is when the booting world changed.  In other words, that is when sda5/16.04 crashes when started from the grub menu, and that is when sda7/20.04 has the different messages flashing across the screen and takes much longer to boot.

Here is a question for you:  If I restored my sda5/16.04 partition using clonezilla, and then did an update-grub from a chroot session into sda5, would it restore my old grub and point to the old kernels?

My assumption is that only doing a restore of the partition will not change the grub.  But when I restore the old grub configuration files (by restoring an old backup) and then do an update-grub, I'm thinking that maybe my grub menu will be pointing at the kernels they were pointing at when I did my backup.  Which would take me back to square one, which requires a simple change in the sda5/16.04 /etc/default/grub file to change the default to load sda7/20.04, which would save me from having to hit the down arrow key.

I guess the first question is whether my assumption that grub is loading different kernels, thus leading to the different boot experience, is a sound assumption.

Thanks for all of your help!

---

### Post by t5404tmz on 2021-04-30
So the good news is that I was able to go into the advanced options in the grub menu and load my sda5/16.04 partition.  And once I was in the 16.04 system I was able to update my grub with the correct default pointing to the 5th entry on the menu.  All of that works now and I don't have to hit the down arrow key anymore.

The problem I have is that my sda7/20.04 loads with a different kernel than before and it is slower, and the advanced options grub menu doesn't have any alternative kernels to boot my 20.04 system. 

  I issued the following command to list all of the kernels I have:

```

master@master-Latitude-E6440:~$ dpkg --list | grep linux-image
rc  linux-image-5.4.0-42-generic                  5.4.0-42.46                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-52-generic                  5.4.0-52.57                          amd64        Signed kernel image generic
rc  linux-image-5.4.0-53-generic                  5.4.0-53.59                          amd64        Signed kernel image generic
rc  linux-image-5.8.0-43-generic                  5.8.0-43.49~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-44-generic                  5.8.0-44.50~20.04.1                  amd64        Signed kernel image generic
rc  linux-image-5.8.0-45-generic                  5.8.0-45.51~20.04.1+1                amd64        Signed kernel image generic
ii  linux-image-5.8.0-48-generic                  5.8.0-48.54~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.8.0-49-generic                  5.8.0-49.55~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-5.8.0-50-generic                  5.8.0-50.56~20.04.1                  amd64        Signed kernel image generic
ii  linux-image-generic-hwe-20.04                 5.8.0.50.56~20.04.34                 amd64        Generic Linux kernel image
master@master-Latitude-E6440:~$ uname -r
5.8.0-50-generic
master@master-Latitude-E6440:~$ 


```

I am booted in the sda7/20.04 load.  The current kernel for that 20.04 load is 5.8.0-50-generic according to the uname -r command.  

Am I correct in assuming that linux-image-5.8 prefixed kernels will load 20.04 and linux-image-5.4 prefixed kernels will load 16.04?

If that is true, then how can I access the other kernels for 20.04 from my grub menu?  In the advanced options menu there are only kernels listed for 16.04.  If my assumption is correct, i.e. that 5.8 prefixed kernels will load 20.04, then there must be a way to include all of the 5.8 prefixed kernels in the advanced menu.

How do I load kernels that are not listed on the grub menus?

---

### Post by oldfred on 2021-04-30
No.
Did you not see post #24, that is why your boot is slow.

Each / (root) will  have multiple kernels, some older and perhaps even newer versions if an upgrade or you have enablement stack working.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Grub will boot into either / if found & working. But only default kernel will be booting, unless you select another in the menu.
And you should only have 2 kernels now. But older version like 16.04 required you to manually houseclean. The reason for 2, is only if newer kernel does not work for some odd reason, you could still boot older working version.

---

### Post by t5404tmz on 2021-04-30
> **oldfred said:**
> No.
Did you not see post #24, that is why your boot is slow.

Each / (root) will  have multiple kernels, some older and perhaps even newer versions if an upgrade or you have enablement stack working.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Grub will boot into either / if found & working. But only default kernel will be booting, unless you select another in the menu.
And you should only have 2 kernels now. But older version like 16.04 required you to manually houseclean. The reason for 2, is only if newer kernel does not work for some odd reason, you could still boot older working version.

I deleted the sdb1 entry in etc/fstab, so that shouldn't be a problem anymore.

Right now my grub is controlled by my sda5 partition.  I have to boot into sda5 to make any modifications to my grub menu.  How can I switch that control over to sda7?

---

### Post by oldfred on 2021-05-01
Boot into sdb7 and do a grub install from there.
This is only for reinstalling grub from a working install, which puts grub into MBR of sda drive and is for BIOS boot system.
sudo grub-install /dev/sda

If you cannot boot into install, you have to mount partition first, chroot, or use Boot-Repair's advanced mode.
And if UEFI, you have to mount ESP - efi system partition, even if chroot.

---

### Post by t5404tmz on 2021-05-01
> **oldfred said:**
> Boot into sdb7 and do a grub install from there.
This is only for reinstalling grub from a working install, which puts grub into MBR of sda drive and is for BIOS boot system.
sudo grub-install /dev/sda


I uninstalled grub from sda7 and then did a re-install.  After reboot I just get a grub prompt... no menu.  So I chroot back into sda5 from a usb session and do a grub-install to /dev/sda from there.  So far, this procedure will always restore my grub menu when I reboot.

Here is the pastebin file:  [https://paste.ubuntu.com/p/CX5zFzkzDB/](https://paste.ubuntu.com/p/CX5zFzkzDB/)

Question about pastebin...  Is it better to delete the old logs when prompted?  I always say "NO."  

My new problem is:  What do I need to do on sda7 to have the grub config built from that partition and have it present me with a grub menu at boot?

Another related question is:  How can I add optional kernels in the advanced options for sda7?  Right now there are 15 iterations of the same entry:

Ubuntu 20.04.02 LTS (20.04) (on /dev/sda7)

Should I close this ticket and open a new one since my original problem is solved?

Thanks for all of your help.

---

### Post by oldfred on 2021-05-01
Somehow your grub on sda5 keeps adding entries for install on sda7. Not sure why. Grub2's os-prober should be only adding it once.

Also not sure why a grub install from your sda7, does not then boot, something not correct with install in sda7.

With boot repair you can in advanced mode, choose your install in sda7 and drive sda. But also choose to install new kernel and full reinstall of grub.
The auto fix will not install new kernel & update system, just reinstall grub.

---

### Post by t5404tmz on 2021-05-01
I'm running boot-repair right now with the option to purge and then reinstall the last kernel plus a full reinstall of grub.  I'm installing it to sda7 and sda as directed.  Also, I running the boot-repair from an sda7 load.

The boot-repair has been running for several minutes with the following message on the screen:

[B]Purge kernels then reinstall last kernel sda7 (pur) This may require several 
minutes...

[/B]It has shown this message before in various steps of the process, but the wait is usually only a few seconds.  How long should it take to purge and reinstall a kernel?

Can it do this function if I am booted into sda7 and it is processing sda7 kernels?

I don't want to interrupt the program unless I have to.

---

### Post by t5404tmz on 2021-05-01
So I interrupted the boot-repair after about an hour of waiting for it to purge and reinstall the sda7 kernels and things are not good.

Here is the pastebin from immediately after that interruption:  [URL="https://paste.ubuntu.com/p/8Tx9Z4yzMR/"]https://paste.ubuntu.com/p/8Tx9Z4yzMR/
[/URL] 
(This was taken from an sda7 load, but now I have to run on sda5.)

I get a grub menu, but when I boot sda7/20.04 it will give me my desktop, but there is no wireless and it doesn't give me an option to turn it on.  Also the customizations I made are there, but the sizes are wrong for my xfce panels.

On sda7 there is no /etc/default/grub file, so I'm guessing that sda5 still has control of grub.

Please help me restore my wifi and my old sda7 desktop.  I haven't lost any data, but I haven't used my sda5 load for awhile and all my current data is in the sda7 partition.  I can mount the data, but I would prefer to get my wireless back on sda7.

---

### Post by oldfred on 2021-05-01
Boot-Repair has to have Internet to download grub & kernel, so that is why it failed.

Can you connect to a wired Ethernet connection?
Then it could download driver if that is the issue.

I do not know Wireless issues. There is a entire sub-forum and a script you need to run that documents your configuration.
Post hardware details. See sticky post at top for details on script.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

If you have wireless in sda5, do not know why newer install would not work.

And you really need to have backups on another drive.

---

### Post by t5404tmz on 2021-05-02
I've had a catastrophic failure probably related to a failed restore of my sda7 partition using clonezilla.  The good news is that the problem I had with my grub is moot.  The bad news is that my entire sda7 partition got wiped out somehow.

I've opened a new ticket to get help recovering it if at all possible.  I'll close this ticket.

I was trying to restore an sda7 image and then I planned to update grub from sda5.  My thought was that my backup would include whatever kernels got trashed by the boot-repair.  Now I'll never know.

---

