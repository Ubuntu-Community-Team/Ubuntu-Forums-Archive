---
title: "Reformatting drive as UEFI and restoring data"
date: 2017-10-22
forum: General Help
---

### Post by Jesse_Evers on 2017-10-22
Hi all,

For a variety of reasons, I would like to reinstall Ubuntu to boot with UEFI rather than in Legacy Mode. I've been using this Ubuntu install for over a year, so there are lots of things set up on it that I'd much rather not have to set up again. Is it possible to copy all my data off of this install (from the root directory all the way down), reformat my drive and install Ubuntu so that it uses UEFI, and then copy the backup I made back back onto the drive in such a way that it works as it did (or almost as it did) before the reformat? 

Thank you!

---

### Post by Kris_M on 2017-10-22
be aware that you can't later install win7 on that uefi drive. btdt.

If you have to, I believe I used clonezilla to pick up the system partition, standalone gparted to change drive to uefi and create new partition (of correct size)(not smaller) for system allowing space in front of it for efi and grub partitions, and then clonezilla to restore the partition to the new one. I probably then had to use something like rescatux to make grub happy, but I forget. I also forget how/if I initialized the little efi partition - oldfred knows all about this stuff - fantastic resource!! I ran with that for a few months and it was okay, but wanted win7 on there so went back to MBR. My win7 wound up on a different SSD altogether. LOL Happy now. I boot to win7 about every 2 months and then mostly just to do the updates - end of month before next set of updates. Nice to have though.

---

### Post by Johnny3 on 2017-10-22
UEFI is for windows. I have done it. But it is a pain and does run Linus any better. If you look it says for other not for other OS than windows I don't use it. Make it much easier. Easier once you can get turn it off.
Good Luck Johnny
Ps read up on the changes MS is thing about how windows will be marketing it's software.

---

### Post by oldfred on 2017-10-22
You use gpt partitioning for UEFI, which is a newer standard than the 35 year old BIOS/MBR or legacy configuration.

If just using Ubuntu on a drive you can use gpt and boot in BIOS or UEFI boot mode, if you have correct supporting partitions.
I started using gpt back in 2010 and then when UEFI started to become the new standard formatted all drives as gpt with both a bios_grub for BIOS boot, but started adding the ESP for future use with UEFI. Then drive could be used for booting either way without major reformatting/repartitioning.

Most desktops only need /home backed up as that is all your data. If you have installed a lot of applications, you want to export a list of installed apps to make it easy to re-install. And if you manually edited any system wide configurations in /etc like I edit 40_custom and NFS with /etc/exports, so I back those up also.
It should be no different than restoring your system from a hard drive failure  from your normal backups. If you have configured any server apps like database, web or other, then those may be in various places in / (root) and need separate backup.

So just do a new UEFI full install and restore /home. 

       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)
[http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997](http://askubuntu.com/questions/40992/what-files-and-directories-can-be-excluded-from-a-backup-of-the-home-directory/40997#40997)

For lots of info & links to even more info on UEFI install, see link in my signature.

---

### Post by Jesse_Evers on 2017-10-23
If I'm using LVM, can I just add an ESP and point a couple files at it? I've extensively configured things outside my home directory, so it would take me quite a while to get back to where I am now. I don't even remember all the things I've messed with, which makes it hard to back them up.

The computer I'm using only has Ubuntu installed on it, and I'm trying to make it use UEFI so that I can follow some instructions I've found that show me how to install OS X. It's a Lenovo T450.

Thank you!

---

### Post by Geoffrey_Arndt on 2017-10-23
If your Thinkpad is robust enough . . (8 gig ram, etc.), I would leave everything AS_IS and buy a copy online of Win7 to install inside Ubuntu via Virtual Box.   Then, can have Windows if needed for those must have programs, and still have all your customizations of Ubuntu intact.   Can then stick with current BIOS config . . . Virtual Box can be run on a machine with 4 gig ram, but 8 gig will provide much better experience.

---

### Post by Jesse_Evers on 2017-10-23
I have 8 gigs of RAM, but the thing I really want to run is Lightroom, which seems like a bit of a risky proposition for running in a virtual environment.

---

### Post by oldfred on 2017-10-23
LVM does not mix with Windows well.
LVM is full drive, Windows has to be in separate NTFS partition outside the LVM.

You can add an ESP and reinstall grub changing from grub-pc to grub-efi-amd64. 
Default UEFI installs of LVM have an ESP as first partition.

If system is that configurated then you need better backup.

 Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
Best practice for Backups - theFu
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)

---

### Post by Jesse_Evers on 2017-10-24
I'm not trying to install Windows, and I don't currently have Windows. I'm only looking to install OS X in addition to Ubuntu. So with that in mind, I can simply add an ESP and reinstall grub?

My LVM install is not using UEFI, hence why there's no ESP.

I'll check out those links about backing up -- you're probably right, I need to get better about backing up my configs.

---

### Post by Kris_M on 2017-10-25
Why do you need UEFI for OS x? Oh, I see - only supported... How about putting it on it's own SSD?

