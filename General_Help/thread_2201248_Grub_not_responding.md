---
title: "Grub not responding"
date: 2014-01-23
forum: General Help
---

### Post by lumaja2 on 2014-01-23
Ubuntu 12.04 LTS
 

 Grub not responding
 

 After Ubuntu working very well on booting had power failure.
 Restart Ubuntu and got to GRUB on enter boot Linux 3.2.0-58-gereric-pae, nothing  appen
 and pressing any key there is not response looks like is frozen. Try various times but still no result.
 Only Ubuntu on this Hard Disk
 I have CD live and USB live
 What should I do?
 Thankyou.

---

### Post by zteam2 on 2014-01-23
The easiest way would probably be to run a disk check on the computer

Open nautilus and double click your harddrive to get it mounted.

Then go to a terminal and run

```
df -H
``` This lists all device mounted devices and their size so we can easily see it's device name.
After that run

```
sudo fsck /dev/sda1/ 
``` Replace sda1, with the device-name you got from df -H

If this is not working try with boot-repair [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bashing-om on 2014-01-23
lumaja2; zteam2 ;

Running a file system check is a good idea, However !

WARNING, can not run a file system check on a partition that is mounted, file system corruption will likely result.

Make sure the partition to be checked is NOT mounted, and as well swap turned off:
```

sudo fdisk -lu
mount
swapoff -a ##if required

``` To identify the partitions we are working with.

#From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
```

sudo e2fsck -C0 -p -f -v /dev/sda1

```
#if errors: -y auto answers yes for fixes needing response see man e2fsck
```

sudo e2fsck -f -y -v /dev/sda1

```

Then see what is.
[INDENT][INDENT][INDENT]all in the process
[/INDENT][/INDENT][/INDENT]

---

### Post by lumaja2 on 2014-01-24
hank you for your response.
 

 I follow your advise with df – H code, I have to explain:
 I have Ubuntu on two Hard Diks, one is the Main 250GB the other is Mini 250GB that I have Ubuntu installed and for Backup.
 The Main is the one with GRUB broken.
 I have the two now connected and comuticated to you with this Mini drive.
 I can't apply the code that you send me on Main disk.
 If I follow your advice, on my opinion is for the Mini drive which is working correct and not fixing Main the broken GRUB. Is This correct or I am wrong?
 I send the result of Terminal that I did
 Dont undersand “[SIZE=3]*Replace sda1, with the device-name you got from df -H*[/SIZE]”.
 Will you please send more imformation on this and if I should have Main HD connect at the same time.
 

 luis@luis-G41M-Combo:~$ df -H 
 Filesystem      Size  Used Avail Use% Mounted on 
 /dev/sdb1       249G  156G   81G  66% / 
 udev            1,1G  4,1k  1,1G   1% /dev 
 tmpfs           415M  873k  415M   1% /run 
 none            5,3M     0  5,3M   0% /run/lock 
 none            1,1G   82k  1,1G   1% /run/shm 
 luis@luis-G41M-Combo:~$ sudo fsck /dev/sda1/ 
 [sudo] password for luis:  
 fsck from util-linux 2.20.1 
 e2fsck 1.42 (29-Nov-2011) 
 /dev/sda1: clean, 961242/15204352 files, 25450994/60796416 blocks 
 luis@luis-G41M-Combo:~$  
 

 

 Thank you

---

### Post by jeanjd63 on 2014-01-24
Hello 
Can you give the return of :
**sudo   fdisk   -l**

---

### Post by lumaja2 on 2014-01-24
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c931d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   486373375   243185664   83  Linux
/dev/sda2       486375422   488396799     1010689    5  Extended
/dev/sda5       486375424   488396799     1010688   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d7d07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   486373375   243185664   83  Linux
/dev/sdb2       486375422   488396799     1010689    5  Extended
/dev/sdb5       486375424   488396799     1010688   82  Linux swap / Solaris
luis@luis-G41M-Combo:~$

---

### Post by jeanjd63 on 2014-01-24
You can try :
[B]sudo  fsck   -f  -y  /dev/sda1

[/B]and you reboot

If it's no ok you can try this from your install on /dev/sdb1 :

You verify that /dev/sda1 is the install that not work with :
[B]mount
[/B]
then :

[COLOR=#000000][FONT=Arial]**sudo  mount   /dev/sda1   /mnt**  
**sudo  mount  --bind  /dev  /mnt/dev**
**sudo  mount  --bind  /proc  /mnt/proc**
**sudo  mount  --bind  /sys  /mnt/sys**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**sudo  chroot  /mnt**[/FONT][/COLOR]
[B]update-grub
grub-install  /dev/sda
exit
[/B]
and you reboot.

---

### Post by lumaja2 on 2014-01-24
First the Terminal result
 **sudo fsck -f -y /dev/sda1**
 

 luis@luis-G41M-Combo:~$ sudo fsck -f -y /dev/sda1  
 [sudo] password for luis:  
 fsck from util-linux 2.20.1  
 e2fsck 1.42 (29-Nov-2011)  
 Pass 1: Checking inodes, blocks, and sizes  
 Pass 2: Checking directory structure  
 Pass 3: Checking directory connectivity  
 Pass 4: Checking reference counts  
 Pass 5: Checking group summary information  
 /dev/sda1: 961242/15204352 files (0.2% non-contiguous), 25450994/60796416 blocks 
 luis@luis-G41M-Combo:~$ 
 

 Second the Terminal result
 I Shut down, disconnect Mini HD and boot on Main HD it come back with grub screen  but still
 frozen. Then again restart thr computer with the two HDs and boot on the Mini HD go through your sugestion, with Main HD /dev/sda1 [SIZE=4]**unmount **[/SIZE][SIZE=3](is this wat you mean).[/SIZE]
 [SIZE=3]Terminal result:[/SIZE]
 

 

 [SIZE=3]luis@luis-G41M-Combo:~$ sudo mount /dev/sda1 /mnt [/SIZE] 
 [SIZE=3][sudo] password for luis: [/SIZE] 
 [SIZE=3]mount: /dev/sda1 already mounted or /mnt busy [/SIZE] 
 [SIZE=3]mount: according to mtab, /dev/sda1 is already mounted on /mnt [/SIZE] 
 [SIZE=3]luis@luis-G41M-Combo:~$ sudo mount --bind /dev /mnt/dev [/SIZE] 
 [SIZE=3]luis@luis-G41M-Combo:~$ sudo mount --bind /proc /mnt/proc [/SIZE] 
 [SIZE=3]luis@luis-G41M-Combo:~$ sudo mount --bind /sys /mnt/sys [/SIZE] 
 [SIZE=3]luis@luis-G41M-Combo:~$ sudo chroot /mnt [/SIZE] 
 [SIZE=3]root@luis-G41M-Combo:/# update-grub [/SIZE] 
 [SIZE=3]Generating grub.cfg ... [/SIZE] 
 [SIZE=3]Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-57-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-57-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-31-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-31-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae [/SIZE] 
 [SIZE=3]Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae [/SIZE] 
 [SIZE=3]Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae [/SIZE] 
 [SIZE=3]Found memtest86+ image: /boot/memtest86+.bin [/SIZE] 
 [SIZE=3]done [/SIZE] 
 [SIZE=3]root@luis-G41M-Combo:/# grub-install /dev/sda [/SIZE] 
 [SIZE=3]Installation finished. No error reported. [/SIZE] 
 [SIZE=3]root@luis-G41M-Combo:/# exit [/SIZE] 
 [SIZE=3]exit [/SIZE] 
 [SIZE=3]**luis@luis-G41M-Combo:~$ **[/SIZE] 
 

 [SIZE=3]After this  Shut down, disconnect Mini HD and boot on Main HD it come back with grub screen  but still frozen. [/SIZE] 
 [SIZE=3]I am sorry about this I was expecting for Ubuntu on the Main HD to boot.[/SIZE]

---

### Post by jeanjd63 on 2014-01-24
Have you do a mount to verify il it was /dev/sda1 or /dev/sdb1 the actual system ? 
Because /dev/sda1 was already mounted i think it was /dev/sdb1 to repair. Can you give the return of :
**mount**

---

### Post by lumaja2 on 2014-01-24
**luis@luis-G41M-Combo:~$ mount **

 **/dev/sdb1 on / type ext4 (rw,errors=remount-ro) **
 **proc on /proc type proc (rw,noexec,nosuid,nodev) **
 **sysfs on /sys type sysfs (rw,noexec,nosuid,nodev) **
 **none on /sys/fs/fuse/connections type fusectl (rw) **
 **none on /sys/kernel/debug type debugfs (rw) **
 **none on /sys/kernel/security type securityfs (rw) **
 **udev on /dev type devtmpfs (rw,mode=0755) **
 **devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620) **
 **tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755) **
 **none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880) **
 **none on /run/shm type tmpfs (rw,nosuid,nodev) **
 **gvfs-fuse-daemon on /home/luis/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=luis) **
 **luis@luis-G41M-Combo:~$  **
 

 The Main HD is the one with GRUB broken the Mini HD is the I been working and in contact with you right now dont know which is  /dev/sda1 or /dev/sda1, use the Terminal on Mini HD
 to write the commands that you send to me and then I restart computert with only the Main HD
 to try to boot.

