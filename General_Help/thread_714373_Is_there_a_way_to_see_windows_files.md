---
title: "Is there a way to see windows files"
date: 2008-03-03
forum: General Help
---

### Post by zorlab on 2008-03-03
I have a dual boot with Ubuntu and windows XP
Just got the blue screen of death on windows and cannot get back in.
Is the an interface or a way to transfer files to Ubuntu from the Windows NTFS  partition?

---

### Post by Rocket2DMn on 2008-03-03
Yes, you need to use the ntfs-3g driver.  If you're using Gutsy, then it is already available to you.
Can you please post the output of:
```
sudo fdisk -l
cat /etc/fstab
```
Let me know if you're not using Gutsy and we will install ntfs-3g.

---

### Post by Feivel on 2008-03-03
> **zorlab said:**
> I have a dual boot with Ubuntu and windows XP
Just got the blue screen of death on windows and cannot get back in.
Is the an interface or a way to transfer files to Ubuntu from the Windows NTFS  partition?

Download the NTFS config tool from your package manager. Works great and it accessed my 320 gig drive without any trouble.

---

### Post by zorlab on 2008-03-03
Have Gutzy 7.10

here is what I get, bear in mind that I am running a raid 0 (2) 250 gig drives

```

barry@oogla-desktop:~$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09470947

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6120    49152000    7  HPFS/NTFS
/dev/sda2            6120       60802   439239041    5  Extended

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000201

Disk /dev/sdb doesn't contain a valid partition table
barry@oogla-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/via_egecdejbi5
UUID=a006fdf4-7d5c-4308-8a6e-5359e0f66943 /               ext3    defaults,errors=remount-ro 0       1
# /dev/mapper/via_egecdejbi6
UUID=27b603e3-df72-4e5d-8822-323241f58a48 /home           ext3    defaults        0       2
# /dev/mapper/via_egecdejbi7
UUID=d7956f83-93b6-4cf0-899b-ed24c8dc4bd4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

### Post by zorlab on 2008-03-03
> **Feivel said:**
> Download the NTFS config tool from your package manager. Works great and it accessed my 320 gig drive without any trouble.

Have to try this after...

---

### Post by Rocket2DMn on 2008-03-03
OK, you need to make an fstab entry for your windows partition (/dev/sda1 it seems).
First make the mount point, then edit fstab.
```
sudo mkdir /media/windows
gksudo gedit /etc/fstab
```
Then add the line
```
/dev/sda1 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close, then run
```
sudo mount -a
```
You should now be able to see the contents of your windows partition.
Like Feivel said, you may need to enable writing with the ntfs-config tool
```
sudo apt-get install ntfs-config
//(if it already exists, then good)
gksudo ntfs-config
```

If you have any problems, let me know and we'll get it fixed.

---

### Post by zorlab on 2008-03-04
well I edited fstab as you meantioned

but I get the following error after the next command:
```
barry@oogla-desktop:~$ sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
barry@oogla-desktop:~
```

could this be because  of the raid array?  should I run dmraid first?

---

### Post by fjgaude on 2008-03-04
Say, I don't think you can mount a raid0 NTFS drive in Ubuntu without using dmraid.

You know dmraid?

---

### Post by zorlab on 2008-03-04
> **fjgaude said:**
> Say, I don't think you can mount a raid0 NTFS drive in Ubuntu without using dmraid.

You know dmraid?


Thats just what I said in the previous message, I had to have dmraid running to partition  and config the drives.
My question was should I run it and then go through the commands that **Rocket ** gave me?

---

### Post by fjgaude on 2008-03-04
I must say I don't know what's going on. You have to mount your raid0 with your dmraid situation:

Find out what dmraid is listing your array as:

```
sudo dmraid -tay
```

Then mount:

```
sudo mount -t ntfs-3g /dev/mapper/<whateveryou get from the above command> /media/windows
```

From -tay you will see something like sil_ahahbhbjaddo. This is what you use to mount by name the array.

I'm making several assumptions, you have already installed ntfs-3g, that you are running a kernel that is latter than 2.6.20.

Let us know how you are doing.

---

