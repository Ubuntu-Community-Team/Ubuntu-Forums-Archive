---
title: "NFTS partions missing - Windows won't boot"
date: 2007-09-01
forum: General Help
---

### Post by simonsocial on 2007-09-01
When booting my system this morning the Windows XP boot option was missing from GRUB. When in Ubuntu the NTFS partions where missing and I can get them to mount.

So far I have added the Windows XP boot option into GRUB, but when I try to load Windows I get an error saying the HAL.dll file is missing and need reinstalling... i've not looked into this problem totally yet but looks like it could be a reinstall.

My probelm is that I need to get my Outlook email file off the NTFS partion before I look into reinstalling Windows.

When I try to mount in my case /dev/sda1 I get the following: -

[COLOR="Red"]Windows is hibernated, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume Windows and turned it 
off properly, so mounting could be done safely.[/COLOR]

So I decided to run [COLOR="Blue"]ntfsfix /dev/dsa1[/COLOR], but I get the following error: -

[COLOR="Red"]Mounting volume... FAILED
Attempting to correct errors... 
Processing $MFT and $MFTMirr...
Reading $MFT... OK
Reading $MFTMirr... OK
Comparing $MFTMirr to $MFT... OK
Processing of $MFT and $MFTMirr completed successfully.
Setting required flags on partition... OK
Going to empty the journal ($LogFile)... OK
Remount failed : No such file or directory
simon@simon-laptop:~$ sudo mount /dev/sda1[/COLOR]


Can anyone help me?

---

### Post by ddrichardson on 2007-09-01
When you boot windows can you get to the recovery console (press F8 during boot). The hal.dll problem is very common and can sometimes be rectified. It's usually to do with boot.ini becoming corrupted. If you can get into the recovery console I'll post more.

---

### Post by dulbirakan on 2007-09-01
I don`t want to be the prophet of evil but could it be some physical failure in your HD? Is it listed in your BIOS? Is S.M.A.R.T. Enabled?

Any ways, try UBCD or UBCD4win for recovery.

Best of luck....

---

### Post by simonsocial on 2007-09-01
Ok... I've got the XP recover console on a bootable CD, which i've tried but it says that it can't find a harddrive. Thats as far as I can get.

My harddrive is working because Ubuntu is installed on it and thats what i'm using at the moment.

I've booted up with the Ubuntu Live CD and it can mount the drives as normal. How come the Live CD can do it but the installed version not??

---

### Post by ddrichardson on 2007-09-01
If the live cd can mount it then recover your files an backup before anything else. As for why the Live CD works and the installed Ubuntu doesn't I can only imagine its related to some configuration on your setup.

---

### Post by simonsocial on 2007-09-02
I've manged to get everything working... some how! I don't really know what I did but I will list what I did anyway...

I used the following guide [http://lifehacker.com/software/disk-recovery/geek-to-live--rescue-files-with-a-boot-cd-192982.php](http://lifehacker.com/software/disk-recovery/geek-to-live--rescue-files-with-a-boot-cd-192982.php) to get a Live CD which had Read and Write on NTFS built into it. So I boot up that and put a copy of my Outlook file on a USB pen. I then restarted my computer and I could boot into Windows. Dunno what happen but something work.

Thanks for all your advice.

---

