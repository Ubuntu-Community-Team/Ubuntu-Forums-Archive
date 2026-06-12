---
title: "Grub reinstall - accidentally deleted partition"
date: 2018-01-29
forum: General Help
---

### Post by nix3nix on 2018-01-29
Hi! I was reinstalling xubuntu this morning (wanted to increase hd space) and all went well, untill...   I previously chunked off 7 GB of hdd space from Windows (it's a dual boot system) but then realized I wasn't able (a true beginner) to join this new space with the old 10 GB Linux partition. So I just went reinstalling Xubuntu on that same old Linux partition (I think it was hda6) and saw that there was perhaps enough space. Completed the installation, rebooted several times, all was well.   Then I made a mistake, but was truly unaware of it: in Windows, i tried to merge the 7 GB partition back with the rest of Windows - I got a warning that it was made with another system and IGNORED it, cause I was sure I did not install Linux on this new one, but on the old. (To be true, I'm not really and 100 % sure, but since it was a fresh install I don't mind installing it again).  The problem now is that the grub menu, as I knew it, is gone with this newly created and then deleted partition. I get a grub rescue screen with several possible comands listed but no menu as before (boot ubuntu, advanced ubuntu, windows, system). If I type "exit" there, then Windows 10 boots normally from there on - and for that I'm really happy since I don't have a backup and there are just too many valuable things there.  Second problem: even though I still do have a Xubuntu usb bootable drive with which I made the installation, I cannot boot with it anymore: the first thing that comes up is this grub screen. Even when I was installing Xubuntu, to boot from the usb, I had to go into system, then change the boot sequence in order to boot from usb (bios somehow NEVER saved my boot order usb>ssd ubuntu>ssd windows) but since I don't use this very often I didn't mind changing it a few times manually.  What I would like to do now is reinstall Grub (somehow) to point to the ubuntu and windows partitions again (even if I had to reinstall ubuntu one more time). What I really cannot risk is the only functional OS I have now: windows. Can it be done so that it does not pose any risks for it? In windows, I can still see the old Xubuntu partition 6, whereas new partition 7 is gone (merged with Windows)  Thank you for any help and suggestions!

---

### Post by nix3nix on 2018-01-29
Hi! I booted again to the grub screen and it's a version 2.02, just to be clear. It says: Minimal BASH-like line editing, TAB lists possible command completions.  Well, I listed all possible commands but cannot find one that seems to be appropriate to boot into bios. I further found this piece of advice: [https://ubuntuforums.org/showthread.php?t=2383753](https://ubuntuforums.org/showthread.php?t=2383753) ... that again supposes booting from a live usb or cd which I would be glad to, but cannot figure out how.

---

### Post by nix3nix on 2018-01-29
"Some procedures are already discussed by others. [There is another method I want to mention here]("https://www.quora.com/How-do-I-deal-with-Fix-Minimal-BASH-like-line-editing-is-supported-GRUB-Error-In-Linux"). This method requires no additional installation media but requires knowledge of your partition table is required.

Set grub locattion.  set prefix=(hdX,Y)/grub

Set root partition.      set root=(hdX,Y)

Set boot partition / mount point.      set boot=(hdX,Y)/boot

Set insmod.      insmod linux

Set initrd.      initrd /boot/initrd.img-X.X.XX-XX-generic

Set linux.      linux /boot/vmlinuz-X.X.XX-XX-generic 

Specify insmod.      insmod normal     normal

Finally,      boot

Note : All the instructions has to be performed according to your own drive name, path and correct filenames. Use ls command to know correct path and filenames whenever in doubt.  Now you should be able to see grub menu. Boot into linux and do a update-grub from there. That should do the trick. In the next reboot you should be able too see the Windows entry in the grub menu."

What do you think?

---

### Post by oldfred on 2018-01-29
You have UEFI install of Windows, and therefore UEFI hardware.
But did you re-install (X)Ubuntu in BIOS boot mode? UEFI and BIOS are not compatible. Once you start booting from UEFI boot menu, you cannot change boot mode. Or grub can only boot other installs in same boot mode.
Since Windows is UEFI, you want Ubuntu in UEFI boot mode.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you cannot boot live installer, you may have to recreate it. You may have written some of the installation into it, in effect corrupting it.
And be sure to boot live installer in UEFI boot mode.
       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If you have any data that is at all valuable, you must have good regular backups. Hard drives do fail, usually at least desirable time, like just before you were going to do a backup. And users, even those of us who may think we know a little make typos are wrong commands. If you have good backups then recovery is easy. If not you may have to spend weeks (I have) tying to recover data.

---

### Post by Impavidus on 2018-01-29
What happened is that you apparently deleted the partition on which grub's configuration file was stored. Grub is still there, but it doesn't know what menu to show. But this is an uefi system and that allows you to still boot Windows. That's nice.

Squeezing Xubuntu into a 10GB partition doesn't work very well, squeezing it in 7GB is even worse, but a single 17GB partition could be done, although it's still tight. But then you need 17GB of consecutive space available, so you have to move other partitions around or shrink Windows a bit more. You could also install Xubuntu on an external usb disk as a full install instead of a live system.

Which version of Xubuntu are you trying to install? And could you give some details about your hardware?

(I can make paragraphs by just hitting enter twice.)

---

### Post by nix3nix on 2018-01-29
> **oldfred said:**
> You have UEFI install of Windows, and therefore UEFI hardware.
But did you re-install (X)Ubuntu in BIOS boot mode? UEFI and BIOS are not compatible. Once you start booting from UEFI boot menu, you cannot change boot mode. Or grub can only boot other installs in same boot mode.
Since Windows is UEFI, you want Ubuntu in UEFI boot mode.

May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you cannot boot live installer, you may have to recreate it. You may have written some of the installation into it, in effect corrupting it.
And be sure to boot live installer in UEFI boot mode.
       
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
If you have any data that is at all valuable, you must have good regular backups. Hard drives do fail, usually at least desirable time, like just before you were going to do a backup. And users, even those of us who may think we know a little make typos are wrong commands. If you have good backups then recovery is easy. If not you may have to spend weeks (I have) tying to recover data.

[LEFT][COLOR=#222222][FONT=Verdana]I believe it was all UEFI, since it worked nicely before I deleted the darn thing. I made the usb key with Rufus and I remember I chose to create MBR for uefi only, not bios+uefi. The problem that I now have is that I simply cannot boot live from usb, no matter how I try. I'll take a look to BootInfo and BootRepair, but later in the evening. Thanks![/FONT][/COLOR]
[/LEFT]

---

### Post by nix3nix on 2018-01-29
> **Impavidus said:**
> What happened is that you apparently deleted the partition on which grub's configuration file was stored. Grub is still there, but it doesn't know what menu to show. But this is an uefi system and that allows you to still boot Windows. That's nice.

Squeezing Xubuntu into a 10GB partition doesn't work very well, squeezing it in 7GB is even worse, but a single 17GB partition could be done, although it's still tight. But then you need 17GB of consecutive space available, so you have to move other partitions around or srink Windows a bit more. You could also install Xubuntu on an external usb disk as a full install instead of a live system.

Which version of Xubuntu are you trying to install? And could you give some details about your hardware?

(I can make paragraphs by just hitting enter twice.)

Thanks for the info!

Originally I intended to enlarge the linux (Ubuntu 16.04 LTS) partition to 17 GB, that's the story behind all this. When I realized it cannot be done easily at least for me, a total linux newbie. So I made a fresh download of Xubuntu 17.10.1 yesterday and first installed it (I believe so) over the same partition Ubuntu was on. I booted, checked the space consumed and since it was (of the total 10 GB) still over 7 GB free space there, decided to merge the 7 GB of unallocated space back to windows partition. Wrong move!

I'm using an old asus zenbook laptop with i7 and 10 gigs of ram (no dvd-rom) and had no issues running ubuntu before. Suddenly I got a warning that I was running out of free hd space so I decided to give it a bit more... the rest you know :)

Thank you both, will report further!

---

### Post by nix3nix on 2018-01-30
Here's the progress: I found [a way to boot directly into uefi  settings ]("https://www.asus.com/us/support/FAQ/1013015/")and select my usb key as the first option to boot from. Nice! The whole thing is you shut down windows holding <shift> and then upon pressing power on, hold the <F2> button as well. Dind't now that, it seems to be related to Fast Startup.

I thought that the simplest way to restore my xubuntu and grub menu would be to simply reinstall xubuntu - after all there's nothing special on the yesterday version, no data, just a fresh install. So I went and selected the *advanced partitioning* option from the first menu (see attachements) and from there chose not to once again shrink windows partition (sda4) but to install to the previously used linux partition (sda6). OK, let's go!

What happens next? I get the following warning: "No root file system is defined. Please correct this from the partitioning menu." I believe it's still all about the missing grub configuration file?

I have now three options:
a. install xubuntu on a newly created partition ([COLOR=#222222][FONT=Verdana]still [/FONT][/COLOR]with [COLOR=#222222][FONT=Verdana]the root file problem[/FONT][/COLOR]?);
b. correct the root file system and grub (with BootInfo and Boot Repair or the one option that I found that "requires knowledge of my partition table");
c. enter windows, delete all partitions that are higher numbered than sda4 (windows) and then proceed with fresh installation of xubuntu.

But now I'll first boot into linux live usb and install BootInfo then paste info here.

---

### Post by nix3nix on 2018-01-30
Well, here it is: the [uploaded report]("http://paste.ubuntu.com/26488803/"). What do you think would be next best step to proceed? BootRepair suggests to write MBR (I installed it on the live xubuntu usb key that I booted from).

Would it not be possible just to wipe off the last two partitions (sda6 and sda7) in Windows - since I looked at the report and now see, which are Windows and which are Linux related:
/dev/sda1      R          2,048       616,448       614,401 Windows Recovery Environment (Windows)
/dev/sda2               616,449       821,249       204,801 EFI System partition
/dev/sda3               821,250     1,083,394       262,145 Microsoft Reserved Partition (Windows)
/dev/sda4             1,083,395   465,502,682   464,419,288 Data partition (Windows/Linux)
/dev/sda5      R    465,506,304   467,142,655     1,636,352 Windows Recovery Environment (Windows)
**/dev/sda6           **467,144,704   487,456,767    20,312,064 Data partition (Linux)
**/dev/sda7           **487,456,768   487,477,247        20,480 Swap partition (Linux)

...and then just reinstalling Xubuntu, creating new partitions for it?

[LEFT][COLOR=#222222][FONT=Verdana]What I'd really not like to is compromise windows in any way... Thanks for your thoughts![/FONT][/COLOR][/LEFT]

---

### Post by Impavidus on 2018-01-30
In the Installation type window, select sda6, then click Change, set the mount point to / and check the button to format. Then you can click Install Now. That will install Xubuntu in that 10GB partition. It's rather small, but should install.

---

### Post by nix3nix on 2018-01-30
> **Impavidus said:**
> In the Installation type window, select sda6, then click Change, set the mount point to / and check the button to format. Then you can click Install Now. That will install Xubuntu in that 10GB partition. It's rather small, but should install.

That's it, you did the magic trick! No need to fix MBR, windows work, linux worx... :)

Thank you for your time and effort to post and help me. Hope that maybe this info helps somebody in the same or similar case. Thanks again!

---