### Post by zorlab on 2008-03-05
Ok  here is what I did 
```
barry@oogla-desktop:~$ sudo dmraid -tay
[sudo] password for barry:
via_egecdejbi: 0 976794112 striped 2 128 /dev/sda 0 /dev/sdb 0
via_egecdejbi1: 0 98304000 linear /dev/mapper/via_egecdejbi 2048
via_egecdejbi5: 0 200004874 linear /dev/mapper/via_egecdejbi 98306111
via_egecdejbi6: 0 600011622 linear /dev/mapper/via_egecdejbi 298311048
via_egecdejbi7: 0 78461397 linear /dev/mapper/via_egecdejbi 898322733

barry@oogla-desktop:~$ sudo fdisk /dev/mapper/via_egecdejbi

The number of cylinders for this disk is set to 60802.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/via_egecdejbi: 500.1 GB, 500118585344 bytes
255 heads, 63 sectors/track, 60802 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09470947

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/via_egecdejbi1   *           1        6120    49152000    7  HPFS/NTFS
/dev/mapper/via_egecdejbi2            6120       60802   439239041    5  Extended
/dev/mapper/via_egecdejbi5            6120       18569   100002437   83  Linux
/dev/mapper/via_egecdejbi6           18570       55918   300005811   83  Linux
/dev/mapper/via_egecdejbi7           55919       60802    39230698+  83  Linux

Command (m for help): sudo mount -t ntfs-3g dev/mapper/via_egecdejbi1 /media/windows
Building a new sun disklabel. Changes will remain in memory only,
until you decide to write them. After that, of course, the previous
content won't be recoverable.

Floating point exception (core dumped)
barry@oogla-desktop:~$ w
 08:21:44 up 35 min,  2 users,  load average: 0.18, 0.08, 0.07
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
barry    tty9     :0               08:07    0.00s 18.56s  0.11s x-session-manag
barry    pts/0    :0.0             08:09    0.00s  0.16s  0.00s w
barry@oogla-desktop:~$ 

```

not sure what I wrote...... but  then I exited and reboot - now what?

---

### Post by zorlab on 2008-03-05
aha!!  got it!  I see  I was trying to mount in fdisk, had to exit first.   
Then it worked  now I have a nice 
Windows Icon on my desktop with all the files! [B] thankyou everyone.:)
[/B]
One thing.. is there something that I wrote to the partition tables that I have to undo?

---

### Post by zorlab on 2008-03-05
Oh darn!  after reboot the files are gone,  


lost and bewildered

---

### Post by Rocket2DMn on 2008-03-05
Your files aren't gone, the drive just isn't mounted so the mount point looks empty.  If you mounted from the command line, you need to mount again after reboot, but if you put it in fstab, run
```
sudo mount -a
```
and post the output so we can see the errors.  If this is the case, also post your fstab file.

---

### Post by fjgaude on 2008-03-05
As far as I can see, you will have to make an entry in fstab for each partition on your drive for it to mount at boot time.

---

### Post by zorlab on 2008-03-05
I think I understand where this is going, but rather than screwing up the edit 
Ill let you give me the info :):)

```








barry@oogla-desktop:~$ sudo mount -a
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

barry@oogla-desktop:~$ sudo dmraid -r
/dev/sda: via, "via_egecdejbi", stripe, ok, 488397167 sectors, data@ 0
/dev/sdb: via, "via_egecdejbi", stripe, ok, 488397167 sectors, data@ 0

barry@oogla-desktop:~$ sudo fdisk -l
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09470947

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6120    49152000    7  HPFS/NTFS
/dev/sda2            6120       60802   439239041    5  Extended

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000201

Disk /dev/sdb doesn't contain a valid partition table
barry@oogla-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/via_egecdejbi5
UUID=a006fdf4-7d5c-4308-8a6e-5359e0f66943 /               ext3    defaults,errors=remount-ro 0       1
# /dev/mapper/via_egecdejbi6
UUID=27b603e3-df72-4e5d-8822-323241f58a48 /home           ext3    defaults        0       2
# /dev/mapper/via_egecdejbi7
UUID=d7956f83-93b6-4cf0-899b-ed24c8dc4bd4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1 /media/windows ntfs-3g default,locale=en_US.utf8 0 0

barry@oogla-desktop:~$ gksudo gedit /etc/fstab
```




.................................................................
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/via_egecdejbi5
UUID=a006fdf4-7d5c-4308-8a6e-5359e0f66943 /               ext3    defaults,errors=remount-ro 0       1
# /dev/mapper/via_egecdejbi6
UUID=27b603e3-df72-4e5d-8822-323241f58a48 /home           ext3    defaults        0       2
# /dev/mapper/via_egecdejbi7
UUID=d7956f83-93b6-4cf0-899b-ed24c8dc4bd4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1 /media/windows ntfs-3g default,locale=en_US.utf8 0 0
...............................................................

