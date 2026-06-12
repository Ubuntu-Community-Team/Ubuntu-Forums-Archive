---
title: "restore x11/org/conf [Resolved]"
date: 2007-02-12
forum: General Help
---

### Post by virtualsnyper on 2007-02-12
hey all...how do i restore my  x11/org/conf backup that i made. i guess you could call me a noob. i'd rather restore it thatn reinstall ubuntu....(again) *ahem. THX!

---

### Post by virtualsnyper on 2007-02-12
hey all...how do i restore my  x11/org/conf backup that i made. i guess you could call me a noob. i'd rather restore it thatn reinstall ubuntu....(again) *ahem. THX!

---

### Post by g3k0 on 2007-02-12
just copy the backup over it using the cp command.
or copy and paste it...
doesnt matter really.

---

### Post by virtualsnyper on 2007-02-12
hey all...im trying to instal nvidia drivers and....surprise surprise ... beryl. I keep crashing my X after reboot though. how do i restore my  x11/org/conf backup that i made. i guess you could call me a noob. i'd rather restore it thatn reinstall ubuntu....(again) *ahem. THX!

---

### Post by virtualsnyper on 2007-02-12
how would that look, since i have to do it in console ?? 

cp  /x11/xorg.conf  /x11/xorg.conf.back ????

---

### Post by g3k0 on 2007-02-12
cp GoodFile BadFile

---

### Post by racmar on 2007-02-12
Assuming your xorg backup is named xorg.conf.back:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.2007.02.12
sudo cp /etc/X11/xorg.conf.back /etc/X11/xorg.conf
```

then reboot 
or restart gdm or kdm by:
```
sudo /etc/init.d/gdm restart
```

---

### Post by highneko on 2007-02-12
> **virtualsnyper said:**
> hey all...im trying to instal nvidia drivers and....surprise surprise ... beryl. I keep crashing my X after reboot though. how do i restore my  x11/org/conf backup that i made. i guess you could call me a noob. i'd rather restore it thatn reinstall ubuntu....(again) *ahem. THX!
If you're using a livecd now you could first mount the root ubuntu partition, then using gnome-terminal copy and replace your current xorg.conf.
```

# Find your root ubuntu partition:
sudo fdisk -l && df -h
# Make directory for partition:
sudo mkdir /ubuntu
# Mount the root ubuntu partition:
sudo mount /dev/example /ubuntu
# Change current directory:
cd /ubuntu/etc/X11/
# Make backups:
sudo cp xorg.conf xorg.conf.broken
# List to find your backup, and a grep too for fun:
ls | grep 'bak' || ls | grep 'bac' || ls
# Replace the word "example" with the real backup file to restore your backup:
sudo cp example xorg.conf

```
Then restart. Good luck, have fun.

---

### Post by virtualsnyper on 2007-02-12
outstanding...THX!

---

### Post by virtualsnyper on 2007-02-12
Amazing Thx!

---

