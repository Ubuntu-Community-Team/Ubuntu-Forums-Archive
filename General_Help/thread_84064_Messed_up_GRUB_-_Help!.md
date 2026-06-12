---
title: "Messed up GRUB - Help!"
date: 2005-10-30
forum: General Help
---

### Post by canadianwriterman on 2005-10-30
I tried installing a GRUB splast screen by adding a line to menu.lst. Now, when I boot I get a black screen and can't go anywhere. I'm using a Knoppix live CD to send the post. I tried editing the line out of menu.lst through the Knoppix live CD, but I can's save the editing file because I don't have permission. How do I get myself out of this without having to totally reinstall Ubuntu?

Thanks for your help.

---

### Post by Xian on 2005-10-30
[QUOTE=canadianwriterman]I tried editing the line out of menu.lst through the Knoppix live CD, but I can's save the editing file because I don't have permission.[/QUOTE]
You need to mount the partition as read-write:

```
# mount -o remount -rw /dev/hdax
```

---

### Post by canadianwriterman on 2005-10-30
[QUOTE=Xian]You need to mount the partition as read-write:

```
# mount -o remount -rw /dev/hdax
```[/QUOTE]

Okay, I did this through the terminal in my live session of Knoppix to no avail. menu.list is on hdb, so I changed "hdax" to "hdbx".

Then, still in my live Knoppix session, I opened Kwrite and tried to edit menu.lst, but I still don't have permission to save the file.

---

### Post by Xian on 2005-10-30
[QUOTE=canadianwriterman]Okay, I did this through the terminal in my live session of Knoppix to no avail. menu.list is on hdb, so I changed "hdax" to "hdbx".[/QUOTE]
Did you replace 'x' with your partition number, i.e. hdb3 or hdb2?
Check to see where knoppix has that partition mounted.

You can use the directory in that command as well.

$ mount

---

### Post by canadianwriterman on 2005-10-30
[QUOTE=Xian]Did you replace 'x' with your partition number, i.e. hdb3 or hdb2?
Check to see where knoppix has that partition mounted.

You can use the directory in that command as well.

$ mount[/QUOTE]

Knoppix shows it as hdb1. I retried the command, but it doesn't seem to do anything. I went back into Kwrite and I still don't have permission to save the file.  Here's the terminal output:

knoppix@ttyp0[knoppix]$ # mount -o remount -rw /dev/hdb1
knoppix@ttyp0[knoppix]$

Is there anyway to boot my machine into Ubuntu by bypassing GRUB?

---

### Post by Xian on 2005-10-30
Create somewhere to mount the partition.
Maybe that is the problem.

# umount /dev/hdb1
# mount -rw /dev/hdb1 /mnt/hdb1

Then again, you may rather to simply [Restore Grub](http://www.ubuntuforums.org/showthread.php?t=24113).

---

### Post by canadianwriterman on 2005-10-30
Thanks for your help, Xian. Unfortunately, nothing worked. The parition was already mounted and GRUB was fine, it was just that I needed to edit menu.lst and couldn't get permission.

I ended up doing a complete reinstall of Ubuntu.

---

