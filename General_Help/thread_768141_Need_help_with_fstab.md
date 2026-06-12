---
title: "Need help with fstab"
date: 2008-04-26
forum: General Help
---

### Post by Vivaldi Gloria on 2008-04-26
Hello guys. I installed Hardy successfully and after the installation I added my other hard disks as follows:

 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# 
UUID=b29710d6-798f-4768-935d-72e015a7dcb1 /               ext3    relatime,errors=remount-ro 0       1
# 
UUID=23c3121d-cbec-4beb-8d6e-80def281abb7 /home           ext3    relatime        0       2
# 
UUID=2e9eed51-91a7-40c2-938b-d76b0a4a957f none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# 
UUID=d6370ab8-d3cc-4e6e-bbad-a6b069e5ed78 /home/hasan2718/belge          ext3  rw  0 3
# 
UUID=cf00790e-75ae-4fbe-94d1-53a5c40e21bc /home/hasan2718/musiki         ext3  rw  0 4
# 
UUID=c34bd1af-38e3-4ea8-a806-8cad5686fa38 /home/hasan2718/video/video1   ext3  rw  0 5
# 
UUID=474d93d3-1026-4553-903c-11bcbf84d226 /home/hasan2718/video/video2   ext3  rw  0 6
# 
UUID=6ba52cdb-e0b1-47df-9fd2-cc9167d96fc0 /home/hasan2718/video/video3   ext3  rw  0 7
# 
UUID=425a54d6-7033-4114-b0e6-868257abd717 /mnt/bavul                     ext3  rw  0 8
# 
UUID=10bcf226-8573-4f98-a471-394e57aedd5f /mnt/yedek                     ext3  rw  0 9
```

All those lines below /dev/scd0 are added by me after the installation and they worked perfectly OK with Gutsy. But now I have a problem with them in Hardy. All the disks are mounted at the mount points that I want, but there are also drive icons for them on my desktop. 

How can I get rid of those icons on my desktop?

Help appreciated.

---

### Post by nquinnathome1 on 2008-04-26
Don't mount them in your /home/username directory - I've not tried it extensively, but I had a similar problem and mounted all my other drives/remote folders in another folder on the root of my drive (/myfoldername/..mounts here...).

This solved the problem of them appearing on the desktop; just add launchers or symlink them.

---

### Post by sdennie on 2008-04-26
You should fire up gconf-editor and navigate to /apps/nautilus/desktop.  I believe that disabling volumes_visible will do what you want.

---

### Post by nquinnathome1 on 2008-04-26
> **vor said:**
> You should fire up gconf-editor and navigate to /apps/nautilus/desktop.  I believe that disabling volumes_visible will do what you want.

The above will also work but it will **also** prevent you having removable disks/CD/DVDs from displaying on the desktop. ;)

---

### Post by sdennie on 2008-04-26
> **nquinnathome1 said:**
> The above will also work but it will **also** prevent you having removable disks/CD/DVDs from displaying on the desktop. ;)

That's true.  If you would like removable media to still appear when you plug it in, another thing you could try would be to create a file called ~/Desktop/.hidden and add the names of the things you'd prefer not to see on the desktop.  I haven't tried this method with the Desktop but, it works well in other directories.

---

### Post by Vivaldi Gloria on 2008-04-26
Thanks for the answers guys. 

The ~/Desktop/.hidden idea doesn't work. I am thinking of disabling volumes_visible even if it will prevent removable disks/CD/DVDs appear on the desktop (which I really don't want).

Wasn't it the case that Gutsy (and Feisty) put a desktop icon **ONLY** of the drives mounted to /media/mountpoint? Those did include CDs and removable disks etc. as well as hard disks mounted there. For those mounted to /mnt/mountpoint or ~/mountpoint no desktop icons appeared.

Now it seems that where ever I mount my hard disk, I get a desktop icon. 

I wish there was a way to get the default Gutsy/Feisty behaviour back.

---

### Post by sdennie on 2008-04-26
Yes, I think that in Gutsy udev was less aggressive (or maybe it has to do with the gnome vfs changes).  I manually mounted something in a tmp directory the other day on Hardy and unexpected things occurred.  Unfortunately, I'm not sure if it's possible to make the system more "lazy" when it comes to mounting things.

---

### Post by Vivaldi Gloria on 2008-04-29
I realized that the partitions mounted to /mnt/mountpoint does not generate desktop icons. It was a mistake on my part. 

So the change from Gutsy to Hardy is that now in Hardy  both ~/mountpoint and /media/mountpoint make desktop icons. In Gutsy, ~/mountpoint doesn't generate desktop icons.

Anyway, the question is now settled. If you want to mount a partition without desktop icons then mount it to /mnt/mountpoint and then put a symlink to where ever you want.

---

### Post by QwUo173Hy on 2008-05-08
I had the same problem and I've mounted my drives in /mnt instead as suggested. This removed the icons from the desktop (thank you!), but how do I make a link? When I right-click on any of the folders I've made in /mnt, the "Make Link" option (gnome) is greyed out.

---

### Post by wdaniels on 2008-05-08
> **jarlath said:**
> I had the same problem and I've mounted my drives in /mnt instead as suggested. This removed the icons from the desktop (thank you!), but how do I make a link? When I right-click on any of the folders I've made in /mnt, the "Make Link" option (gnome) is greyed out.

/mnt is probably owned by root, so you would not be able to do it in nautilus that way without privileges.  Just use a terminal command like:

```
ln -s /mnt/something ~/place/to/put/link
```

---

### Post by QwUo173Hy on 2008-05-09
Thanks wdaniels. That works. I thought that because /mnt had root permissions, doing that would give me a folder I couldn't read or write to but that's not the case thankfully.

---

### Post by Vivaldi Gloria on 2008-05-10
Alternatively, press Alt+F2 and run

```
gksudo nautilus
```

Goto your mountpoint in /mnt, right click to properties and then change the ownership from root to yourself. Now you can do whatever you like without a problem.

By the way, you can make a link by dragging the icon with the mouse and pressing the Alt button on the keyboard while dragging and then releasing the icon wherever you want and choosing link from the appearing menu. 

So open two nautilus folders side by side, one with the icon, the other with the place to put the link and then drag from one to other with the above method.

---

