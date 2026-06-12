---
title: "system hangs after login"
date: 2008-03-17
forum: General Help
---

### Post by adult swim on 2008-03-17
i am running gutsy with an intel 945 video card.  i was messing with my resolutions and i switched the screen orientation to upside down when my system crashed.  i thought no problem, ctrl-alt-backspace to login again.  now i can get to a normal login screen but after i login my screen flashes, then the cursor is displayed upside down (as expected) but it just hangs with a tan screen.  nothing will load.
i have tried to reconfigure the xserver in tty1 with sudo dpkg -reconfigure xserver-xorg and with the fix X command from booting in recovery mode.  all they seem to be interested in is my keyboard layout.
im stuck here!

---

### Post by Tomatz on 2008-03-17
This should fix it:

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Tomatz on 2008-03-17
It will ask for keyboard layout (this is important) just take your time and answer all questions correctly.

---

### Post by adult swim on 2008-03-17
i ran sudo dpkg-reconfigure -phigh xserver-xorg and it didnt prompt for anything, it just displayed that a backup had been made of my old file.  it is still hanging after login, with the upside down cursor.

---

### Post by taurus on 2008-03-17
Remove the -phigh option if you want to reconfigure everything.

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by adult swim on 2008-03-17
i tried that too but it didnt work.  is there a way i could copy the xserver-xorg from a live cd to my hd?

---

### Post by taurus on 2008-03-17
Yes, there is.

Boot from the LiveCD.  Then, mount the partition on the harddrive where / is located.  Assuming it is /dev/sda1, do,

```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/sda1 /mnt/ubuntu
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
sudo umount /dev/sda1
```
Reboot and see what happens.

---

### Post by Tomatz on 2008-03-17
t

---

