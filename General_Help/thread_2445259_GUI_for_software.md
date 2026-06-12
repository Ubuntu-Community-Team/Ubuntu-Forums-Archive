---
title: "GUI for software"
date: 2020-06-11
forum: General Help
---

### Post by T6&amp;sfpER35% on 2020-06-11
is there a GUI for ubuntu software centre (now snap store in 20.04) and flatpak?
i've downloaded apt and flatpak but both only runs in terminal.
cause frankly , snap store sux.

thanks!

---

### Post by tea for one on 2020-06-11
Are you looking for gnome-software?

```
sudo apt install gnome-software
```

The icon will be labelled **Software**

---

### Post by T6&amp;sfpER35% on 2020-06-11
ok cool found it.
but i've also installed flatpak plugin ( ```
o14@01:~$ sudo apt install gnome-software-plugin-flatpak[sudo] password for o14: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-software-plugin-flatpak is already the newest version (3.36.0-0ubuntu3).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
o14@01:~$ 



``` ) ,but it doesn't show under **software ?**

---

### Post by Dennis N on 2020-06-11
> [flatpak plugin] .. but it doesn't show under software ?

It is a plugin for gnome-software with no separate GUI. When a Flatpak version of the software is available, it is selectable using the sources selector at the top of the Software GUI.

---

### Post by T6&amp;sfpER35% on 2020-06-11
oh ok , i see . thanks!
in a previous distro i had there was a block named flatpak where one would find all the flatpak apps.
guess that's what  confused me .

---

### Post by Dennis N on 2020-06-11
Here is a screenshot (attached)
And if you want to see Flatpaks only, use the Flathub web site.

---

### Post by T6&amp;sfpER35% on 2020-06-11
yes thanks i saw that now.

what i meant by block for flatpak

[IMG]https://i.ibb.co/TbHWN8q/download.jpg[/IMG]


bottom right corner

anyway ,no big deal, thanks for replies.

---

### Post by Dennis N on 2020-06-11
> bottom right corner
Is this from the 'previous distro' you referred to? I see it's called 'Software Manager' which I don't recognize.

---

### Post by T6&amp;sfpER35% on 2020-06-11
yes ,it's from mint

---

