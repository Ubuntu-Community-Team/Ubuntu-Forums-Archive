---
title: "Failed to write to /home/user.."
date: 2006-11-30
forum: General Help
---

### Post by ~LoKe on 2006-11-30
> Nov 30 10:34:16 x04d gconfd (loke-8368): Failed to write "/home/loke/.gconf/desktop/gnome/interface/%gconf.xml": Failed to open "/home/loke/.gconf/desktop/gnome/interface/%gconf.xml.new": Permission denied  
Nov 30 10:35:18 x04d gconfd (loke-8368): Failed to write "/home/loke/.gconf/apps/update-manager/%gconf.xml": Failed to open "/home/loke/.gconf/apps/update-manager/%gconf.xml.new": Permission denied  
Nov 30 10:35:18 x04d gconfd (loke-8368): Failed to write "/home/loke/.gconf/apps/metacity/general/%gconf.xml": Failed to open "/home/loke/.gconf/apps/metacity/general/%gconf.xml.new": Permission denied  
Nov 30 10:35:18 x04d gconfd (loke-8368): Failed to write "/home/loke/.gconf/apps/panel/applets/applet_6/prefs/%gconf.xml": Failed to open "/home/loke/.gconf/apps/panel/applets/applet_6/prefs/%gconf.xml.new": Permission denied  
Nov 30 10:35:18 x04d gconfd (loke-8368): Failed to write "/home/loke/.gconf/desktop/gnome/peripherals/keyboard/host-x04d/0/%gconf.xml": Failed to open "/home/loke/.gconf/desktop/gnome/peripherals/keyboard/host-x04d/0/%gconf.xml.new": Permission denied  
Nov 30 10:35:18 x04d gconfd (loke-8368): Failed to write "/home/loke/.gconf/desktop/gnome/interface/%gconf.xml": Failed to open "/home/loke/.gconf/desktop/gnome/interface/%gconf.xml.new": Permission denied  
I recently reinstalled Edgy and backed up  my home directory.  Once I replaced it, I started getting these errors.  I've used the same username the whole time, so that'd can't be a problem.  I've tried chmod 664 and 775'ing my home directory, no help.

Am I supposed to chown it or something?

---

### Post by apjone on 2006-11-30
Try chown ,

---

### Post by taurus on 2006-11-30
Boot into the recovery mode and at the prompt, paste the output of these two commands here.

```
id loke
/home/loke
```

---

### Post by ~LoKe on 2006-11-30
> **taurus said:**
> Boot into the recovery mode and at the prompt, paste the output of these two commands here.

```
id loke
/home/loke
```

> uid=1000(loke) gid=1000(loke) groups=1000(loke),4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin)
loke@x04d:~$ /home/loke
bash: /home/loke: is a directory

Didn't need to use the recovery console; I can log in just fine. =]

---

### Post by taurus on 2006-11-30
Sorry, it should have been

```
ls -la /home/loke
```

---

