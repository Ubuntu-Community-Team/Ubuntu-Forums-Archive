---
title: "Can't Read Data CD"
date: 2007-08-02
forum: General Help
---

### Post by LesPaulGuy86 on 2007-08-02
I am fairly new to Ubuntu and love it. I'm using 7.04 on a Dell Inspiron 4550 with a 60 gb harddrive and a gig of memory. 

I burned a data CD and put two text files on it, each only 1 KB in size. I used the burner that's in Nautilus, the one that just automatically comes up when you stick in a blank CD. I have not installed any other CD burning programs.

I burned the two text files on the cd. No Ubuntu machines can read it (I've tried two, including the machine that burnt it). I stick it in a windows box and I can access the files and look at them.  How do I get the Ubuntu machine to read it? Every time I try to mount the CD drive, it says there probably isn't any media in the drive.

Any help will be really appreciated.

Thanks!

Jonathan

---

### Post by Mark Phelps on 2007-08-02
When I insert a data CD, a CD icon opens on my Gnome desktop.  I double-click that and the CD opens in Nautilus.

What happens when you insert a data CD?

---

### Post by LesPaulGuy86 on 2007-08-02
When I insert this data CD that I burned, I hear the CD drive spinning and working, then it quits. No icon pops up...nothing. It's just like I opened it and closed it. When I inserted the CD before I burned it (when it was blank) it recognized that it was a blank CD and asked me what kind of CD i'd like to burn.

---

### Post by tsmgroup2 on 2008-03-01
Jonathan's not the only user with this problem.

I am using Ubuntu on three or four systems and have the same problem.  I am using ubuntu 7.10 both the amd 64 and the i386 versions.  Can burn any file known to man on a blank CD, but no reading ability even when drives become mounted.  I can read the burned CD from the same computer that I burned it from, but can't read it on other systems using Ubuntu.  Was really looking forward to completing a business card and letterhead project for a relative of mine, but can't until this data file read problem is resolved.

Wait to hear from you and hope for the best!

Mark
TSM Group 2:confused:

---

### Post by Athelstan101 on 2008-03-01
The problem could be down to the CDs themselves; certain brands / models of CD readers don't cope very well with certain CD-R/W disks.

Try using a different data CD in the drive and see if that works.

To get some more information on what's going on with the 'unreadable' CD, you could open up two terminal windows and in one watch the Kernel messages by typing:
$ sudo cat /proc/kmsg
('CTRL+c' to stop viewing the messages).

In the other terminal window mount the CD dirve manually by typing:
$ sudo mount -t auto /dev/cdrom /mnt/cdrom/

Hope that helps.

---