By the way.  ~~> here is the NTFS partition designation  in dmraid, fdisk 
[B]
/dev/mapper/via_egecdejbi1
[/B]

---

### Post by fjgaude on 2008-03-05
> **zorlab said:**
> 
.................................................................
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/via_egecdejbi5
UUID=a006fdf4-7d5c-4308-8a6e-5359e0f66943 /               ext3    defaults,errors=remount-ro 0       1
# /dev/mapper/via_egecdejbi6
UUID=27b603e3-df72-4e5d-8822-323241f58a48 /home           ext3    defaults        0       2
# /dev/mapper/via_egecdejbi7
UUID=d7956f83-93b6-4cf0-899b-ed24c8dc4bd4 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sda1 /media/windows ntfs-3g default,locale=en_US.utf8 0 0
...............................................................

By the way.  ~~> here is the NTFS partition designation  in dmraid, fdisk 
[B]
/dev/mapper/via_egecdejbi1
[/B]

I guess you have gotten the UUIDs for the mounted drives by using something like vol_id command, eh?

I think all you have to do now is use the /dev/mapper/via_egecdejbi1 in place of the /dev/sda1 in your fstab. You could get its UUID if you wish and use that instead of the mapper name.

Let us know how things go.

---

### Post by zorlab on 2008-03-05
> **fjgaude said:**
> I guess you have gotten the UUIDs for the mounted drives by using something like vol_id command, eh?

I think all you have to do now is use the /dev/mapper/via_egecdejbi1 in place of the /dev/sda1 in your fstab. You could get its UUID if you wish and use that instead of the mapper name.

Let us know how things go.

hmmm don't know what you mean
I used the tutorial here on the forum to install dual boot from the live/install 7.1 cd.
Tried your edit and this did not work. 

I am thinking my only hope is to write a script or command lines that will work when I click on an icon ( think i saw this somewhere)...

Ubuntu apparently does not see /etc/mapper/via_egecdejbi1 in Partitions unless dmraid is running.

Is this correct?  Am I on the right track here?

---

### Post by fjgaude on 2008-03-05
When you boot Ubuntu dmraid starts automatically. It is in the kernel.

Can you manually mount sda1 when in Ubuntu?

[HTML]sudo mount /dev/mapper/via_egecdejbi1 /media/windows[/HTML]

---

### Post by zorlab on 2008-03-05
Just booted into Ubuntu to input the command```
sudo mount /dev/mapper/via_egecdejbi1 /media/windows
```......... but before I had the chance, there is the mounted Widows partition, on my desktop.:confused:

This is par for the course with my experience with Ubuntu... each boot brings up different, errors, low graphics mode, wont boot, have to use recovery mode, desktop res changes,, Fire fox keeps crashing, etc.

 Darn, I was hopping I would avoid all this crap, going over to linux  :(

I suspect next reboot and the file will get inaccessible again!  who knows.

Thanks for the help guys..   if there is anything else to config,  let me know please!

---

### Post by Rocket2DMn on 2008-03-05
If windows is not shut down correctly, linux won't be able to mount the ntfs drive/partition without you forcing it to, so something similar to this may have been the reason it didn't automount on boot.  It won't mount if you hibernate windows either, it has to be completely shut down.

---

### Post by zorlab on 2008-03-05
well ok.......... booted several times to ubuntu and it is working perfectly now

TKS again

---

### Post by fjgaude on 2008-03-05
What you have been doing with Ubuntu is learning its general capabilities at handling just about anything. All it takes is time and patience to learn, to learn what is needed to get to where you wish to be.

Glad things are finally going your way.

---

### Post by zorlab on 2008-03-06
Thats right  I am not giving up that easy, If it take a bit of time to customise it and adjust and configure it so it is stabe, I will do just that, soI can be running a virus free no bull-**** op sys

So far I have fixed 4 issues, and I just installed  the customized alternative browser for Firefox. (name excapes me right now..) It was crashing often.  

What was amaising is all the dedicated people working to provide harware specific apps!

Wonderful folks here. Cant beat the support

---

### Post by fjgaude on 2008-03-06
Well, you see by my signature what I did... it works well this way... with a fast box I get my work done and have time to help others, as they have helped me.

Life is good!

---

