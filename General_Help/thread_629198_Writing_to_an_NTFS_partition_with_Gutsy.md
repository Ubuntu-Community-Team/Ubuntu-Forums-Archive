---
title: "Writing to an NTFS partition with Gutsy"
date: 2007-12-02
forum: General Help
---

### Post by w00t1138 on 2007-12-02
I'm very new to Ubuntu and I have a small question.  I want to make absolutely  sure that it is safe to write to a separate drive that's in NTFS format.  I knew you had to install a certain package to do this in Feisty, but I just want to make sure there weren't any settings to change in Gutsy before I could do so.

---

### Post by Cresho on 2007-12-02
from what I know and tested, gutsy is more stable than feisty.  you can auto mount the partition by adding some lines in the fstab for bootup purpouses.  or When you mount the ntfs (just click on the winxp drive and enter password), you have immediate access to the files.  you can copy and read but you cannot write to that drive until you give yourself permission.  One way I have total access to the drive is through the auto initiation of the fstab.  the other way is mannually mounting the drive and sudo nautilus in the terminal  right click on the folder you want access and give yourself permission.  Not sure what others around here do but I hope I got you started.

---

### Post by w00t1138 on 2007-12-04
Thanks for the response! Whenever I clicked on the drive it would ask for my security password and then mount it.  After that I was able to write files to it with no problem.  But about auto-mounting the drive at startup, how do I edit fstab so it auto-mounts?

---

### Post by Cresho on 2007-12-07
Now this was tricky for me since i am a total newbie.  In the terminal, you bring up the "g editor" a.k.a. text editor in as root. with this command "sudo gedit"   and navigate yourself to /etc/fstab or in one shot, use this command to edit fstab

sudo gedit /etc/fstab

Now you have the fstab right infront of you.  if you look at the third line, it gives you info such as

<file system> <mount point>   <type>  <options>       <dump>  <pass>
  proc               /proc                 proc      defaults           0             0

but what you really need to know is where the drive (filesystem) is at and where it is mounted.

this is the one I use for windows xp
/dev/sdb1       /media/WinXP       auto    defaults,user,rw               0 0

this is how I did it and I know its not the appropriate way to figure out the mounts.  After you mount your drive, open up a second terminal and type df and enter.  look low and you will see a /dev/sdbsomething and where it is mounted.  just plug the filesystem and the mountpoint into the line i use as an example like the 
/dev/sdb1       /media/WinXP       auto    defaults,user,rw               0 0

and save it at the bottom of the list like my list.


/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
/dev/sdb1       /media/WinXP       auto    defaults,user,rw               0 0
/dev/hdb5       /media/Music        auto    defaults,user,rw               0 0


dont forget to save the file

---

