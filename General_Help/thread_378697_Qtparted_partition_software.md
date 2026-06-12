---
title: "Qtparted partition software"
date: 2007-03-07
forum: General Help
---

### Post by stchman on 2007-03-07
Hello all, I was messing around with qtparted and I gather that the software is still pretty buggy.  I tried to reformat a USB key and it just wont work.  The program hangs.

The command line partitioner is very confusing.  I have found a third reason to keep a windows machine around after games and excel.

Can anyone give me a tutorial on drive partition editing under Ubuntu.  With XP the disk manager made it an absolute snap.

Are there any freeware type packages for Ubuntu that make disk management a snap?

Thanks

---

### Post by jimbob on 2007-03-07
Download and burn the Gparted standalone CD.

IMHO it is a much better partitioning and formatting tool.

Google for the website.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by laidback on 2007-03-07
Have you tried Gparted, it's usually in Systems>Administrator>Gnome partition editor. I haven't partitioned a usb there yet but it has worked well for me for hd's.

If it isn't available there it's in Synaptic, so dowload and install it.

(I'm using Dapper)

If you're able to download as jimbob suggests then that's even better.

---

### Post by bodhi.zazen on 2007-03-07
gparted :

Documentation: [Documentation](http://gparted.sourceforge.net/documentation.php)

Download: [Download Gparted](http://sourceforge.net/project/downloading.php?groupname=gparted&filename=gparted-livecd-0.3.3-7.iso&use_mirror=osdn)


To format your usb : [http://www.ubuntuforums.org/showthread.php?t=302724](http://www.ubuntuforums.org/showthread.php?t=302724)

If you like that kind of thing ;)

---

### Post by stchman on 2007-03-08
> **jimbob said:**
> Download and burn the Gparted standalone CD.

IMHO it is a much better partitioning and formatting tool.

Google for the website.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

I want to be able to add and delete partitions while Ubuntu is running.  Of course I realize that I cannot delete the primary partition that Ubuntu is running on.  As far as resizing partitions, I would have to boot up a stand alone CD to do that.

Basically I just want to be able to delete, add, format, delete and format to different filesystems (FAT, FAT32, EXT2, EXT3).

Thanks

---

### Post by jimbob on 2007-03-08
Gparted will let you do anything you want on any partitions you want from Ubuntu as long as they are not mounted.

apt-get install Gparted
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by stchman on 2007-03-08
> **jimbob said:**
> Gparted will let you do anything you want on any partitions you want from Ubuntu as long as they are not mounted.

apt-get install Gparted
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]


Cool I will try that.  qtparted seems too buggy.

Thanks

---

