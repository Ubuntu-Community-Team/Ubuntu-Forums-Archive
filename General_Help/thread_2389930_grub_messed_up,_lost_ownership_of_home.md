---
title: "grub messed up, lost ownership of /home"
date: 2018-04-23
forum: General Help
---

### Post by lemmy18 on 2018-04-23
i was running ubuntu with the system on sda (750GB HDD) and /home on sdb (1TB HDD). it was 14.04 upgraded from 12.04 using the GNOME DE.
18.04 is about to release, and i wanted to back up /home in preparation.
i tried installing a package and the installation wiped out gnome, chromium, skype, vlc, handbrake, and at least one other program which i can't remember the name of.
before rebooting the system, i reinstalled GNOME (sudu apt-get install) and the rest of the removed software.
i also ran sudo apt-get -f install and autoremove which took out a bunch of older versions of linux kernel.
when everything looked back to normal, i rebooted.
/dev/mapper/cryptoswap1 not ready. this has happened a number of times, but it usually fixes itself after a few seconds. this time it didn't right itself so after 3 mins i pressed S to skip mounting.
this caused some kind of loop (the monitor kept resetting and the picture remained blank), so i hit the reset button on the box.
GRUB came up missing. i don't know how to repair GRUB, so i inserted the 12.04 installer disk, planning to use the browser in the "try without installing" mode.
i use the dvorak keyboard layout, and the LiveCD would only load qwerty layout, so i couldn't type to use the search engine.
installed 12.04.1 alongside 12.04.3 (14.04 didn't seem to be present), and found how to repair GRUB. problem is, i couldn't get the GRUB error to repeat so i had no place to type the set set insmod and normal lines.
also, couldn't enter 12.04.3, the cryptswap1 error persisted and would not fix itself.
installed 16.04 alongside 12.01 and 12.04.3, now i can at least open /brian in terminal and ls shows 2 files, even though properties of the drive show nearly 1TB of content.

i don't remember if i encrypted /home or not, but i have had  trouble with encrypted drives in the past and lost files due to not  having the correct encryption key, so i'm pretty sure i do NOT have  /home encrypted.
is there ANY way to access my true home folder using chown or tricking GRUB to a repair prompt or any other method?
can i AT LEAST copy the contents to my external drive?
the path shown in terminal when i open /brian (my home folder) in terminal: /media/lemmy/6c1e4cbf-eb59-4bd2-a7a7-bf528907deb5/brian
the path shown in terminal when i open a random folder in my external drive/media/lemmy/My Passport/foo

---

### Post by oldfred on 2018-04-23
Best to always have a current version live installer to use as repair disk for every operating system you have installed. 
And then best to run Boot-Repair with that current version.

 May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by lemmy18 on 2018-04-23
is this what you asking for?
[https://paste.ubuntu.com/p/vwdTD8kMqP/](https://paste.ubuntu.com/p/vwdTD8kMqP/)

---

### Post by oldfred on 2018-04-23
Have you tried the recommended repair?
It looks like it will reinstall grub from sda14, or your newest version.

Your older installs had other system folders as partitions. Better now to have everything in / (root) with possible exception being /home as a separate partition.

Your install in sda1, uses an encryption /home from sdb1. I assume it is encrypted since you have encrypted swap which was only used with encrypted /home.
The fstab's in other installs did not mount or when you installed, you did not reuse the /home partition on sdb1.

Boot-Repair probably cannot auto fix your grub from sda1, since you have all the system partitions. It knows to look for separate /boot, but does not find other system partitions. If you want to attempt to boot your old 12.04 which became obsolete a year ago, you would have to chroot into it. And repositories are closed so no new updates. It does not show you updated to 14.04 as your sda5 /boot has all 3.2 version kernels (and some older) from 12.04.

---

### Post by lemmy18 on 2018-04-24
i really do appreciate you taking the time to help. hopefully i can mark this solved after you answer one last question...

where abouts is the recommended repair? is it in the report? honestly i  don't understand that report enough to know what i'm looking at until  someone says "start with line ___". at least the report has the lines  numbered.

i'm less interested in repairing 12.04 since i will be installing  18.04 later this week. i'm more interested in regaining ownership of  12.04 /home so i can copy it all to an external drive before installing  18.04. that said, if i have to repair to gain ownership, i'll do it,


again, thank you for being patient with me. (the external drive is a recent acquisition and i will be much more vigilant about backing everything up with this new installation)

---

### Post by yancek on 2018-04-24
The recommended repair is always at the end of the output, in your case lines 3156/3157 which just reinstalls Grub.  You already have  Grub from that partition (sda14) installed so I'm not sure how much good that will do.  You have proper entries for 16.04 and you also have entries for 12.04 in the grub.cfg of 16.04.  One thing is having the boot files almost at the end of the drive, can often cause problems.  What exactly can you do/boot now?

There should be no problem booting other than 12.04 to mount and access your /home partition on sdb1 to copy to another drive.  What have you tried?

---

### Post by oldfred on 2018-04-24
Can you boot now?

Because your 12.04 shows encrypted swap, when you installed you must have encrypted /home.
But you should be able to mount it from other installs if you have the encryption key.

 Encrypted /home links with more info. I have never used an encrypted /home.
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)
[https://help.ubuntu.com/community/EncryptedHome](https://help.ubuntu.com/community/EncryptedHome)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering_Your_Mount_Passphrase)
remove encryption on /home
[http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/](http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/)

---

### Post by lemmy18 on 2018-04-24
thank you, yancek. the only things i've tried so far are listed in post #1 of this thread. there is almost a full 1TB on sdb1 /home that i do not know how to access. i can open sdb1 /home in terminal, but from there i don't know what to do. CLI is far from being my strength, and i barely know what i'm doing in GUI.
the path shown in terminal when i open sdb1 /home/brian in  terminal: /media/lemmy/6c1e4cbf-eb59-4bd2-a7a7-bf528907deb5/brian
the path shown in terminal when i open a random folder in my external drive: /media/lemmy/My Passport/foo
if this was WinXP i'd be home by now.

---

### Post by lemmy18 on 2018-04-24
oldfred, i haven't tried anything yet. not sure yet what this boot repair utility is; i'll have to try and google about it and hope i understand what i read.
as for the key, i can look through my old notes to see if i have a key, or if i even used encryption... (i learned long ago to take meticulous notes on such things, the problem is my filing non-system)

---

### Post by oldfred on 2018-04-24
Can you actually see files in the folders?
If so then not encrypted and just permission & ownership issue?

Is this a partition you want to permanently mount via fstab, or just manually mount once.
You have to create a mount point and mount it manually or fstab and then give yourself owership & permission.

Unmount if already mounted via Naulitus to /media/$USER/..... default mount by UUID.
       sudo mkdir /mnt/data
sudo mount /dev/sdb1 /mnt/data
sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

I typically label all partitions, so those I only occasionally mount are mounted by label not UUID, so I know which is which.

---

### Post by lemmy18 on 2018-04-24
unfortunately, no, i can't see folders or files aside from 2 very small files, and when i try to open them i get an error "This link cannot be used because its target doesn't exist." i'm still looking for my installation notes from 6 yrs ago. just went through a mountain of disks... plenty of software and windows rescue disks, no ubuntu rescues yet.

---

### Post by lemmy18 on 2018-04-24
after 6 yrs and abt a dozen times moving, i have lost things along the way. no encryption key to be found and i have looked through literally every disk and piece of paper including the file box with the bank statements. it appears the only way i'm going to get into /home is to mount it from the installation of ubuntu that it belongs to.

GRUB is present and functioning after i installed 16.04 alongside 12.04.3

booting 12.04.3 gives the following error:
13.377200 SP5100 TCO timer mmio address 0xb8fe00 already in use
/dev/mapper/cryptswap1 not ready or not present.
Wait, S to skip mounting, M to manually repair.

waiting does nothing, S does nothing, and M does nothing.

reboot, arrow to 12.04.3 advanced and ckdsk (or is it fdsk? i forget) and i get a lot of scrolling. it appears that every partition of every device has a superblock where the last write time is in the future by less than a day probably due to an incorrectly set hardware clock. it says FIXED after all of those, then the scrolling stops. flashing cursor, no prompt. i can type but idk what to type or if it's even supposed to stop there.

---

### Post by oldfred on 2018-04-24
Its fsck.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

You can comment out the swap entry in fstab just to avoid that error.
But 12.04 is not maintained anymore so very difficult to fix.
And if /home encrypted you still have to have passphrase to boot, it is not automatic. Only if not encrypted will it then mount.

---

### Post by lemmy18 on 2018-04-24
wait, you say passphrase... do you mean my user login passphrase or the encryption key? because passphrase i have, i just can't get to the login bc it stalls at the splash. (yeah, i googled the error, it seems to have something to do with this machine having ATI graphics)

---

### Post by oldfred on 2018-04-24
You need the encryption passphrase. And should not have to boot the original 12.04 install but be able to mount from any install or live installer as long as you know the passphrase. You may have to install the encryption drivers.

But there is no recovery from encrypted partitions otherwise, that is why really good backups of any encrypted data is required.

---

### Post by lemmy18 on 2018-04-25
> **oldfred said:**
> You need the encryption passphrase. And should not have to boot the original 12.04 install but be able to mount from any install or live installer as long as you know the passphrase. You may have to install the encryption drivers.

But there is no recovery from encrypted partitions otherwise, that is why really good backups of any encrypted data is required.

ENCRYPTION PASSPHRASE NOT NEEDED

going to mark this thread solved.
the solution in my case was to load the 12.04.1 that i installed beside my original 12.04.3, and open terminal.
sudo apt-get update
sudo apt-get install ecryptfs-utils
[FONT=arial]
use the GUI to mount the drive with the encrypted files, then back in terminal run
[/FONT]
sudo-ecryptfs-recover-private
[FONT=arial]
it asked if i know my LOGIN password, enter Y
enter LOGIN password at prompt, which in my case looks like ******** not the ******************************** encryption key
data became accessible as read-only in the 12.04.1 tmp folder
copy to external drive
files are unencrypted upon writing to external drive and can be accessed and written from any system.

as i had nearly a whole TB of data to move it took 15 hours, during which time i was unable to enter the 16.04 installation where i had this thread bookmarked. it only just now finished.

next step is to find my firefox bookmarks and copy that file (another thread), then wipe the entire system and start over (bionic beaver final release tomorrow!!!)

thank you everyone for your input.[/FONT]

---