I clonezilla my SSDs periodically - saved me many a time.

---

### Post by Jesse_Evers on 2017-10-25
I'd put it on its own drive but I'm doing this on a laptop -- no space for a second drive.

---

### Post by Jesse_Evers on 2017-10-28
Sorry, I still have a couple clarifying questions.

Can I create the new ESP inside LVM? And when I install the UEFI version of grub, will I have to do that after booting from a flash drive or something like that?

---

### Post by Dennis N on 2017-10-28
I can answer the first part: an LVM logical volume is not a partition, so can't be used as an EFI system parition.

---

### Post by oldfred on 2017-10-28
Just to add a bit.
The default installs using LVM have a separate ESP - efi system partition and a separate /boot partition outside the LVM.

If you install Ubuntu it will install the UEFI boot version of grub. But how it installs is dependent on how you boot install or repair media. Once you change to UEFI, you always boot install & flash drives in UEFI mode for consistency.

I have seen only one or two posts that have said /boot could be inside the LVM as grub has drivers, but that is not the normal install and you would have to do a lot of research on that method.

---

### Post by Dennis N on 2017-10-28
> I have seen only one or two posts that have said /boot could be inside the LVM as grub has drivers, but that is not the normal install and you would have to do a lot of research on that method.

Hi Fred;

I can add that in fact you don't always need a boot partition with LVM installs. On my SSD, I am using LVM whever possible, but the installer and grub must support it. Ubuntu-based OSes and Fedora-based OSes will install to LVM logical volumes without needing a boot partition;  Manjaro's installer will not (so far) install Manjaro to an LVM logical volume, but its grub will boot LVM  installations without them having a boot partition. My drive has a mix of standard partitions (for ESPs and Manjaro) and LVM for everything else.

---

### Post by Chanath on 2017-10-28
> **Jesse_Evers said:**
> Hi all,

For a variety of reasons, I would like to reinstall Ubuntu to boot with UEFI rather than in Legacy Mode. I've been using this Ubuntu install for over a year, so there are lots of things set up on it that I'd much rather not have to set up again.  

What happens, when you go to BIOS > Boot and enable Boot Mode to UEFI? As you don't have Windows installed, there must be only Grub there. You may have to pull it up, if its down under. Would your installed Ubuntu boot in your t450 in that mode?

---

### Post by oldfred on 2017-10-28
There are two versions of grub, grub-pc for BIOS and grub-efi-amd64 for the 64 bit UEFI boot.
And normally UEFI uses gpt partitioning, and BIOS uses MBR(msdos) partitioning.
Windows only boots with BIOS from MBR, and only with UEFI from gpt.
Ubuntu can boot either BIOS or UEFI from gpt if correct supporting partitions. 

Sudodus has posted instructions on installing both grub versions and having a system that can boot in either mode. 
Some sometimes updates can un-sync them, although he may have worked around that.

---

### Post by Jesse_Evers on 2017-10-29
> **Chanath said:**
> What happens, when you go to BIOS > Boot and enable Boot Mode to UEFI? As you don't have Windows installed, there must be only Grub there. You may have to pull it up, if its down under. Would your installed Ubuntu boot in your t450 in that mode?

If I force it to boot in UEFI mode, nothing happens. It hangs at boot.

I just checked, and I have a /boot partition of filesystem type ext2. I seem to remember there's a special type of filesystem for the ESP? Or maybe it's just fat32?

I checked and I have an MBR partition table, so I guess I'd have to totally redo the partitions to be able to boot with UEFI at all...so just adding an ESP in LVM wouldn't work even if it was possible, which from what people have said, is very difficult or impossible.

---

### Post by Chanath on 2017-10-31
[COLOR=#696969]> **Jesse_Evers said:**
> If I force it to boot in UEFI mode, nothing happens. It hangs at boot.

I just checked, and I have a /boot partition of filesystem type ext2. I seem to remember there's a special type of filesystem for the ESP? Or maybe it's just fat32?

I checked and I have an MBR partition table, so I guess I'd have to totally redo the partitions to be able to boot with UEFI at all...

You mentioned earlier that you'd like to keep your installation. I think you may have to reinstall all applications you have again in a new Ubuntu install. You should copy any data in your home folder to an external disk. Then go to BIOS > Boot and enable Boot Mode to UEFI. Most probably the CSM mode would be disabled, when you enable UEFI. If not, disable it manualy.

Boot the T450 with a live Ubuntu DVD/USB. It should boot in the UEFI mode, that is, you'd have a normal GRUB login screen, where you can choose. Choose the live mode. Once, Ubuntu boots up, install it in the whole hard disk. Ubiquity would create the necessary partitions. After the installation, and once you boot, you can shrink the partition and create others. They should be gpt ones.

This is how I would've done. But, you have to decide what you'd do. [/COLOR]

---

### Post by oldfred on 2017-10-31
Do not confuse the UEFI required ESP - efi system partition that is FAT32 with boot flag with a Linux /boot partition that often is ext2 but must be a Linux type partition to support ownership & permissions.

---

