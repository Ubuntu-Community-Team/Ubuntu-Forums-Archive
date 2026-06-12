---
title: "Error in many applications with Python"
date: 2007-10-18
forum: General Help
---

### Post by troorl on 2007-10-18
Hi.
I have a problem. Every time I'm starting python's applications, that uses GTK, they write same error:
```
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 28, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_get_scaled_font
```
It's appears in many programms, in update-manager for example. I try to reinstall all pythons librarys with GTK and cairo bindings. What's wrong? :(

P.S. Ubuntu Gutsy 7.10 with fresh updates

and sorry for my English)

---

### Post by sttop on 2007-10-20
i'm getting the exact same error. i can't open software sources, restricted drivers manager, advanced desktop effects settings and other applications. anyone knows how to fix it?


```
victor@Home:~$ /usr/bin/software-properties-gtk
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 27, in <module>
    import gtk
  File "/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py", line 48, in <module>
    from gtk import _gtk
  File "/usr/lib/python2.5/site-packages/cairo/__init__.py", line 1, in <module>
    from _cairo import *
ImportError: /usr/lib/python2.5/site-packages/cairo/_cairo.so: undefined symbol: cairo_clip_extents

```

---

### Post by nrune on 2007-10-21
Yep same issue, no clue. have reinstalled gtk and python.  Considering doing a clean install

Mike

---

### Post by waltervalderrama on 2007-10-21
Same problem, I am dissapointed with Gutsy, one advantage of linux is that you keep upgrading without reinstalling..... I think I am going to reinstall everything, because neither automatix works

---

### Post by troorl on 2007-10-28
Any ideas?

---

### Post by TRDownShift on 2007-10-30
eh, I'm having the same prob, and wen i did some looking i found one guy who said if you delete everything in the lib folder and run some command like "ldconfg" or something, can't remember, it will fix it, but to me that just sounds like your going to wipe out all the dependencies for all your app's and then NOTHING will work so i haven't tryed it yet...

---

### Post by waltervalderrama on 2007-10-30
I had to reinstall everything. I have a separated /home partition, so all my files are there. Clean installation works perfectly

---

### Post by TRDownShift on 2007-10-30
> **waltervalderrama said:**
> I had to reinstall everything. I have a separated /home partition, so all my files are there. Clean installation works perfectly

is there a way to make that /home partition right now so i can back up all my crap.... cus the last thing i wanna do is lose all my stuff right now... T.T 

i mean i've got 800+ songs on stepmania and tons of themes and wallpaper that i don't even remember where they came from, and it really blows becus im going to lose all my settings and stuff along thoughs  lines, most of the time i could just back everything up to DVD's but right now becus of this bug my computer won't burn anything :(

---

### Post by waltervalderrama on 2007-10-31
There is an app called "gparted" just apt-get it. There you can graphically edit your partitions.

---

### Post by TRDownShift on 2007-10-31
And once i get that how do i set ubuntu to use the new partition as my home folder, also how would i move my corrent home folder into that partition so i dont lose all my stuff?

would it be anything like naming the partition "Home" and then mount it and drag and drop? then maybe on the new install theres so way to mount the home partition as the home folder? (oh and if i got any of this right your going to have to tell me step by step cus i don't even know how to mount things yet in the terminal T.T)

---

### Post by waltervalderrama on 2007-10-31
You have to mount the new partition to a folder. For example, I have my /etc/fstab file like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=c7bf9376-b07e-4b68-a500-e04e05fef3e0 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=2e7a66af-47c1-43eb-a248-361b0e00aa27 /home           ext3    defaults        0       2
# /dev/sda1
UUID=C8987CC1987CAF94 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=4566-5F44  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=807d5c8d-6568-4b90-b97a-b113ddacddc9 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Where sda3 is mounted as /home. You can do something similar. Edit your /etc/fstab file and assign it as /home/something/ (you have to create that folder). After doing that type sudo mount -a
Now you can copy all your data.

Good luck

---

### Post by troorl on 2007-10-31
but problem wasn't fixed...

---

### Post by ijustam on 2007-11-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/libcairo/+bug/129816](https://bugs.launchpad.net/libcairo/+bug/129816) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is how I, and others, fixed it:
[LIST=1]
[*]Back up your /usr/local/lib directory: **cp -R /usr/local/lib $HOME/bak/lib**
[*]Delete the original directory: **sudo  rm -r /usr/local/lib**
[*]Run this command: **sudo ldconfig**
[/LIST]

Should work now :)

---

