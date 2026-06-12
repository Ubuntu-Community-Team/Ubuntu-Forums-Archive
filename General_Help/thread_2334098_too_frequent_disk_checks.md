---
title: "too frequent disk checks"
date: 2016-08-16
forum: General Help
---

### Post by Buntu Bunny on 2016-08-16
This is new. Almost every time I boot up I get a disk check. No errors are found, but it makes me nervous because it's doing it so frequently. 

It started the other day when my husband was the first to use the computer. When I tried to switch users, the system froze. Alt SysRq REISUB did nothing. First hard boot gave me only a black screen. Second one did a disk check and found errors. System froze again when I chose "try to fix." Third reboot brought up Grub, then the splash screen with a disk check. This time my desktop loaded fine. Since then it wants to do a disk check every morning when I start the machine.

My machine is an Asus CM 1740. It came with Windows 7 installed, so I've had it about 4 years. It is set up as a dual boot with Windows.

Obviously I'm worried about hard drive failure. Or could something else be going on? Something I can fix? While I await answers I'll get a fresh backup of everything I don't want to lose.

---

### Post by sudodus on 2016-08-16
Have you checked the S.M.A.R.T. status? You can do it with Disks alias ***gnome-disks***, or with ***smartctl*** (installed with the package smartmontools).

Is there a problem with the root partition (with ext4)? After an update of 16.04 maybe one month ago I had constant checking (at each boot) and I could get rid of it after running ***e2fsck*** and ***tune2fs***.

You can check it with

```
sudo e2fsck -cf /dev/sdxy
```

in order to check not only the logical structure, but also the memory locations on the disk (if the blocks are healthy or not).

You can check and change the settings for automatic checking the ext file system with ***tune2fs***. See ```
man tune2fs
``` for details.

-o-

Check the corresponding things of Windows file systems with Windows tools (***chkdsk*** or a GUI tool).

---

### Post by Buntu Bunny on 2016-08-16
sudodus, thank you for your help!

> **sudodus said:**
> Have you checked the S.M.A.R.T. status? You can do it with Disks alias ***gnome-disks***, or with ***smartctl*** (installed with the package smartmontools).

I found GSmartControl in the Software Centre, installed, and ran that. It reported "Passed" (but see EDIT below).

> Is there a problem with the root partition (with ext4)? <snip>

You can check it with

```
sudo e2fsck -cf /dev/sdxy
```

in order to check not only the logical structure, but also the memory locations on the disk (if the blocks are healthy or not).

For that I got

```
BuntuBunny@BuntuBunny-CM1740:~$ sudo e2fsck -cf /dev/sdxy
[sudo] password for BuntuBunny: 
e2fsck 1.42 (29-Nov-2011)
e2fsck: No such file or directory while trying to open /dev/sdxy
Possibly non-existent device?

```

I'm thinking I didn't do that correctly(?)

EDIT: after I published this post I explored GSmartControl and found the self-test tab. There were some problems with the self test.

> Test #1
Type: Short Offline
Status: Completed with read failure
% Completed: 10%
Lifetime hours: 24789
LBA of the first error: 380571375

Complete selective self-test log:

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.


That doesn't sound good.

---

### Post by Cavsfan on 2016-08-16
> **Buntu Bunny said:**
> 
```
BuntuBunny@BuntuBunny-CM1740:~$ sudo e2fsck -cf /dev/sdxy
[sudo] password for BuntuBunny: 
e2fsck 1.42 (29-Nov-2011)
e2fsck: No such file or directory while trying to open /dev/sdxy
Possibly non-existent device?

```

