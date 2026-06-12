---
title: "Mounting disk"
date: 2007-05-22
forum: General Help
---

### Post by Eric the Red on 2007-05-22
I have linux on the sda2 and Windows Xp on the sda1 so in order to mount the xp file system in Ubuntu I did 

sudo su -
mount /dev/sda1 /mnt
cd /mnt 

and voila I can see the files. The only problem is that when I try copying a file for example 

cd /mnt
cd "Documents and Settings" 
cp thefile.zip /home/matt 

it copied to that location fine "through a terminal". HOWEVER, I can't view, open, send or write to the file. What the heck is going on?? is this file still mounted in /home/matt? I did:

ls -al 

and I noticed that the file was 'read only' so I did:

chmod 775 thefile.zip 

However, it didn't seem to fix anything. 

Note: if I look at the icon of the file in its pasted location "/home/matt" I noticed that there's a red "X" on the icon and a "lock" symbol on the icon. 

What is going on did I mount this driver correctly?

---

### Post by vtel57 on 2007-05-23
You mounted and accessed the partition with temporary Root priveleges (sudo), so when you acted on the file (copied it), you were effectively Root. When you go back to regular user, you can't view that file because it belongs to Root. Try:

```
 $ sudo chown -R <your regular user name> <the file name>
```

Don't type the < and >. They're there to let you know that you have to fill in the blank with the proper information.

What you're doing with this command is changing the ownership of the file/directory to your user from Root.

Luck! :)

---

### Post by elpichi on 2007-05-23
umm i had a similar problem until a friend suggested me to install ntfs configuration tool which lets you read/write/delete/ files from ubuntu to filesystems like fat32/ntfs(in your case windows?) etc, 
[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)
and it also mounts drives at bootup

---

### Post by Eric the Red on 2007-05-23
Thanks both of you. 

Vtel your solution worked perfectly.

---

### Post by Eric the Red on 2007-05-23
If I were to delete file on my windows partition through Ubuntu.. would that be considered "Risky Business"??

Should I only be reading the files?

---

### Post by vtel57 on 2007-05-23
There are differences of opinion on this in the GNU/Linux community, Eric. A lot of old timers will tell you that attempting to write to NTFS from Linux is probably **not** a good idea, if you value the data on the NTFS partition. However, on the other hand... I'm reading a lot of good reviews about ntfs-3g drivers that allow Linux to rwx on NTFS volumes. The distribution Mepis actually comes out-of-the-box with this feature. Read some forums. Ask some opinions. After that, make your informed decision. Personally, I don't need to write to my NTFS partition. I only have Windows installed on my system for games. Beyond that, it never gets booted.

Have FUN! :)

~Eric

---

### Post by hartz on 2007-05-23
Some comments:

The chown command takes the new owner first, then the list of files to act on.

The -R option is to change a directory and all of its subdirectories (Recursively)

---

### Post by vtel57 on 2007-05-23
Ooops! A typo on my part. You're absolutely correct. I used the recursive command in the example above because I didn't know whether the poster was working with a single file or a directory.

From the manual:

> chown [OPTION]... [OWNER][:[GROUP]] FILE...

Edited the above post to correct this.

Thanks,

~Eric

---

### Post by Eric the Red on 2007-05-23
not a prob, I just did "man chown" and voila.

---

### Post by vtel57 on 2007-05-23
Woo-hoo! Someone who thinks for himself! That'll come in handy learning GNU/Linux, my friend! :)

Luck to you!

~Eric

---

