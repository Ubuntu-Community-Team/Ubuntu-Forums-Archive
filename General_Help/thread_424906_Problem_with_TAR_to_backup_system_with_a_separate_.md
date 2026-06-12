---
title: "Problem with TAR to backup system with a separate /home"
date: 2007-04-27
forum: General Help
---

### Post by kilou on 2007-04-27
Hi,

I'm using Feisty and wanted to use a separate home partition to keep my settings for future clean installs. Previously when I was using home on the root partition I was backing up the system using this TAR command and everything was fine (backup AND restore):

sudo tar -cvpzf backup.tgz --one-file-system $exclude_list /

with exclude_list="
		--exclude=/lost+found/* 
		--exclude=/tmp/* 
		--exclude=/var/tmp/* 
		--exclude=/var/log/*
		--exclude=/var/cache/apt/archives/*.*
		--exclude=/home/user/.Trash/* 
		--exclude=/home/user/.thumbnails/*
		--exclude=/root/.Trash/*
		--exclude=/root/.thumbnails/* "	

Now that /home is on a separate partition I had to change the TAR command. I decided to **create one backup file for root and another separate backup file for /home**. The backup file for root filesystem is:

sudo tar -cvpzf backup_root.tgz --one-file-system $exclude_root /

with exclude_root="
		--exclude=/lost+found/* 
		--exclude=/tmp/* 
		--exclude=/var/tmp/* 
		--exclude=/var/log/* 
		--exclude=/var/cache/apt/archives/*.* 
		--exclude=/root/.Trash/* 
		--exclude=/root/.thumbnails/* "

Since /home is on another filesystem this backup effectively doesn't include it since I use the option --one-file-system.

I then did some tests, format the root partition (untouching /home that was on a separate partition and working, I didn't delete it!) and then booting from the LiveCD I restored the root file system from the above TAR command. Everything appears to work correctly when untarring but when I reboot the system hangs on the Ubuntu boot image (the bar that represent boot process stay at the beginning. I tried several times and always get the same results. I also tried to remove the --one-file-system option in the TAR command and add --exclude=/home/* to the exclude_root list (see above) but always get the same results: the system is able to boot with Grub, load the Ubuntu boot image but the boot process stops. 

I also tried to launch Ubuntu in recovery mode to see where it hangs and the boot stops after loading USB drivers.

Do you know what Iam doing wrong? It seems that it's impossible to backup and restore a root partition if home is on another partition (untouched)....

Any advice would be appreciated. I'd like to solve this problem before going with a proper install of Feisty and tune all parameters. Thanks!

PS: I'm restoring from a LiveCD with:

                #Mount root partition
		mkdir /mnt/restored_root
		mount /dev/sda1 /mnt/restored_root

		#Restore root system
		tar xvpfz backup_root.tgz -C /mnt/restored_root

---

### Post by Skrynesaver on 2007-04-27
Perhaps try with a --preserve-premissions, just a thought off the top of my head ;)

---

### Post by kilou on 2007-04-27
Thanks for the reply. Basically this is what I'm doing with the -p option in the tar -cvpzf command so it doesn't appear to be the issue. I've always used tar -cvpzf and permissions were always restored correctly.

---

### Post by kilou on 2007-04-27
I also tried to make a clean install of Ubuntu and then extract the backup archive on top of it without formatting the root partition but I produced exactly the same problem when rebooting: system hangs at Ubuntu boot screen and progress bar is stuck at the beginning. I can't understand why simply putting /home on a separate partition doesn't allow me to backup root and restore it correctly :(

---

### Post by kilou on 2007-04-28
....and the root filesystem is backed up to/restored from an EXT3 partition (external USB drive) so the permission are stored.

---