sd[COLOR=#ff0000]xy[/COLOR] was meant to be changed to your disk and partition. Like if you have your install on one disk it would be sd[COLOR=#ff0000]a[/COLOR], if 2nd disk it would be sd[COLOR=#ff0000]b[/COLOR], etc.
The y represents the partition of that disk 1, 2, 3, 4, etc.

lsblk will provide a list of your disks/partitions like this:
```
cavsfan@cavsfan-le-beast:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 262.8G  0 part 
&#9500;&#9472;sda2   8:2    0     4G  0 part [SWAP]
&#9500;&#9472;sda3   8:3    0 170.4G  0 part 
&#9500;&#9472;sda4   8:4    0     1K  0 part 
&#9500;&#9472;sda5   8:5    0  18.6G  0 part /
&#9492;&#9472;sda6   8:6    0    10G  0 part 
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/cavsfan/Fantom
sr0     11:0    1  1024M  0 rom  
```

If your partition was the 3rd one on disk drive 1, enter:

```
sudo e2fsck -cf /dev/sd[COLOR=#ff0000]a3[/COLOR]
```

Change it to suit your system and see what the output of that is.

---

### Post by sudodus on 2016-08-16
Sorry for /dev/sdxy (I thought that with so many beans, you needed no explanation). Thanks to *Cavsfan* for a good explanation (that I should have included in my first post)!

-o-

I agree that the S.M.A.R.T. status is somewhat alarming.

> Test #1
Type: Short Offline
Status: Completed with read failure


I'm glad that you made the backup at once (as you wrote in your first post). Some people continue to use drives with bad blocks, but keep an eye on the number of bad blocks with read and/or write errors. If the number starts to increase rapidly, they replace the drive.

I don't rely on a drive with bad blocks (as discovered by e2fsck and chkdsk), and try to replace it as soon as possible, at least in a computer with important data.

---

### Post by Buntu Bunny on 2016-08-16
> **Cavsfan said:**
> sd[COLOR=#ff0000]xy[/COLOR] was meant to be changed to your disk and partition. Like if you have your install on one disk it would be sd[COLOR=#ff0000]a[/COLOR], if 2nd disk it would be sd[COLOR=#ff0000]b[/COLOR], etc.
The y represents the partition of that disk 1, 2, 3, 4, etc. ...<snip> ...

Cavsfan, excellent explanation, thank you so much. 

> **sudodus said:**
> Sorry for /dev/sdxy (I thought that with so many beans, you needed no explanation).

You'd think. I've just have a lot of questions. :P Becoming a Linux guru is on my to-do list, but I just haven't gotten to it yet. 

> **sudodus said:**
> 

I agree that the S.M.A.R.T. status is somewhat alarming.

I'm glad that you made the backup at once (as you wrote in your first post). Some people continue to use drives with bad blocks, but keep an eye on the number of bad blocks with read and/or write errors. If the number starts to increase rapidly, they replace the drive.

I don't rely on a drive with bad blocks (as discovered by e2fsck and chkdsk), and try to replace it as soon as possible, at least in a computer with important data.

That's very telling and very helpful; keeps me from having to wrestle with "what to do." I'd been working on backups to get ready to update from 12.04 to 16.04, but I think it would be best to replace the computer altogether.

Many thanks for the help! Love this forum.

---

### Post by sudodus on 2016-08-16
You are welcome :-)

If you feel that your problem/question of the first post is solved/answered, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by Cavsfan on 2016-08-16
You are very welcome! :) Xubuntu is my favorite too! I have Arch Linux on here. I use Xfce exclusively and it's just like Xubuntu.

This is the best forum out there! Lots of knowledgeable people with various expertises that can help anyone out.

BTW: my hard drive gave me some warnings about the S.M.A.R.T. status of my hard drive.
My daughter got me a new hard drive for Christmas a few years ago.
I bought a drive clone box and it absolutely copied the old one to the new one perfectly.
I think I had to repair grub with a live cd but, every OS on it (about 7-8 at the time) including Windows 7 was exactly as it was.
 
So, this old machine is still kicking since April 2009!

---

### Post by Buntu Bunny on 2016-08-16
sudodus, will do.

Cavsfan, since I want to upgrade to 16.04, would a drive clone still be something useful for me?

---

### Post by sudodus on 2016-08-17
I would recommend a fresh installation rather than a disk clone. A 'compromise' is to keep /home (put it into an own partition).

If you have Windows there are other things to consider. A fresh installation works much better than an old bloated system, but needs a lot of time-consuming work (while a fresh linux installation can be done quickly).

---

### Post by Buntu Bunny on 2016-08-17
That's what I figured. Thanks. :)

---

### Post by Cavsfan on 2016-08-17
> **Buntu Bunny said:**
> sudodus, will do.

Cavsfan, since I want to upgrade to 16.04, would a drive clone still be something useful for me?

If your disk drive is the only thing that is bad. Getting a new drive the same size as the one you have and a Dual Bay Clone Docking Station to clone the old one to a new one should work as it did for me.

I don't have access to the one my daughter bought me as when I login to NewEgg and look at purchase history it does not show up.
But, it was similar to this one: [http://www.newegg.com/Product/Product.aspx?Item=9SIA1DS3CG5700&cm_re=hard_drive_cloner-_-9SIA1DS3CG5700-_-Product](http://www.newegg.com/Product/Product.aspx?Item=9SIA1DS3CG5700&cm_re=hard_drive_cloner-_-9SIA1DS3CG5700-_-Product)

You'll just have to find one that suits your system. Mine is only USB 2.0 compatible so that would not work for me but I know it was like that one.
My wife put it up so I cannot readily find it. It's probably 3 years old though and it did what I asked of it.
**But, do look at all of them and get one that suits your needs USB 2.0 or USB 3.0 whichever one you have and SATA II or SATA II, whatever you need for your system.**

> **sudodus said:**
> I would recommend a fresh installation rather than a disk clone. A 'compromise' is to keep /home (put it into an own partition).

If you have Windows there are other things to consider. A fresh installation works much better than an old bloated system, but needs a lot of time-consuming work (while a fresh linux installation can be done quickly).

I didn't mean a software disk clone I meant hardware to duplicate what she has on the old disk to a brand new one, like the one above.

The important thing is getting a new drive and the Hard Drive Duplicator/Clone Function box and then it will be just the exact same as it was on the old hard drive.
Or a new PC if it is time to upgrade to a new one.
Then she can do a fresh install of 16.04.1, which is what I did last week.

---

