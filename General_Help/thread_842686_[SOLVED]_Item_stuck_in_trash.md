---
title: "[SOLVED] Item stuck in trash"
date: 2008-06-27
forum: General Help
---

### Post by Joe of loath on 2008-06-27
hi all;

I deleted a file a while back, but it's still stuck in the trash. I try delete or move it, and it comes up the following error:

Error removing file: Directory not empty

does anyone have any answers as to how I delete it? I would do it through the terminal, or at least try, but I have no idea where the trash is located.

thanks in advance;
Joe

---

### Post by Vivaldi Gloria on 2008-06-27
Try following. Press Alt+F2 and start

```
gksudo nautilus
```

Find the top level of the disk the file is deleted from, i.e. if it was in /mnt/mountpoint then go there. Then press ctrl+H to see hidden files. Press shift + delete after you select the .trash-* folder.

If you have more than one disk drive then shift+delete .trash-* folders in each one.

---

### Post by nikgare on 2008-06-28
Your trash should be located here:

~/.local/share/Trash/files

---

### Post by iaculallad on 2008-06-28
For User's trash:

```
sudo rm -rf /home/your_username/.local/share/Trash/*
```

Or for Root's Trash:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by VMC on 2008-06-28
Have you tried rebooting and then check you trash. I've had problems when trash gets messed up and then a reboot solves everthing.

---

### Post by aysiu on 2008-06-28
iaculallad's suggestion will work, but if you take it, be very, very careful to **paste** the command in instead of retyping it. If you mess up retyping, you could be emptying a lot more than the trash.

---

### Post by Joe of loath on 2008-07-04
second one worked, thanks!

---

### Post by Habbit on 2008-07-04
Actually, the root access provided by sudo and the root shell of "sudo -s" preserves the $HOME variable (try it running "echo ~" with such commands). Only "sudo -i" creates a "clean" interactive root shell with $HOME="/root".

---

