---
title: "How can I re-order partitions?"
date: 2015-12-06
forum: General Help
---

### Post by tho.tran1809 on 2015-12-06
Hi guys,

Below attachment is my GParted:
[ATTACH=CONFIG]265992[/ATTACH]


/dev/sda3 and /dev/sda5 are 2 Windows partitions.
/dev/sda6 is /root and /dev/sda7 is /home

Now I don't wanna use Windows any more, so I wanna delete both sda3 and sda5, to extend both sda6, sda7 and sda9. When I boot with Live CD, if I delete sda3 and sda5, /root and /home became sda5 and sda6, which is different. So I'm wondering is there any problem with that? If yes, how can I delete and re-order my partitions without loosing any data?

Thanks a lot!

---

### Post by grahammechanical on 2015-12-06
Terms such as sda4 and sda5 are just labels. Grub & Linux are actually using Globally Unique Identifiers (GUID) to distinguish hard drives and partitions. That is true in your case because the motherboard is using GPT partitioning. I have MBR partitioning and so my partitions have a Universally Unique Identifier. (UUID). In both cases these identifiers are a long string of alpha-numeric characters.

Here is an example from my grub.cfg file. It identifies the first partition on the first hard disk. Other wise known as sdb1

UUID=2b5ca5d3-03b7-4771-9c6a-ebd0b2fcae0d

So, removing those windows partitions will change the sda labels but not the GUID identifier string. But remember. to open/mount the Ubuntu partition & run 

```
update-grub
```

after you have finished with partitioning and before you close the live session, That will clear up the grub boot menu. You can find grub.cfg so as to study it at /boot/grub/grub.cfg.

Regards.

---

### Post by yancek on 2015-12-06
You have an Extended partition (sda4) in which the partitions sda5 and higher are contained.  If you delete sdaa5 the partition sda6 will change to sda5.  Although Grub uses UUIDs, it also has a set root entry for the specific partition(s) so changing this will create problems booting.  Although it is possible to do things the way you want it is more complicated and when moving partitions there is always a possibility of data loss so make sure you have backups.  It would probably be simpler to format the two partitions with a Linux filesystem and create mount points for them.

---

### Post by Bucky Ball on 2015-12-06
In a live session:

- Delete 3 and 5 (do you need the Win recovery partition sda2?); 
- Expand sda4 into the new uallocated space;
Resize other partitions as required.

You'll see in Gparted the /dev/sda* now set on the partitions when you've finished. Note them down as you may need to reboot and edit the /etc/fstab file so they are mounted in the correct places. After a reboot, first the command given previously:

```
sudo update-grub
```

PS: The deleting and resizing may take some time.

---

### Post by oldfred on 2015-12-06
If you have an extended partition, you do not have the newer gpt partitioning, but the older MBR(msdos) partitioning.

I see you already have a data partition. You can just delete the NTFS partitions and create new data partitions formatted ext4. That will erase all data currently on them.
If you want a larger data partition and since the NTFS logical partition is first in extended partition you can delete it with gparted & move start of extended partition. Then you can make one larger partition.

Are you sure you do not want Windows? Many delete Windows and later find that one application or game that only works or works well in Windows and want it back. It took me years before I finally gave up on Windows. Best to fully back it up just in case, you want it back later. 
 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by furtom on 2015-12-06
Since you don't want windows anymore, I'd strongly recomment a reistilation if this is at all possible. I'd probably go that route if I were in your position.

You have your /home on a seperate partition, so this should be fairly painless.

You just choose "something else" in the installer and delete all your old partitions except /home and whaterer else you want to keep. Then you can creat your root partition and move and resize those partitions. It will be a nice clean install with all your mount points having logical names.

If you don't want to reinstall, I know how I'd do it:

Boot to a live DVD/USB and use gparted to delete and resize. 

After that, (while still in the live Ubuntu environment), I'd remmend the Boot Repair utility as the easiest solution. Run the following commands in a terminal to install Boot Repair. (I never understood why this wasn't included on the image!)
 
```
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```

Using Boot Repair to fix grub is fairly self-explanitary and should work. If it doesn't, post back.

Anyway, these methods should work without a bunch of manual configuration. Fee free to ignore if you want to delve into /etc/fstab and grub! :)

---

### Post by tho.tran1809 on 2015-12-06
Thanks guys a lot for your information.

I booted with LiveCD, partitioning, update grub, restart and everything is just fine :)

---

### Post by Bucky Ball on 2015-12-06
Excellent news! :)

Please see the first link in my signature and good luck.

---

