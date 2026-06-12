---
title: "Transfer an entire installation that has multiple mounting points to a new drive."
date: 2012-10-25
forum: General Help
---

### Post by myrtle001 on 2012-10-25
Hello all,

I need to transfer my entire Ubuntu 12.04LTS installation (can't upgrade since I don't have enough disk space) to my new hard drive. What confuses and concerns me is that I have different mount points for certain files (such as /var). Perhaps this will explain:
[LIST]
[*]**Current Installation:** "/" is mounted to an approximately 11 GiB partition on my Corsair 60GB SSD, and "/usr" is mounted to an approximately 100 GiB partition on my Seagate 1TB HDD.
[*]**New Installtion:** "/" is mounted to the only partition on my new Samsung 128GB SSD, and (I believe this is right - I'm not booted up on the new installation right now) "/home" (also, note that "/home" is encrypted) is mounted to an appoximately 380 GiB partition on my Seagate 1TB HDD.
[*]**My Linux swap partition** is an appoximately 20 GiB partition on my Seagate 1TB HDD.
[*]**Window$ Installation:** Installed to an approximately 49 GiB partition on my Corsair 60GB SSD, with an appoximately 105 MiB system reserve on another partition on my Corsair 60GB SSD, and it also mounted to an approximately 500 GiB partition on my Seagate 1TB HDD.
[/LIST]

It's somewhat of a mess...

Anyway, how would I go about transferring my current installation to my new installation, without having to worry about GRUB not recognizing it or other stuff like that? I should also mention that I have a Seagate 2TB backup drive if I need to use that in the process to transfer files (though, note that I'd preferably like to keep all of my settings and preferences on all of my installed programs).

Thanks in advance!

---

### Post by LiamOS on 2012-10-25
Previously, I've tarred up my entire system and extracted it onto a correctly formatted and mounted filesystem. **This is a bit complicated**, but it may be what you're looking for. Allow me to explain:

First, tar up your system:
```
# tar cjfvp system.tar.bz2 / --exclude=/proc --exclude=/tmp --exclude=/dev --exclude=/sys --exclude=/run ... 
```(You'll need the disk space to do that; expect it to take up ~80% of the size of your entire system. Consider ignoring places like /home/user/Music if you have that already backed up. It's also worth noting that FAT32 has a max file size of ~4GB, so you can't use an external drive formatted with that.)
If you're wondering about the cjvfp options, man tar can sort you out, but the p is *very* important.

With that tar image, you can fire up a live cd of your choice, mount your / partition on, say, /mnt/ubuntu, and then do the following in the case of /var on sda3, /boot on sda1, / on sda2, /home on sda4:
```
# mkdir /mnt/ubuntu
# mount /dev/sda2 /mnt/ubuntu
# mkdir /mnt/ubuntu/boot && mkdir /mnt/ubuntu/home && mkdir /mnt/ubuntu/var
# mount /dev/sda1 /mnt/ubuntu/boot
# mount /dev/sda4 /mnt/ubuntu/home
# mount /dev/sda3 /mnt/ubuntu/var
# cp /path/to/system.tar.bz2 /mnt/ubuntu/
# cd /mnt/ubuntu
# tar xjvfp system.tar.bz2 
```
Finally, you'll need to install grub, so chroot in:
```
# mount -t proc none /mnt/ubuntu/proc
# mount -R /dev /mnt/ubuntu/dev
# mount -R /sys /mnt/ubuntu/sys
# chroot /mnt/ubuntu /bin/bash
# grub-install /dev/sda 
```Finally, you'll have to edit /etc/fstab to reflect your new system. The Ubuntu docs should have some info on this, and the Arch and Gentoo docs would be good reference too.



EDIT: Also, I doubt you'd ever need 100GB for /usr. Consider having as much of it on your SSD as you can, as this will greatly improve system performance, and /usr generally doesn't do a lot of writing on ubuntu.

Also, do not mess with the Windows partition, and don't try this method with it. Doing the first usually results in it feaking out... I should know. :(
Doing the second would just be hopeless, but I'd almost be tempted to see what exotic error messages it puts out.

---

### Post by oldfred on 2012-10-25
I always run bootinfoscript before & after any major upgrade. That way I have documented what it was and hopefully the after is what I expected.

Post the link to the BootInfo report that this creates. BootInfo runs the bootinfoscript & adds some extra useful data if you have boot issues, but worth running anyway.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If you just want script.
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils


So have you done a clean install to new SSD drive? 
Was the separate /home the same /home you had with old install?

---

### Post by myrtle001 on 2012-10-25
Sorry, I should've mentioned why I'm doing this. When I originally bought my computer (in parts, built it), I bought a 60GB SSD and a 1TB HDD. I intended to make it into a SSD/HDD combo - putting files on HDD, and programs/boot files on the SSD. However, I was somewhat ignorant to the fact that Windows wanted to use 49GB of my tiny 60GB SSD. So, with Ubuntu now cramped on it's 11GB partition (it commonly tells me something like "The filesystem "/" has only 535MB (that's random - I can't remember the exact number) remaining." and it won't let me upgrade to 12.10). So, I now bought a Samsung 830 Series 128GB SSD to expand my amount of SSD.

Though, I guess I somewhat have another question: is there a perhaps a better way to utilize and optimize both the SSD's I have and my 1TB HDD?

> **LiamOS said:**
> Previously, I've tarred up my entire system and extracted it onto a correctly formatted and mounted filesystem. **This is a bit complicated**, but it may be what you're looking for. Allow me to explain:

First, tar up your system:
```
# tar cjfvp system.tar.bz2 / --exclude=/proc --exclude=/tmp --exclude=/dev --exclude=/sys --exclude=/run ... 
```(You'll need the disk space to do that; expect it to take up ~80% of the size of your entire system. Consider ignoring places like /home/user/Music if you have that already backed up. It's also worth noting that FAT32 has a max file size of ~4GB, so you can't use an external drive formatted with that.)
If you're wondering about the cjvfp options, man tar can sort you out, but the p is *very* important.

With that tar image, you can fire up a live cd of your choice, mount your / partition on, say, /mnt/ubuntu, and then do the following in the case of /var on sda3, /boot on sda1, / on sda2, /home on sda4:
```
# mkdir /mnt/ubuntu
# mount /dev/sda2 /mnt/ubuntu
# mkdir /mnt/ubuntu/boot && mkdir /mnt/ubuntu/home && mkdir /mnt/ubuntu/var
# mount /dev/sda1 /mnt/ubuntu/boot
# mount /dev/sda4 /mnt/ubuntu/home
# mount /dev/sda3 /mnt/ubuntu/var
# cp /path/to/system.tar.bz2 /mnt/ubuntu/
# cd /mnt/ubuntu
# tar xjvfp system.tar.bz2 
```
Finally, you'll need to install grub, so chroot in:
```
# mount -t proc none /mnt/ubuntu/proc
# mount -R /dev /mnt/ubuntu/dev
# mount -R /sys /mnt/ubuntu/sys
# chroot /mnt/ubuntu /bin/bash
# grub-install /dev/sda 
```Finally, you'll have to edit /etc/fstab to reflect your new system. The Ubuntu docs should have some info on this, and the Arch and Gentoo docs would be good reference too.



EDIT: Also, I doubt you'd ever need 100GB for /usr. Consider having as much of it on your SSD as you can, as this will greatly improve system performance, and /usr generally doesn't do a lot of writing on ubuntu.

Also, do not mess with the Windows partition, and don't try this method with it. Doing the first usually results in it feaking out... I should know. :(
Doing the second would just be hopeless, but I'd almost be tempted to see what exotic error messages it puts out.

So, I won't have to worry about my different mount points for this method? It will all copy over correctly, as if it was exactly the same install and nothing changed?

Also, I'll be deleting the old install once everything is set up correctly (in other words, I won't be worrying about "/usr" anymore). On my new install (sorry if I wasn't clear on that - I already did a clean install on the Sammy SSD), "/usr" is already mounted with the rest of the "/" filesystem ("/home" is the only one with a different moint point - it mounts to my 1TB HDD). Once the old install is deleted, I'll expand the partitions on the 60GB SSD to free up some room for the cramped Windows$ 7 install.

Thanks!

---

### Post by oldfred on 2012-10-25
All the user settings are in /home. So if you have an old /home and a new /home you can copy the old data to the new system. May have been better to copy first before install as if in new install you have already changed some things, you may overwrite those.

You can use rsync or cp but parameters are important. Did you use the same username with old & new installs as ownership might be an issue if not the same.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Others that really are the same with different copy commands:
Uses cp -ax
[http://www.ibm.com/developerworks/linux/library/l-partplan/index.html](http://www.ibm.com/developerworks/linux/library/l-partplan/index.html)

If you have installed a lot of apps in the old install and want all of them in the new install. But list is long as it includes all dependencies. If old install is older, you may install the old defaults like OO when LO is now the standard. You may want to review list, it is just a text file.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

If new install is working, then there should not be any issues, but sytem settings are in /etc and if you customized any they may be in your old /etc.

---

### Post by shreepads on 2012-10-26
Honestly I would just 
- Format the new SSD (after backing up any user created data) to the 1TB Seagate
- Use Clonezilla/ Acronis etc to clone the old SSD to the new one
- Use Parted to resize partitions
- Boot with the new SSD and repair any boot errors
- Mount the partitions on the 1TB Seagate and copy over any user data backed up in step 1

You could keep /home on the new SSD but symlink the user data folders (Documents, Pictures etc) to a partition on the 1TB Seagate...

---

