---
title: "help required in resizing drive-dual boot"
date: 2018-09-23
forum: General Help
---

### Post by kevinorourke2008 on 2018-09-23
Hi Guys, could somebody guide me through how to resize my hard drive so that Ubuntu has more space please. I have a 750 gig hard drive which is split between windows 10 and ubuntu 18.04.01 lts. I have 250 gig for ubuntu and what i see as a waste of space for windows but I need to keep windows for work so i cant simply get rid of windows and dedicate the whole drive to ubuntu. I would like to make the Ubuntu partition 500 gig so that I've a bit of wriggle room on my drive. Could anybody point me in the direction of any previous posts about this or indeed guide me.  Many thanks in advance. Kev.

---

### Post by RobGoss on 2018-09-23
Hello, I would try resizing your hard using Windows **Disk Management** tool, this way you could just give that **unallocated** space to Ubuntu and expand the Ubuntu's partition. Sorry I don't use Windows any more so I can't take a closer look for you.

Also make sure you make a **complete backup** before you attempt this that way you don't loose any data. This link might help you understand how to accomplish this

How to resize Windows partition
[https://www.youtube.com/watch?v=tJiakVgAtn4](https://www.youtube.com/watch?v=tJiakVgAtn4)

---

### Post by Impavidus on 2018-09-23
Use a Windows tool to shrink the Windows partition and create unallocated space, reboot Windows a couple of times to allow it run all its disk checks, then boot a Linux live disk and use gparted to resize the Ubuntu partition. The unallocated space coming off the Windows partition must be adjacent to the Ubuntu partition, or it won't work. If you Ubuntu uses LVM/encryption, it gets a more complex.

Using a single, large partition for Ubuntu isn't really recommended. Most people here suggest to make a smaller (15–30 GB) partition for the system and a larger one for data or /home. It's easier for backups or reinstall.

---

### Post by ajgreeny on 2018-09-23
It would be very helpful to see a screenshot of gparted showing the partitions on your hard drive as we can then give better advice.

As the two other respondents have said, **make sure you have full backups of all your personal files in particular**; I can't help with Windows as I haven't used it for 13 years and XP, but make sure you can also restore that OS with whatever is available to you should the whole OS become totally corrupt.

Reinstalling Ubuntu is no problem, so I never bother with a full backup of the OS itself, and only backup my home, including all the hidden folders and files, and as suggested and advised by Impavidus, I suggest you retain the unallocated space from Windows shrinking as a separate ext4 partition; how you then use that new partition depend on its size and how much data you currently have which is why the screenshot of gparted will help so much.

---

### Post by kevinorourke2008 on 2018-09-24
I've attached my screenshot to this message. As you can see the partition for windows is quite big and my ubuntu partition is not so big if possible i would like it to be the other way around.
So I will go into windows and shrink that partition and then reboot several times and then use gparted to resize partition for linux to use.

many thanks guys, I think im on the right track with your help.

kev.

---

### Post by Impavidus on 2018-09-25
You problem is that they're not adjacent. You want to shrink sda4, but you want to expand your /home partition, which is sda7. Your options after shrinking sda4 are either to create a new data partition, but having your data spread over two partitions (/home and /data) is not ideal. Or you can create a new /home partition between sda4 and sda5, copy all data, delete the old /home partition, move sda5 and sda6 to the right, expand the new /home partition to the right to occupy the free space and fix fstab, which is a complex procedure with many things that can go wrong.

Or maybe you would like an extra ntfs partition for data shared between Windows and Linux. It's not ideal for storing data you only need on Linux, but if you want to share data, it's better to have a separate data partition for that than to use the Windows C partition, so that you never have to mount the Windows C partition in Linux and don't risk damaging it.

---

### Post by HermanAB on 2018-09-25
I would partition the unallocated space and simply mount it as /mnt/data or some such and not try to resize the Ubuntu partition.  

Note that the more you faf with partitioning tools, the higher the likelyhood that you will corrupt the disk.

Therefore a better/safer idea is not to change the partitions at all, but simply mount the Windows partition in Ubuntu.

---

### Post by kevinorourke2008 on 2018-09-25
Hi Guys I've used the windows resizing tool and now have a partition which ive named storage but the problem is i cant see it in file manager without going into "other locations" but if i use sudo nautilus I can see the drive on the left of the screen. Is there a way that i can make the drive come up on the left hand side automatically instead of having to sign in as root

---

### Post by oldfred on 2018-09-25
It depends on where you mount your storage partition. If mounted in /home or /media/$USER then it should show in Nautilus.  But if mounted in / or /mnt then it will not directly show.
I mount my data partition in /mnt/data but link all folders into /home.

If you have it in fstab it will automatically be remounted on reboot. You can use device, label or UUID to mount in fstab. device is now not recommended as plugging in flash drives or other USB drives may change drive order, and then mount does not work.

Post these:
lsblk -f
cat /etc/fstab

---

### Post by kevinorourke2008 on 2018-09-25
NAME   FSTYPE  LABEL       UUID                                 MOUNTPOINT
loop0  squashf                                                  /snap/skype/51
loop1  squashf                                                  /snap/core/4917
loop2  squashf                                                  /snap/core18/19
loop3  squashf                                                  /snap/core/5145
loop4  squashf                                                  /snap/boa/141
loop5  squashf                                                  /snap/animationm
loop6  squashf                                                  /snap/test-snapd
loop7  squashf                                                  /snap/canonical-
loop8  squashf                                                  /snap/gimp/39
loop9  squashf                                                  /snap/skype/48
loop10 squashf                                                  /snap/boa/134
loop11 squashf                                                  /snap/gimp/40
loop12 squashf                                                  /snap/canonical-
loop13 squashf                                                  /snap/gimp/47
loop14 squashf                                                  /snap/skype/54
loop15 squashf                                                  /snap/simplenote
loop16 squashf                                                  /snap/simplenote
loop17 squashf                                                  /snap/boa/144
loop18 squashf                                                  /snap/simplenote
loop19 squashf                                                  /snap/canonical-
loop20 squashf                                                  /snap/core/5328
sda                                                             
&#9500;&#9472;sda1 ntfs    System      DC586B06586ADF30                     
&#9500;&#9472;sda2 vfat                AA6C-4912                            /boot/efi
&#9500;&#9472;sda3 ntfs                566E6DE36E6DBBFD                     
&#9500;&#9472;sda4 ntfs    TI31205500A 884EACA34EAC8B8E                     
&#9500;&#9472;sda5 ntfs                A0086D4F086D258E                     
&#9500;&#9472;sda6 ext4                2483a70d-d771-467c-bf62-891847fafeb5 /
&#9500;&#9472;sda7 ext4                877249f5-646e-4a40-9e63-37ddf19bdf22 /home
&#9500;&#9472;sda8 ntfs    Recovery    42C80C3EC80C3329                     
&#9492;&#9472;sda9 ext4    storage     97a0e640-273d-4e1b-916e-7fd080e2b821 

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda7 during installation
UUID=2483a70d-d771-467c-bf62-891847fafeb5 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=AA6C-4912  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/sda8 during installation
UUID=877249f5-646e-4a40-9e63-37ddf19bdf22 /home           ext4    defaults

---

### Post by oldfred on 2018-09-25
Now you have a choice on where to mount it. You can directly mount in /home, in typical default mount /media/$USER/storage, or /mnt/storage. If in /mnt it will not be directly shown in Nautilus, I use links for each folder and do not want it there as link is there. But if you want storage in Nautilus you use either of the other choices.

Name used to mount does not have to be same as label. Or you can actually use label to mount partition. I once labeled partition data, but mounted as Data which confused everything as those are different.

I use this as my example to copy & edit with my UUID.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead. 

This is my mount:
# Entry for /dev/sdb4 on Asus AR:
UUID=a0c1c99f-0f09-4787-a7cc-9e15bb3b4aa5 /mnt/data ext4 relatime,nofail,x-systemd.device-timeout=4 0 2

You could use this:
sudo mkdir /mnt/shared
      
 LABEL="shared"  /mnt/shared  ext4  defaults,nofail,x-systemd.device-timeout=4  0  2 
And depending on where you want it or what to mount it at, various alternative.
If you need help on a specific entry post where and what name.

You may also need ownership & permissions. 
If at /mnt/data, change to what you actually use:
      
 sudo chmod -R a+rwX,o-w /mnt/data
sudo chown -R $USER:$USER /mnt/data

---

### Post by kevinorourke2008 on 2018-10-09
Hi Guys, thank you for all of your help with this matter, but i've decided to do the sensible thing which is to buy a 1 TB hard drive, reinstall windows 10 onto the drive and then install Ubuntu which will give me all of the options that I want. I'm going to allocate 100 gig to windows and then for ubuntu give myself 500 gig storage and 400 gig for ubuntu, or there abouts.

---

### Post by C.S.Cameron on 2018-10-09
> **kevinorourke2008 said:**
>  but if i use sudo nautilus I can see the drive on the left of the screen.  

Do not use "sudo nautilus", it can mess up your permissions, and it no longer works with 18.04.

---