---

### Post by Bashing-om on 2014-01-24
lumaja2; jeanjd63; Hey ,

Too many cooks spoils the soup, I do continue to monitor this thread. Yall are doing well.
If I may make a couple of observations and directives.
I triple boot 'buntus, and my grub often gets broke, - My system is set up the way I want and breaking grub I can fix, so advise;

You have verified that the main ubuntu on the first drive (sda) is intact - good !
There exist many "old" kernels, do we have space constraints ? 
check:
```

df -h
df -i

```
If you do have the operating overhead, proceed.
OK, now there can only be ONE grub controlling the boot process, all others are slave to this primary grub, This primary grub must be the 1st entry in the grub boot menu.
So, what to do ? -- been here many times - fix grub thus.
Boot the mini (sdb) install and 
```

sudo update-grub

```
now to make sure that sda (main OS) has control (re-)install grub to the MBR of the sda drive.
As you can not boot sda, then the procedure must be done from an exterior source, either sdb or liveDVD - whichever.
The easy way:
Boot from the alternate means: -> terminal codes:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work ##we know this is correct by the '*' in fdisk out put ##
sudo grub-install /dev/sda
sudo umount /mnt/work

```

Reboot and make sure that  sda is the 1st boot priority.
Should workie great, last long time;
Else
We will be looking at the primaries' /etc/fstab file.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by lumaja2 on 2014-01-25
Come back after a good rest.
 Error on may last reply (right now dont know which is /dev/sda1 or /dev/sda1) shoud be /dev/sda or /dev/sda1. Dont know this commends and still dont understand which is which my assumption is the (**sda)** is Main one and** (sd1)** is the Mini, or** (sda)** with broken Grub and **(sd1)** the working HD. Please correct me.
 

 **You have verified that the main ubuntu on the first drive (sda) is intact - good !.**
 Dont understand **You have verified that the main ubuntu on the first drive (sda) is intact - good !.   **as above my view **(sda) **is Main with broken Grub. Confused with this.
 (There exist many "old" kernels, [SIZE=4]**do we have space constraints ?) **[/SIZE][SIZE=3]dont understand.[/SIZE]
 

 Terminal result:
 luis@luis-G41M-Combo:~$ df -h 
 Filesystem      Size  Used Avail Use% Mounted on 
 /dev/sdb1       232G  146G   75G  66% / 
 udev            983M  4,0K  983M   1% /dev 
 tmpfs           396M  852K  395M   1% /run 
 none            5,0M     0  5,0M   0% /run/lock 
 none            990M   80K  990M   1% /run/shm 
 /dev/sda1       232G   97G  124G  44% /media/feeb7ae5-1ada-4933-a640-bb0d40ee4e2a 
 luis@luis-G41M-Combo:~$ df -i 
 Filesystem       Inodes  IUsed    IFree IUse% Mounted on 
 /dev/sdb1      15204352 197609 15006743    2% / 
 udev             215879    566   215313    1% /dev 
 tmpfs            219514    478   219036    1% /run 
 none             219514      3   219511    1% /run/lock 
 none             219514      5   219509    1% /run/shm 
 /dev/sda1      15204352 961242 14243110    7% /media/feeb7ae5-1ada-4933-a640-bb0d40ee4e2a 
 [EMAIL="luis@luis-G41M-Combo"][COLOR=#000000]luis@luis-G41M-Combo[/COLOR][/EMAIL]:~$
 

 Sorry, but I dint carry on with other commands because of above confusion dont want to brake anything and thank you for your help.

---

### Post by Bashing-om on 2014-01-25
lumaja2; Hey,

I too am tired and my ability to think is impaired.
The out puts of "df -h and i" are good. So we may proceed.
In my AM I will look over this thread once more, see IF I can determine what ubuntu is installed on which drive.

At that time I will respond to your questions in your last post.

[INDENT][INDENT]cheerfully making progress
[/INDENT][/INDENT]

---

### Post by jeanjd63 on 2014-01-25
Hello 
I don't know why the system respond /dev/sda1  busy in post #8.
You can try  :

[B]sudo  umount  /dev/sda1
sudo mkdir  /tmp/sda1[/B]
[COLOR=#000000][COLOR=#000000][FONT=Arial][B]sudo mount /dev/sda1 /tmp/sda1

[/B]and verify you have no error messages  

**sudo mount --bind /dev /tmp/sda1/dev**
**sudo mount --bind /proc /tmp/sda1/proc**
**sudo mount --bind /sys /tmp/sda1/sys**[/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Arial]**sudo chroot /tmp/sda1**[/FONT][/COLOR][/COLOR]
[B]update-grub
grub-install /dev/sda
exit

[/B]And you reboot on /dev/sda

---

### Post by lumaja2 on 2014-01-25
luis@luis-G41M-Combo:~$ sudo umount /dev/sda1 
 [sudo] password for luis:  
 luis@luis-G41M-Combo:~$ sudo mkdir /tmp/sda1 
 luis@luis-G41M-Combo:~$ sudo mount /dev/sda1 /tmp/sda1 
 luis@luis-G41M-Combo:~$ sudo mount --bind /dev /tmp/sda1/dev 
 luis@luis-G41M-Combo:~$ sudo mount --bind /proc /tmp/sda1/proc 
 luis@luis-G41M-Combo:~$ sudo mount --bind /sys /tmp/sda1/sys 
 luis@luis-G41M-Combo:~$ sudo chroot /tmp/sda1 
 root@luis-G41M-Combo:/# update-grub 
 Generating grub.cfg ... 
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported. 
 Found linux image: /boot/vmlinuz-3.2.0-58-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-58-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-57-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-57-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-56-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-56-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-55-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-55-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-54-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-54-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-53-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-53-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-52-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-52-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-51-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-51-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-49-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-49-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-45-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-45-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-44-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-44-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-43-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-43-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-40-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-40-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-39-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-39-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-38-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-38-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-37-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-37-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-36-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-36-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-35-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-35-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-32-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-32-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-31-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-31-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-30-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-30-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-29-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-29-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-26-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-26-generic-pae 
 Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae 
 Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae 
 Found memtest86+ image: /boot/memtest86+.bin 
 done 
 root@luis-G41M-Combo:/# grub-install /dev/sda 
 Installation finished. No error reported. 
 root@luis-G41M-Combo:/# exit 
 exit 
 luis@luis-G41M-Combo:~$

---

### Post by jeanjd63 on 2014-01-25
And now if you reboot on device /dev/sda what it say?

---

### Post by lumaja2 on 2014-01-25
[SIZE=3]Sorry I Forgot to reboot.[/SIZE]
 [SIZE=3]On reboot Main drive the same, dint start.[/SIZE]

 [SIZE=3]Lately on reboot in Mini drive with the two drves connected I get the Grub screen[/SIZE]
 [SIZE=3]but clicking on Enter it reboots.[/SIZE]
 [SIZE=3]On idea instead of wotking with two Ubuntu drives I thought if working with Live CD to be[/SIZE]
 [SIZE=3]easyer but slower, is this correct?[/SIZE]

---

### Post by jeanjd63 on 2014-01-25
Can you try to boot on kernel [COLOR=#000000]3.2.0-57 on your first drive ?[/COLOR]

---

### Post by lumaja2 on 2014-01-25
[SIZE=3][COLOR=#000000]Dont know kernel 3.2.0-57 and first drive is this the one I call Main or on the Mini on which wright this on? Please explain.[/COLOR][/SIZE]

---

### Post by jeanjd63 on 2014-01-25
In update-grub on main install we can see this :
[SIZE=3][COLOR=#000000]Found linux image: /boot/vmlinuz-3.2.0-57-generic-pae [/COLOR][/SIZE]
[SIZE=3][COLOR=#000000]Found initrd image: /boot/initrd.img-3.2.0-57-generic-pae

So you can try to boot, on main device, on this kernel (if grub menu don't appears you press key Shift during boot).[/COLOR][/SIZE]

---

### Post by lumaja2 on 2014-01-25
I tried again with Shift the grub page come up, as usually the cursor is on &#8220;ubunty, with Linux 3.2.0.58-generic-pae&#8221; underneath is another with the same and (recovry mode) but still frozen.

---

### Post by jeanjd63 on 2014-01-25
You don't have "previous versions" ?

---

### Post by lumaja2 on 2014-01-25
I tried again with Shift the grub page come up, as usually the cursor is on &#8220;ubunty, with Linux 3.2.0.58-generic-pae&#8221; underneath is another with the same and (recovry mode) but still frozen.

---

### Post by lumaja2 on 2014-01-25
Previous Grub version or Ubuntu, Ubuntu have 10.04 LTS Grub no and dont know.

---

### Post by jeanjd63 on 2014-01-25
There is an other choice on third line ? 
If yes you keep it and on next screen, you choice the third line.

---

### Post by lumaja2 on 2014-01-25
We crossing Replys, on Main disk Grub is totally frozen the arrow keys do not respond or nothingelse.

---

### Post by jeanjd63 on 2014-01-25
Have you important data on /dev/sda1 ? If yes save and reinstall. I think it is broken and i don't see any way to repair.
Good luck.

---

### Post by oldfred on 2014-01-25
May be best to see details. Do not run auto fix with Boot-Repair as it will install one grub in both drives. With manual fix from advanced you can choose one install and that drive's MBR to install into.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

You do have a lot of kernels. Usually best to house periodically. I typically keep 2, current and one older one.
After you get it fixed.

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by lumaja2 on 2014-01-25
No /dev/sda1 to me the Mini is for long time in is box, i use it now because it is faster that Live CD

---

### Post by lumaja2 on 2014-01-25
Going away until Wedsday or Thursday

---

### Post by lumaja2 on 2014-01-30
[COLOR=#000000][SIZE=3]I am back and need help with the following:[/SIZE][/COLOR]
 

 [INDENT][COLOR=#000000][SIZE=3]With manual fix from advanced you can [SIZE=4]***choose one install and that drive's MBR to install into.***[/SIZE][/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]I got confused with Boot-Repair which commands should I use?[/SIZE][/COLOR][/INDENT]

---

### Post by Bashing-om on 2014-01-30
lumaja2; Consider.

IF the ubuntu install that is on that 1st hard drive is to be your PRIMARY operating system, then install grub to sda.
This then will be your controlling grub from which all other operating systems will boot from.(bios set to boot 1st hard drive as 1st priority)

[INDENT][INDENT]hope that helps
[/INDENT][/INDENT]

---

### Post by lumaja2 on 2014-01-31
[INDENT][COLOR=#000000][SIZE=3]I deep apoligze for now knowing enough.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]My problem is this of two hard drives I dont know which is sda.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]I have connected now 2 hard drives that are exactly the same and have Ubuntu installed the difference is one is a small disk from a laptop (which I can connect as usb as well), now I use this disk to boot Ubuntu, the other is normal hard disk (I think this is the one you mention the PRIMARY) and it as the broken Grub.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]Which of this is sda and sdb, to install the new Grub.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]In Boot-Repair advanced Main options must I open Reinstall GRUB and Restore MBR and Apply?[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]Please give this imformation.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]Thank you[/SIZE][/COLOR][/INDENT]

---

### Post by oldfred on 2014-01-31
Boot-Repair will normally auto fix single installs, and works with external drives if you correctly say yes to the question it should ask about is this drive an external drive.

Otherwise Boot-Repair installs one version of grub to the MBR of all drives. Which usually is not the best case if you have multiple installs and multiple drives. Then best to uncheck auto and use advanced options and the grub location tab. You chose which operating system and which drive.

If not sure we can give more detail if you run the BootInfo report from Boot-Repair and post the link it gives.

---

### Post by lumaja2 on 2014-01-31
[INDENT][COLOR=#000000][SIZE=3]To oldfred[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]**[http://paste.ubuntu.com/6849941/](http://paste.ubuntu.com/6849941/) **[/SIZE][/COLOR] [/INDENT] [INDENT][COLOR=#000000][SIZE=3]Follow your instructions and on advanced and winthout changing the settings click Apply, it gave the above URL.[/SIZE][/COLOR]
[/INDENT] [INDENT][COLOR=#000000][SIZE=3]Shut Down computer disconnect Main Hard Disk and restart computer on external drive which is the one with working Grub a full page open with Grub with other entries on and start Ubuntu.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]Shut Down again connect the Main Hard Disk (one with Grub broken) it got to [/SIZE][/COLOR] [/INDENT] [INDENT][COLOR=#000000][SIZE=3]Verifying DMI Pool Data[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]Missing operating system[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]What to do next?[/SIZE][/COLOR][/INDENT]

---

### Post by oldfred on 2014-01-31
It looks like you ran this:
> Reinstall the GRUB of sdb1 into the MBR of sdb

But you need to run this:
Reinstall the GRUB of sda1 into the MBR of sda

---

### Post by lumaja2 on 2014-02-01
[INDENT][COLOR=#000000][SIZE=3]To oldfred[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3][http://paste.ubuntu.com/6853077/](http://paste.ubuntu.com/6853077/)[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]Explaining what I did:[/SIZE][/COLOR][/INDENT] [INDENT][COLOR=#000000][SIZE=3]On Boot-Repair  Main options [/SIZE][/COLOR] [/INDENT] [INDENT][COLOR=#000000][SIZE=3]Reinstall GRUB is &#8220;*ticked&#8221;  *Unhide boot menu:  *10 seconds.*[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]Open GRUB location[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]OS to boot by default:  *&#8220;sdb1 (The OS now in use &#8211; Ubuntu 12.04 LTS)&#8221;*[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]I change Place GRUB into:  *&#8220;sda&#8221;     and Apply*[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]Boot Main drive result:[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]_Verifying DMI Pool Data_[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]_error: no such device: 0ba58038-0fa4-4232-a92d-fbaf38f1c543._[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]_Grub rescue>_[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]Dont wanted to brake the hard disk or Ubuntu so I am very unsure of GRUB.[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]Appreciate very much your great help and I am sorry it didn't come right from the beginning.[/SIZE][/COLOR][/INDENT] [INDENT] [COLOR=#000000][SIZE=3]Please explain  how to setup GRUB properly (where and what) to achieve this successfully[/SIZE][/COLOR][/INDENT]

---

### Post by oldfred on 2014-02-01
You installed the Ubuntu in sdb into the MBR of sda.

You want to select the install in sda and install to the MBR of sda. Boot-Repair should let you manually do that.

This should be sda1 and not the one in use.
 OS to boot by default: “sdb1 (The OS now in use – Ubuntu 12.04 LTS)”
I change Place GRUB into: “sda” and Apply

---

### Post by lumaja2 on 2014-02-02
Main drive is working but not as normal, on booting opens GRUB page and from there then it boots this happens on both Hard Disks. How to fix this last gremlin Please. Thank you for your good and appreciated help

---

### Post by oldfred on 2014-02-02
Not sure what gremlin you are concerned about.
With two systems, grub menu should show, so you can choose which system to boot.
Default is 10 sec wait and then it boots the default entry.

See Boot Display Behaviour in this:
 gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)

---

