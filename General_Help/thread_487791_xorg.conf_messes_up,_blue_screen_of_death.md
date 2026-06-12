---
title: "xorg.conf messes up, blue screen of death"
date: 2007-06-29
forum: General Help
---

### Post by Neuralgia on 2007-06-29
hi guys...

as the title states, i messed up with my xorg.conf

i did a back up, but i don't know how to restore it... WITHOUT using any graphical interface.

Everytime i boot i get a blue screen telling my my xorg.conf doesn't detect a screen...

Help please!

---

### Post by samkline on 2007-06-29
when you're at X's blue screen, press CTRL+ALT+F1 to switch to tty1. then login, you should use the root account. i don't know how experienced you are so i'll make it simple. do this:

[LIST=1]
[*]type [FONT="Courier New"]cd /etc/X11[/FONT] (remember, it is case sensitive) to switch to the proper directory
[*]type [FONT="Courier New"]rm xorg.conf[/FONT] (this will remove your X configuration file, you may want to just move it somewhere else with [FONT="Courier New"]mv xorg.conf old_xorg.conf[/FONT])
[*]if you know the filename of your backup, type [FONT="Courier New"]mv xorg_backup.conf xorg.conf[/FONT] - of course replacing the first filename with whatever you named it. this assumes the backup file is in the same directory, if not use the full path for the first file (for example, [FONT="Courier New"]mv /home/you/xorg_backup.conf xorg.conf[/FONT])
[*]if you can't remember the filename exactly, just type [FONT="Courier New"]ls[/FONT] to view a listing of the files in that directory.
[*]after you restore your original xorg.conf, type [FONT="Courier New"]startx[/FONT] to start the graphical user interface.
[/LIST]

hope this helps, reply if you have any questions :)

edit: if you can't find your old backup, you can also type [FONT="Courier New"]dpkg-reconfigure xserver-xorg -pcritical[/FONT] to have it generate one (do this as root, or put [FONT="Courier New"]sudo[/FONT] in front)

---

### Post by Crafty Kisses on 2007-06-29
> **Neuralgia said:**
> hi guys...

as the title states, i messed up with my xorg.conf

i did a back up, but i don't know how to restore it... WITHOUT using any graphical interface.

Everytime i boot i get a blue screen telling my my xorg.conf doesn't detect a screen...

Help please!

You should try this command:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Neuralgia on 2007-06-29
Thx samkline, but my "backup" was a peace of paper ;)

I did what codename suggested, and now it's back as good as always... thanks

---