### Post by ~LoKe on 2006-11-30
> loke@x04d:~$ ls -la /home/loke
total 1072
drwxrwxr-x 12 root root   4096 2006-11-29 17:12   
drwxr-xr-x 46 loke loke   4096 2006-11-30 10:33 .
drwxr-xr-x  3 root root   4096 2006-11-29 14:52 ..
drwxrwxr-x  2 root root   4096 2006-11-29 17:14 .3ddesktop
-rwxrwxr-x  1 loke loke  13560 2006-11-30 10:32 .bash_history
-rwxrwxr-x  1 loke loke    220 2006-11-29 17:13 .bash_logout
-rwxrwxr-x  1 loke loke    414 2006-11-29 17:13 .bash_profile
-rwxrwxr-x  1 loke loke   2227 2006-11-29 17:13 .bashrc
drwxr-xr-x  2 loke loke   4096 2006-11-29 19:54 .beryl
-rw-r--r--  1 loke loke    117 2006-11-30 10:33 .beryl-managerrc
drwxrwxr-x  4 loke loke   4096 2006-11-29 18:25 .config
-rwxrwxr-x  1 root root   6182 2006-11-29 17:13 .conkyrc
-rwxrwxr-x  1 root root    140 2006-11-29 17:13 .cvspass
drwxrwxr-x  3 loke loke   4096 2006-11-30 00:15 Desktop
-rw-------  1 loke loke     26 2006-11-30 10:33 .dmrc
drwxrwxr-x  7 root root   4096 2006-11-29 17:14 .dvdcss
drwxrwxr-x  4 loke loke   4096 2006-11-29 17:43 .emerald
-rwxrwxr-x  1 loke loke     16 2006-11-29 17:13 .esd_auth
drwxrwxr-x  8 root root   4096 2006-11-29 17:14 .etwolf
drwxrwxr-x  8 root root   4096 2006-11-29 17:13 .evolution
drwxrwxr-x  5 root root   4096 2006-11-29 17:14 .exaile
lrwxrwxrwx  1 loke loke     26 2006-11-29 14:52 Examples -> /usr/share/example-content
-rwxrwxr-x  1 loke loke      0 2006-11-29 17:18 .fonts.cache-1
-rwxrwxr-x  1 root root    202 2006-11-29 17:13 .fonts.conf
drwxrwxr-x  4 root root   4096 2006-11-29 17:13 .gaim
drwxrwxr-x  6 loke loke   4096 2006-11-30 10:14 .gconf
drwxrwxr-x  2 loke loke   4096 2006-11-30 11:45 .gconfd
drwxrwxr-x  3 root root   4096 2006-11-29 17:12 .gftp
drwxrwxr-x 21 root root   4096 2006-11-29 17:12 .gimp-2.2
drwxrwxr-x  5 root root   4096 2006-11-29 17:13 .gkrellm2
-rwxrwxr-x  1 loke loke      0 2006-11-30 10:15 .gksu.lock
drwxrwxr-x  3 loke loke   4096 2006-11-30 10:22 .gnome
drwxrwxr-x  6 loke loke   4096 2006-11-30 10:22 .gnome2
drwx------  2 loke loke   4096 2006-11-29 18:00 .gnome2_private
drwxrwxr-x  2 root root   4096 2006-11-29 17:12 .gnupg
drwxrwxr-x  2 loke loke   4096 2006-11-29 16:42 .gstreamer-0.10
-rwxrwxr-x  1 root root      0 2006-11-29 17:13 .gtk-bookmarks
-rwxrwxr-x  1 loke loke     86 2006-11-29 17:13 .gtkrc-1.2-gnome2
-rwxrwxr-x  1 loke loke    730 2006-11-29 21:38 .gtk-recordmydesktop
-rwxrwxr-x  1 loke loke    863 2006-09-02 13:28 hawkwind.asc
-rw-------  1 loke loke  35351 2006-11-30 10:33 .ICEauthority
drwxrwxr-x  4 root root   4096 2006-11-29 17:13 .icons
drwxrwxr-x  3 root root   4096 2006-11-29 17:14 .kde
-rwxrwxr-x  1 root root     35 2006-11-29 17:13 .lesshst
drwxrwxr-x  3 root root   4096 2006-11-29 17:12 .local
drwxrwxr-x  3 loke loke   4096 2006-11-29 18:38 .macromedia
-rwxrwxr-x  1 root root    114 2006-11-29 17:13 .mailcap
drwxrwxr-x  3 root root   4096 2006-11-29 17:14 .mcop
-rwxrwxr-x  1 root root     31 2006-11-29 17:14 .mcoprc
drwxrwxr-x  3 loke loke   4096 2006-11-29 14:59 .metacity
-rwxrwxr-x  1 root root    230 2006-11-29 17:14 .mime.types
drwxrwxr-x  3 loke loke   4096 2006-11-29 17:33 .mozilla
drwxrwxr-x  2 root root   4096 2006-11-29 17:12 .mplayer
-rwxrwxr-x  1 root root    268 2006-11-29 17:14 .mysql_history
drwxrwxr-x  3 loke loke   4096 2006-11-29 17:12 .nautilus
drwxrwxr-x  2 root root   4096 2006-11-29 17:13 .ntrc_2
-rwxrwxr-x  1 root root   1362 2006-11-29 17:13 .nvidia-settings-rc
drwxrwxr-x  3 root root   4096 2006-11-29 17:13 .openoffice.org2
drwxrwxr-x  2 root root   4096 2006-11-29 17:13 .qt
-rwxrwxr-x  1 root root  41267 2006-11-29 17:13 .recently-used
-rwxrwxr-x  1 loke loke 190645 2006-11-29 21:37 .recently-used.xbel
-rwxrwxr-x  1 root root   1024 2006-11-29 17:14 .rnd
-rw-rw-r--  1 loke loke     26 2006-11-29 17:13 save.dmrc
-rwxrwxr-x  1 root root 217305 2006-11-29 17:14 setlist.jpg
drwxrwxr-x  3 root root   4096 2006-11-29 17:12 .subversion
-rwxrwxr-x  1 loke loke      0 2006-11-29 17:13 .sudo_as_admin_successful
drwxrwxr-x  2 root root   4096 2006-11-29 17:12 .synaptic
drwxrwxr-x 15 root root   4096 2006-11-29 17:13 .themes
drwxrwxr-x  5 loke loke   4096 2006-11-29 17:13 .thumbnails
drwxrwxr-x  8 loke loke   4096 2006-11-29 17:32 .Trash
drwxrwxr-x  2 root root   4096 2006-11-29 17:13 .update-manager
drwxrwxr-x  2 loke loke   4096 2006-11-29 17:12 .update-notifier
drwxrwxr-x  4 root root   4096 2006-11-29 18:43 usr
-rwxrwxr-x  1 root root 174163 2006-11-29 17:13 utorrent.exe
drwxrwxr-x  3 root root   4096 2006-11-29 17:13 .vlc
drwxrwxr-x  2 root root   4096 2006-11-29 17:13 .wapi
-rwxrwxr-x  1 root root      4 2006-11-29 17:13 .windows-label
-rwxrwxr-x  1 loke loke    115 2006-11-29 18:03 .Xauthority
-rwxrwxr-x  1 loke loke    117 2006-11-29 17:53 .xbindkeysrc
-rw-r--r--  1 loke loke 103620 2006-11-30 11:49 .xsession-errors

I was stupid enough not to remove the hidden configuration files beforing copying over my home directory.  That must be the cause.

---

### Post by taurus on 2006-11-30
```
sudo chown -R loke:loke /home/loke
```

---

### Post by ~LoKe on 2006-11-30
Ah, so simple.  Thank you!

---

### Post by taurus on 2006-11-30
But of course.  ;)   Let me know if everything is working fine now!

---

### Post by ~LoKe on 2006-11-30
> **taurus said:**
> But of course.  ;)   Let me know if everything is working fine now!

Aye, it does. ;)

---

