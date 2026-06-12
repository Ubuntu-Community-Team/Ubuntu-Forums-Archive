---
title: "Boot problem"
date: 2008-05-30
forum: General Help
---

### Post by OsamaK on 2008-05-30
[I]Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu 8.04, kernel 2.6.24-17-generic
Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
Ubuntu memtest86+
Other operating system:
Microsoft Windows XP Professional[/I]

This thing above is my startup menu, it's too long and include repeated items, with same functions. It was growing each time I upgrade when Ubuntu 8.04 was beta. Also, I installed KDE and XFCE (if they make sense).

Someone on #ubuntu told me to edit **"/boot/grub/menu.lst"**, but it's not editable, I encounter the flowing  problem:
[I][B][SIZE=4]
Could not save the file /boot/grub/menu.lst.[/SIZE][/B][/I]
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by lisati on 2008-05-30
> You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
I had the problem once or twice when editing the menu.lst file - mainly because I'd forgotten to use "sudo"

---

### Post by WRDN on 2008-05-30
You need root privileges before you can edit the menu.lst file.
As lisati said, you can use sudo, or type "su" then the root password.
I wouldn't recommend deleting the entries for the other kernels, incase you need to boot into them in the future. Instead, put a "#" before the word "title" for each you want to remove from the screen at bootup.
That way, you can easily retrieve the entries by removing the "#".

---

### Post by OsamaK on 2008-05-30
Hum, I didn't understand you well. I'm the admin at my computer, and there isn't any user else, Am I a 'root'? If not, how to log-in as  a root? Thanks a lot!

---

### Post by WRDN on 2008-05-30
> **OsamaK said:**
> Hum, I didn't understand you well. I'm the admin at my computer, and there isn't any user else, Am I a 'root'? If not, how to log-in as  a root? Thanks a lot!

In Windows, an admin can do anything.
In Linux however, only the root account (which you cant login as normally) can change some system files.

To login as root type:

```
su
```

You will then be prompted for the password. To exit from root, type "exit".

You can also access the menu.lst file by typing:

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by OsamaK on 2008-05-30
Great! Edited. Thanks :)

---

