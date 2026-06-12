---
title: "Mounted windows partition only root (Solved)"
date: 2005-10-27
forum: General Help
---

### Post by 3dmaker on 2005-10-27
How can I accesss my windows partition without me having to login as root? Or do sudo /bin/su? I want it so I can double click the icon on my desktop and it will allow me to access it. Not say Permession Denied.

---

### Post by Appolusionist on 2005-10-27
[QUOTE=3dmaker]How can I accesss my windows partition without me having to login as root? Or do sudo /bin/su? I want it so I can double click the icon on my desktop and it will allow me to access it. Not say Permession Denied.[/QUOTE]
Take a look at this [article]("https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions") in the Ubuntu Wiki. This will show you how to have your Windows partition to mount automatically for you.

---

### Post by 3dmaker on 2005-10-27
I know how to auto mount it. My question is how do I make it so that not only use root can view the drive.

---

### Post by budluva04 on 2005-10-27
chown ?

---

### Post by 3dmaker on 2005-10-27
What?

---

### Post by Mustard on 2005-10-27
I'm missing the point with this question.  If you have followed the wiki guide that was given then you should be able to browse the contents of you other drives from your user account.  I have never had to log in as root to read my other drives.  Something is amiss. :)

---

### Post by soulestream on 2005-10-27
you just need to add umask=000 to your /etc/fstab line for your windows, this will give all users full r/w access to your other partition. 

Dont do this if you have your windows drive formatted NTFS as you dont want to write to it, bad things happen


if its ntfs then you will need to change to another umask setting. man umask


soule

---

### Post by 3dmaker on 2005-10-27
It is NTFS. So i can tdo umask
man umask
No manual entry for umask

---

### Post by psyguy92 on 2005-10-27
The guide pointed to above is good.  Another great place to look is here:
[http://linux-ntfs.sourceforge.net/info/ntfs.html#4.0](http://linux-ntfs.sourceforge.net/info/ntfs.html#4.0)

It is much more detailed and technical, but very informative :)

For a shorter version, do this:

1.
[PHP]cat /proc/filesystems[/PHP]
If you see ntfs anywhere, you can read ntfs (windows xp default filesystem).
If you can't, please read documentation at [http://linux-ntfs.sourceforge.net](http://linux-ntfs.sourceforge.net)  

2.
[PHP]fdisk -l[/PHP]
You will see output showing you which device is of type ntfs.  Note which one.
It could be /dev/hda1 /dev/hda2 /dev/sda1 /dev/sda2 or many others.  NB: where you read fdisk -l, that is the letter L, not the number one.

3.
[PHP]sudo mkdir /mnt/windows[/PHP]
You need a mountpoint.  This is a place where the windows partition is to be accessed from.  Think of it as a 'shortcut' folder.

4.
[PHP]sudo mount /dev/hda1 /mnt/windows -t ntfs -r -o umask=0222, uid=1000[/PHP]
Here we mount the volume.  NB: Change hda1 to whatever you noted in step 2.
Also, uid=1000 could be substituted with your login name.  Mine reads uid=psyguy92   
The -t means type.  The -r means mount as read-only -- we can't write to ntfs at this time, at least not safely.   The -o is specifying an option - we are using uid (user id) as an option.   The umask is like the chmod command in reverse.  0222 lets everyone read and execute (but NOT write!) everything on the windows partition.  Reasonable perhaps, but you might want to familiarize yourself with security ;)

If you want to automount, see the guide I mentioned.

I'm pretty sure all of this is correct.  It's what I've learned from going through the guide I mention at the top of this post.  Good luck!

psyguy92

---

### Post by aysiu on 2005-10-28
What's wrong with [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)?

---

### Post by 3dmaker on 2005-10-28
So, if my FSTAB says this

/dev/hda1       /media/hda1     ntfs    defaults        0       0

Where do I put in the umask?

---

### Post by 3dmaker on 2005-10-28
[QUOTE=aysiu]What's wrong with [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)?[/QUOTE]
Thank you! It works great!

---

### Post by psyguy92 on 2005-10-28
[QUOTE=aysiu]What's wrong with [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)?[/QUOTE]

Nothing I'd guess. As long as /dev/hda1 is correct.  Mine is not there, so that guide wouldn't work if I didn't know what that line meant or how to find the correct info.

psyguy92

---

