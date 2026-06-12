---
title: "Creaks hard drive."
date: 2015-04-21
forum: General Help
---

### Post by Vladimir1989 on 2015-04-21
Hello! Prompt, please, in what may be the problem. On laptop installed windows and ubuntu, but when ubuntu hard disk is very much cracking, under windows there is no such thing. What could this mean? Thank you.

---

### Post by dragonfly41 on 2015-04-21
By "creaking" do you mean "noisy" or "clicking"?

Start by searching for "noisy drive dual boot" for possible explanations.

Here is one ...

[http://askubuntu.com/questions/583621/linux-is-making-much-more-hard-disk-noise-than-windows-7-on-laptop](http://askubuntu.com/questions/583621/linux-is-making-much-more-hard-disk-noise-than-windows-7-on-laptop)

Do you have swap partition? Publish here your partitions layout.

---

### Post by Vladimir1989 on 2015-04-22
&#1060;&#1072;&#1081;&#1083;.&#1089;&#1080;&#1089;&#1090;&#1077;&#1084;&#1072;   &#1056;&#1072;&#1079;&#1084;&#1077;&#1088; &#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1086;  &#1044;&#1086;&#1089;&#1090; &#1048;&#1089;&#1087;&#1086;&#1083;&#1100;&#1079;&#1086;&#1074;&#1072;&#1085;&#1086;% C&#1084;&#1086;&#1085;&#1090;&#1080;&#1088;&#1086;&#1074;&#1072;&#1085;&#1086; &#1074;
/dev/sda7         14G         4,5G  8,5G           35% /
none             4,0K            0  4,0K            0% /sys/fs/cgroup
udev             428M         4,0K  428M            1% /dev
tmpfs             88M         1,2M   87M            2% /run
none             5,0M            0  5,0M            0% /run/lock
none             438M          12M  426M            3% /run/shm
none             100M          64K  100M            1% /run/user
/dev/sda8        9,3G         108M  8,7G            2% /home
Hello! The sound is reminiscent of a hard crunch, as if the hard drive scrape with something sharp.

---

### Post by J_Me on 2015-04-22
> Hello! The sound is reminiscent of a hard crunch, as if the hard drive scrape with something sharp.You should stop using that drive/laptop immediately. The drive is failing.

---

### Post by Vladimir1989 on 2015-04-22
Why windows 7 on the same laptop, this phenomenon is not?

---

### Post by dragonfly41 on 2015-04-22
In the thread I posted is this (possible) explanation .

> 
First of all: this is a hardware issue.  On the inside of the hard disk,  bits are packed more densely then on the outside of the hard disk, so  the noise is different.  (And just by your description, *without hearing the noise* I can deduce that Ubuntu is on the *outside* of the disk)


I agree that you should stop using the drive and later you can try to recover data from the drive placed in a USB container and analysed by a LiveUSB OS.

---

### Post by RobGoss on 2015-04-22
Sounds like a hardware failure How old is the machine?

---

### Post by Vladimir1989 on 2015-04-22
Laptop Dell  inspiron 1501 2005-2006 year. 
I have another external hard drive to 160 gigabytes, if I install ubuntu on it there is a probability of such failures?

---

### Post by dragonfly41 on 2015-04-22
I have Dell Inspiron 1720 laptop same vintage year and I have had to replace drives several times on this and other other old platforms.

It is a fact of life that there will be failures. Plan to expect this.

Probability of failure is difficult to assess.

---

### Post by Vladimir1989 on 2015-04-22
Do you think that if you add RAM, then the problem goes away?

---

### Post by dragonfly41 on 2015-04-22
Short answer is no.  Although this might reduce stress on the drive it is the drive which is probably on its way to eventually failing.   Use its remaining life to extract any important data to a fresh drive.

You can try creating a LiveUSB to run Ubuntu and you will find that the drive is probably quieter.

You can investigate the internal drive with some commands  ..

====================
sudo apt-get install udisks

sudo udisks --show-info /dev/sda
====================
sudo apt-get install smartmontools

sudo smartctl -i /dev/sda
====================
sudo apt-get install lshw 

sudo lshw -class disk -class storage
====================
sudo apt-get install badblocks

sudo badblocks -help
====================


[later edit]

This site might help to pinpoint the "sound".

[http://datacent.com/hard_drive_sounds.php](http://datacent.com/hard_drive_sounds.php)

---

### Post by RobGoss on 2015-04-22
Sometimes when installing different distributions not all of them will run smoothly it is good practice to try different flavors to see which one is right for that particular machine. In fact some distribution may not even booth up the first time you try to install it.

---

### Post by RobGoss on 2015-04-22
> **Vladimir1989 said:**
> Laptop Dell  inspiron 1501 2005-2006 year. 
I have another external hard drive to 160 gigabytes, if I install ubuntu on it there is a probability of such failures?

Well its doesn't seem that old I'm running Lubuntu on a 14 year old Dell 2400 and its runs fine I mean its not the fastest machine I have but workable.

---

### Post by RobGoss on 2015-04-22
To be honest I don't think the ram will cause your machine to make noise as you stated, maybe a hard drive or a CD ROM on its way out.

---

### Post by Vladimir1989 on 2015-04-22
[TABLE="class: b-layout-table b-layout-table_layout_47-47, width: 1163"]
[TR="class: b-layout-table__row"]
[TD="class: b-layout-table__cell b-layout-table__cell_position_r"][COLOR=#222222][FONT=Arial]The swap partition should go first or be in the middle, between the root and home? And does it matter when crunches the hard drive crunch?[/FONT][/COLOR]


[/TD]
[/TR]
[/TABLE]

---

### Post by pmi2 on 2015-04-22
> **Vladimir1989 said:**
> Why windows 7 on the same laptop, this phenomenon is not?Windows and Ubuntu are installed on different partitions, this means different parts of the same disk drive (different concentric tracks or "cylinders").  This is also true about the Ubuntu swap file.  

So it is possible that when the operating system is accessing those parts of the disk where Ubuntu is installed, there is some kind of problem.

There are various things you can do to test for a bad disk.  

The simplest one is using the Ubuntu "Disks" utility to look at the stored disk attributes (SMART).  The next simplest is to download GSmarControl (from the Ubuntu Software Center) and run the built-in disk tests.  There are three of them, Short, "Conveyance", and Long.  GSmartControl also gives you access to any logged errors that may have occurred in the past, with details that will help you decide what to do next.

Finally you can download any one of several more thorough disk tests which run from a live CD/DVD, without booting Ubuntu or Windows.  There can take a long time to run, and require booting from a CD/DVD or a USB stick.

Here is a link to some third party tools you can use to test your disk drive:

[http://pcsupport.about.com/od/toolsofthetrade/tp/tophddiag.htm](http://pcsupport.about.com/od/toolsofthetrade/tp/tophddiag.htm)

If you suspect a disk is going bad, but still working, you can almost always test it and confirm the problem.

---

