---
title: "Incomplete xorg?"
date: 2005-03-22
forum: General Help
---

### Post by taki on 2005-03-22
I'm following the how to on installing ATI drivers.

When I get to here:

Edit /etc/X11/xorg.conf and change "ati" to "fglrx", perhaps with a command like: sudo*sed*-i*-e*'s/"ati"/"fglrx"/'*/etc/X11/xorg.conf. Alternatively, just use your favourite text editor, or use sudo*dpkg-reconfigure*xserver-xorg and select "fglrx" instead of "ati".

I have a big problem. I can edit xorg.conf okay, but when I try to reconfigure xserver-xorg, I get this:

dpkg: error processing reconfigure (--install):
 cannot acess archive: No such file or directory
dpkg: error processing xserver-xorg (--install):
 cannot acess archive: No such file or directory

Also, I don't seem to have an XF86Config-4 file. Anywhere.

I used Synaptic to install all the files it told me to install. What am I missing?

---

### Post by JGJones on 2005-03-22
[QUOTE=taki]I'm following the how to on installing ATI drivers.

When I get to here:

Edit /etc/X11/xorg.conf and change "ati" to "fglrx", perhaps with a command like: sudo*sed*-i*-e*'s/"ati"/"fglrx"/'*/etc/X11/xorg.conf. Alternatively, just use your favourite text editor, or use sudo*dpkg-reconfigure*xserver-xorg and select "fglrx" instead of "ati".

I have a big problem. I can edit xorg.conf okay, but when I try to reconfigure xserver-xorg, I get this:

dpkg: error processing reconfigure (--install):
 cannot acess archive: No such file or directory
dpkg: error processing xserver-xorg (--install):
 cannot acess archive: No such file or directory

Also, I don't seem to have an XF86Config-4 file. Anywhere.

I used Synaptic to install all the files it told me to install. What am I missing?[/QUOTE]
 When you edit xorg.conf file you don't need to run dpkg-reconfigure xserver-xorg.

There is no XF86Config-4 file as that's for XFree86 (Warty) since Hoary now use xorg instead.

Just run

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo gedit /etc/X11/xorg.conf

```

First line copy your original xorg.conf file to a backup file
Second line - directly edit the xorg.conf file - you  can do this no problem so do this and change ati to fglrx in Devices section.

Restart X by pressing Crtl, Alt and Backspace at same time.

---

### Post by taki on 2005-03-23
Thanks for clearing that up, JG.

---

