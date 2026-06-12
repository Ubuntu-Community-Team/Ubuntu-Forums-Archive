---
title: "Need Help Raid on MSI K9A2 Platinum"
date: 2008-05-27
forum: General Help
---

### Post by qbasasa on 2008-05-27
Hello i cant get to work My raid Drives that i use on Windows
My main board is [Msi K9A2 Platinum]("http://global.msi.com.tw/index.php?func=proddesc&prod_no=1332&maincat_no=1&cat2_no=171")

Raid 0 
2x Some 320gb hd's
Connected to Promise controller on The mainboard I made raid using some bios toll

DmRaid Dont see the device 

I cant find any signs in ubuntu that there are any Drives besides the system one <20gb old junk>

Can anyone help me solve  this

---

### Post by fjgaude on 2008-05-27
You can't boot raid0 without having a driver installed before the OS tries to load. dmraid only works after the OS is loaded. You can see under Ubuntu the stripped drives.

Now if you can load the OS on a single drive then dmraid will see the raid0 pair of drives.

Using the old drive, do this:

```
sudo dmraid -tay
```

Then you can mount the raid pair using the now known /dev/mapper/<letters> for it.

---

### Post by qbasasa on 2008-05-27
I have the ubuntu on 20gb drive But I can't find any drivers for Raid and no mater what dmraid switch I use it  always says "No RAID disks"

---

### Post by fjgaude on 2008-05-27
What version of Ubuntu are you using?

What does

```
sudo fdisk -l
```

show?

---

### Post by qbasasa on 2008-05-27
Ubuntu 8.04
<ubuntu-8.04-desktop-i386.iso>

Nope :\


```

--@--:~$ sudo fdisk -l
[sudo] password for --: 

Disk /dev/sda: 20.4 GB, 20485785600 bytes
255 heads, 63 sectors/track, 2490 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5319575f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         669     5373711   83  Linux
/dev/sda2             670         791      979965   82  Linux swap / Solaris
/dev/sda3             792        2490    13647217+  83  Linux

```

---

### Post by fjgaude on 2008-05-27
Strange, the individual drives don't show... they should have even if they are in a raid array. Something is not right.

Can't think of anything to suggest...

---

### Post by qbasasa on 2008-05-28
Then What should i say im new to ubuntu :P
Maybe it need some new drivers but i could not compile the ones i found.

I foun WebPage with Driver but i cant compile :\
If anyone could help me
[http://www.promise.com/support/download/download2_eng.asp?productId=191&category=driver&os=4&go=GO](http://www.promise.com/support/download/download2_eng.asp?productId=191&category=driver&os=4&go=GO)

---

### Post by fjgaude on 2008-05-28
If the drivers are not for Linux then they are not for Ubuntu. You should be able to see the two drives using fdisk in any event.

---

### Post by qbasasa on 2008-05-28
They Are for linux but i dont uderstand what Readme from them say there are packages for suse and some other distro on webpage

---

### Post by fjgaude on 2008-05-28
I don't think I can be of any assistance. So much to learn...

You need a .deb package to install in Ubuntu.

---

### Post by qbasasa on 2008-05-28
About dmraid:
```
--@--:~$ sudo dmraid -ay
No RAID disks

--@--:~$ sudo dmraid -ay -vvv -d
WARN: locking /var/lock/dmraid/.lock
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: /dev/sda: via     discovering
No RAID disks

--@--:~$ sudo dmraid -b         
/dev/sda:     40011300 total, "7EJ0ZQQ1"

--@--:~$ sudo dmraid -rD
No RAID disks
```

---

### Post by keasley on 2008-06-04
I believe this will help.

Read the whole thread.  Should give some insight on how to get the promise raid up and running.

[http://www.linuxquestions.org/questions/slackware-14/drivers-for-promise-pdc42819-raid-controller-on-msi-k9a2-platinum-motherboard-621818/]("http://www.linuxquestions.org/questions/slackware-14/drivers-for-promise-pdc42819-raid-controller-on-msi-k9a2-platinum-motherboard-621818/")

---

### Post by cariboo on 2008-06-05
I used this

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

It was quite easy to get raid running. Mind you it's been about a year since I set it up and I've basically just forgotten about it. No problems at all.

JIm

---

