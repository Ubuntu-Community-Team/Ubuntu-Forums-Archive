---
title: "Backing up Xorg configuration"
date: 2006-11-18
forum: General Help
---

### Post by Ryan H on 2006-11-18
I tried to change my monitor resolution by editing the xserver configuration files via command prompt and now I can't start x server so I have no GUI. I downloaded Lynx through the terminal and that's what I am using now but it's not very accessible. If anyone could tell me how to back it up that would be awesome.
Thanks.

-Ryan H

---

### Post by turbojugend_gr on 2006-11-18
If you have not backed up xorg.conf file there no way for you to restore it, if you did it should be like "/etc/X11/xorg.conf.bak" just rename it deleting the .bak thing and restart X.

If there's no backup file, type "sudo dpkg reconfigure xserver-xorg" and foolow instructions, should be easy.

Best wishes, TJ.

---

### Post by Ryan H on 2006-11-19
I tried to change my monitor resolution by editing the xserver configuration files via command prompt and now I can't start x server so I have no GUI. I downloaded Lynx through the terminal and that's what I am using now but it's not very accessible. If anyone could tell me how to back it up that would be awesome.
Thanks.

-Ryan H

---

### Post by ciscosurfer on 2006-11-19
At this point, you need to reconfigure your xorg.conf file via command line.  You can do this manually via the command line program **vi** and edit the file that way.  Learn about using vi first through the man pages```
man vi
```Once you get it the way you like it, you can make a backup like this```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```From the command line you can also issue the following, and it will help you configure your file via ncurses (I believe...someone can correct me here if they know better)```
sudo dpkg-reconfigure xserver-xorg
```You can also issue the same with the following switch```
sudo dpkg-reconfigure -phigh xserver-xorg
```Good Luck!

---

