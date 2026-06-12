---
title: "Mounted drives on desktop"
date: 2013-02-19
forum: General Help
---

### Post by Barney-R on 2013-02-19
Previous versions of Ubuntu have shown an icon on the desktop whenever a drive or partition is mounted, a CD or DVD inserted or a memory stick plugged in.

I like to unmount devices that aren't currently in use, and before shutting down, but 12.04 (using Gnome desktop) doesn't show them, though desktop items are shown.

I realise 12.04 is different to what I've known before, better in some ways, and some things I'll have to get used to, but is there an easy way to display mounted drives on the desktop?

---

### Post by dino99 on 2013-02-19
first be sure to use a clean /etc/fstab : only mount what is needed by the session, as mountall will directly mount/umount on the fly the other device(s)

---

### Post by Barney-R on 2013-02-19
Sorry dino99. I don't understand any of that.

I normally mount partitions (on a second physical drive) from the "Places" menu in Gnome, and other devices by inserting them (CD/DVD) or by plugging them in. I can also mount and unmount partitions using the Disk Utility.

I normally only mount partitions/devices when I want them, but it's a lot easier if I can have a reminder icon on the desktop to show which devices are mounted, which also gives me the option to right-click and unmount/eject.

---

### Post by rnerwein on 2013-02-19
> **Barney-R said:**
> Sorry dino99. I don't understand any of that.

I normally mount partitions (on a second physical drive) from the "Places" menu in Gnome, and other devices by inserting them (CD/DVD) or by plugging them in. I can also mount and unmount partitions using the Disk Utility.

I normally only mount partitions/devices when I want them, but it's a lot easier if I can have a reminder icon on the desktop to show which devices are mounted, which also gives me the option to right-click and unmount/eject.
hi
i am running 12.04 too and on the sidebar is for every drive wich is present in the fstab a icon. if i plug in a device when the system is already up a icon pops up on the sidbar too.

hm ???
chiao

---

### Post by Barney-R on 2013-02-19
From what you say, I assume you're using the Unity desktop, rnerwein. I'll probably switch to that at some point, but for now, with so much to do (I only installed 12.04 on Friday), I'm more comfortable with Gnome.

I'm sure you understand what it's like with a clean install, settings to be entered manually, software to be installed and set up the way I want it, any number of other things. I suspect that I'll prefer Unity in time, but for now it's one less complication if I keep to what I know.

---

### Post by dino99 on 2013-02-19
[http://askubuntu.com/questions/126540/how-to-add-a-show-desktop-icon-to-the-launcher](http://askubuntu.com/questions/126540/how-to-add-a-show-desktop-icon-to-the-launcher)

---

### Post by Barney-R on 2013-02-19
Problem solved!

After a bit of Googling, I found the following thread.

[http://ubuntuforums.org/showthread.php?t=1944438](http://ubuntuforums.org/showthread.php?t=1944438)

On checking the Software Center, using the search term "tweak", I found "Advanced Settings" (Tweak advanced GNOME 3 settings).

I installed it, opened it, and on the "Desktop" page I found "Show mounted volumes on the desktop". I mounted a volume to test it, and there it was.

---

