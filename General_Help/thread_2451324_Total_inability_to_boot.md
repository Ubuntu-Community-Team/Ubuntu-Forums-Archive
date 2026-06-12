---
title: "Total inability to boot"
date: 2020-10-01
forum: General Help
---

### Post by OiPenguin on 2020-10-01
I did a regular system update of 20.04 and have since been unable to boot the system. I've used hours to search for solutions. I've even reinstalled (minus /home) several times, trying 20.04, 18.04 and even 20.10 release candidate. I've tried boot repair, both the manual and the automatic solution. I've altered uefi-settings and safe boot in bios. All to no avail. 

When booting I can as normal choose regular or recovery. Regular fails, regular gets stuck - I'm not able to choose any of the options (resume, clean, dpkg...). I get this error: [https://photos.app.goo.gl/YCE5jtS35VyhzqRj7](https://photos.app.goo.gl/YCE5jtS35VyhzqRj7)

My machine is a Lenovo yoga 720 which has been excellent for about two years up until today.

I'm desperate and will be grateful if someone can help me!

---

### Post by oldfred on 2020-10-01
Sometimes exit just then boots.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by GhX6GZMB on 2020-10-01
Nice to know I'm not alone:
[https://ubuntuforums.org/showthread.php?t=2451281](https://ubuntuforums.org/showthread.php?t=2451281)

Doesn't solve the problem, though.

Something's gone completely awry with the latest update.

---

### Post by OiPenguin on 2020-10-02
> **oldfred said:**
> Sometimes exit just then boots.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Thanks
[https://paste.ubuntu.com/p/rkmXHprWG3/](https://paste.ubuntu.com/p/rkmXHprWG3/)

Some additional errors:
[https://photos.app.goo.gl/8CXEeB1dR72vKCgr9]("https://photos.app.goo.gl/8CXEeB1dR72vKCgr9")

---

### Post by OiPenguin on 2020-10-02
> **ml9104 said:**
> Nice to know I'm not alone:
[https://ubuntuforums.org/showthread.php?t=2451281](https://ubuntuforums.org/showthread.php?t=2451281)

Doesn't solve the problem, though.

Something's gone completely awry with the latest update.

Yeah, it\s always nice to share a problem. Hopefully that will increase our chances of resolution as well. I suspect our problem is related to what is being reported here although it is reported as fixed, which our problems clearly are not:
[https://unix.stackexchange.com/questions/607694/ubuntu-20-04-01-not-booting-after-kernel-update](https://unix.stackexchange.com/questions/607694/ubuntu-20-04-01-not-booting-after-kernel-update)

---

### Post by oldfred on 2020-10-02
You have newer NVMe drive but have installed in both BIOS & UEFI boot mode.
You have grub in gpt's protective MBR and a bios_grub partition which are for BIOS boot.
And you have Ubuntu/grub boot files in ESP - efi system partition for UEFI boot.

With UEFI Secure Boot on, you cannot boot in BIOS/Legacy/CSM mode anyway, but need to be careful not to try. Best to make sure you only boot in UEFI mode.

You also have UEFI Secure Boot on. Have you tried booting with UEFI Secure Boot off?
Do not know if Groovy has any issues with Secure Boot. Some posted some hiccups. It is not released, yet.
I just installed Kubuntu Groovy as another install with Secure Boot off, without any issue.

You can remove old boot entries in UEFI with efibootmgr.

sudo efibootmgr -v
Delete entry change XXXX to correct entries. Some UEFI require all 4 HEX char, other just need 1 or 2 significant char.
sudo efibootmgr -b XXXX -B
Delete Ubuntu as example of delete command.
[http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743](http://ubuntuforums.org/showthread.php?t=2289179&p=13331743#post13331743)

---

### Post by OiPenguin on 2020-10-03
Thanks, however I found this very complicated.

I've tried booting both with and without UEFI Secure Boot on.

I tried to remove some old boot entries with efibootmgr, but don't know which I shall remove. I suppose removing all will make it impossible to boot at all, even from an USB-key?

---

### Post by oldfred on 2020-10-03
First fix issue, then you can houseclean UEFI boot entries. 

Not sure if you need a full fsck or a full reinstall of grub & new kernel so it updates initramfs.

Can you boot recovery mode, second entry in grub menu.
If only Ubuntu you have to press escape key right after UEFI/BIOS screen to get grub menu.
If you have UEFI fast boot on, you do not have time to press a key and need to do a "cold" boot or full power down. And press correct keys as you then boot from a cold system.

From recovery mode, you can have all partitions unmounted & run fsck or do other repairs.
Or you can use live installer to run fsck.
And with Boot-Repair's advanced mode do a full reinstall of grub & latest kernel.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

to see UEFI boot entries as shown in Boot-Repair
sudo efibootmgr -v
You want to remove old Linpus Lite entries which were shown as default? But probably no others.
Did you install Linpus lite & then remove it?

---

### Post by OiPenguin on 2020-10-03
> **oldfred said:**
> First fix issue, then you can houseclean UEFI boot entries. 

Not sure if you need a full fsck or a full reinstall of grub & new kernel so it updates initramfs.

Can you boot recovery mode, second entry in grub menu.
If only Ubuntu you have to press escape key right after UEFI/BIOS screen to get grub menu.
If you have UEFI fast boot on, you do not have time to press a key and need to do a "cold" boot or full power down. And press correct keys as you then boot from a cold system.

From recovery mode, you can have all partitions unmounted & run fsck or do other repairs.
Or you can use live installer to run fsck.
And with Boot-Repair's advanced mode do a full reinstall of grub & latest kernel.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

No, I'm unable to boot into recovery. I do get the choice, I also get the recovery menu, but I'm unable to choose any of the options. It freezes and the terminal shows in the background.

sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required, Run both commands as they have different parameters.
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

to see UEFI boot entries as shown in Boot-Repair
sudo efibootmgr -v

> **oldfred said:**
> 
You want to remove old Linpus Lite entries which were shown as default? But probably no others.
Did you install Linpus lite & then remove it?

The whole machine is utter mess. I've never installed Linpus and I don't know what it is. I wiped Win 10 when the machine was new and installed Ubuntu so I don't know why it still is in the boot menu.

My current attempt at a solution is to mount with a live session, rsync my old /home (now mounted as /mnt/lars is the live session, to my server. I use the command *rsync -a /mnt/lars USER@server-ip:/home/USER/*, however I get errors such as these, *rsync: [sender] opendir "/mnt/lars/.gnome" failed: Permission denied (13)*, probably due to right issues. I'm tempted to change ownership of the mounted directory, but I'm afraid that will cause further problems. 

At the moment any solution for backup to server is my preferred solution. Once I've preserved a backup I'm free to do anything with the machine without any risk. My first attempt will be a total wipe and reinstall after creating a new partion table. Suggestions are welcomed :-)

---

### Post by OiPenguin on 2020-10-03
Problem solved, however not in the most eloquent fashion. My finale solution was to copy /home/ to an external disk and perform a total wipe follow by a clean install. Note to self: remember frequent backups!

---

### Post by GhX6GZMB on 2020-10-03
> **OiPenguin said:**
> Problem solved, however not in the most eloquent fashion. My finale solution was to copy /home/ to an external disk and perform a total wipe follow by a clean install. Note to self: remember frequent backups!

Not nice.

This means a complete reinstall of all applications plus system/program configurations. Been there, done that. The latest upgrade really is a killer.

---

