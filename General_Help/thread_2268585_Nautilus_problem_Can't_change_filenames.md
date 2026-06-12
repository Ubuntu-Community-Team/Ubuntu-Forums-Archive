---
title: "Nautilus problem: Can't change filenames"
date: 2015-03-09
forum: General Help
---

### Post by Krabun on 2015-03-09
When I want to rename a filename and try to type nothing happens, also the in the search bar it's not possible to type. I can copy/move files or extract rar-files. I have read & write permissions.
Is there a way to reinstall Nautilus?

---

### Post by yancek on 2015-03-09
How exactly are you trying to rename the file(s), what command?  Are these files in your /home/user directory?  Elsewhere and if so are you using sudo?  Have you tried the mv command which accomplishes the same thing?

---

### Post by Krabun on 2015-03-09
I use the option 'rename' from the right click menu. The files are in my homedirectory and on ntfs partitions. The mv command works but I don't want to use the terminal to change names.

---

### Post by ajgreeny on 2015-03-10
You certainly should be able to rename files on both partitions, assuming the NTFS partition is mounted as it would be normally with an extra line in /etc/fstab.

Can we see the output of **cat /etc/fstab** in terminal please, as that could be the problem with the NTFS partition.
Can you also show us the output of **ls -l *<filename*>** for one of these files in your home that the file-manager will not allow you to rename just to be sure it does belong to you and is not owned by another user or root.

---

### Post by Krabun on 2015-03-10
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda13 during installation
UUID=XXXXXXXXXXXXXXXXXXXX /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda12 during installation
UUID=XXXXXXXXXXXXXXXXX none            swap    sw       

-rw------- 1 test test

---

### Post by ajgreeny on 2015-03-10
Two comments to make.
[LIST=1]
[*]You do not mount the NTFS partition using /etc/fstab, so I presume you do so by double clicking on the icon for it in your file-manager.  It is a long time since I have used an NTFS partition and I am no longer certain of the default permissions if you mount it that way, so it may be better to use fstab to mount it at boot if it is always present and not an external drive partition. 
[*]If your username is test, the owner of the unnamed file for which you show permissions, you should be able to rename it without problem.  Is that file on anNTFS partition or in your /home? 
[/LIST]

What exactly do you mean by your comment that when you try to type nothing happens?

---

### Post by Krabun on 2015-03-10
1. I mount the ntfs partition by clicking. How exactly does it work with fstab?

2. I am the owner of the file, I just changed the name. The file is on a my home directory.

It means that there's no output when I type. Also the Enter-key doesn't work, only the escape-key.
The strange thing is that when I start Nautilus I can change names or enter a search term for 2 or 3 times, then it suddenly stops. 
Another thing is that there are 2 copies of two ntfs partitions; backup & backup1 and multimedia & multimedia1. Backup & multimedia: owner root, backup1 and multimedia1: owner me.

---

### Post by yancek on 2015-03-10
You should be able to read/write/delete anything in your /home/username directory.  One exception would be if you copied a file to your /home/username directory and didn't change permissions.  You should not generally be able to change anything in the /home directory or any other system directories.

> 
It means that there's no output when I type. Also the Enter-key doesn't work, only the escape-key.

If you use the rename or mv commands, there is no output in a terminal.  Sounds like a problem with your keyboard if the Enter key doesn't work.  Is this when you right-click and select rename and change the name?

If you have windows/ntfs data partitions, you can write to them but you need to set permissions and I would not expect a default to be to write.  You will probably want to set an entry in fstab and you need to set umask permissions as standard Linux permissions aren't applicable on ntfs.  What exactly do you want?  Do you want your user to be able read/write to all four partitions.  Not sure about the partitions, you indicate there are two but your list four?

---

### Post by Krabun on 2015-03-10
The keyboard is not the problem, it functions everywhere else. With no output I'm only referring to nautilus, not the terminal. 
> Is this when you right-click and select rename and change the name?  Yes.

I'm the only one who uses the computer, so I have read/write rights. But it's not a matter of rights because if that were the case, I wouldn't be able to delete files. 
I have 6 ntfs partitions and 2 of them appear double in Nautilus, the ones I mentioned before (backup & multimedia).
Can you tell me if it is possible to reinstall nautilus and how.

---

