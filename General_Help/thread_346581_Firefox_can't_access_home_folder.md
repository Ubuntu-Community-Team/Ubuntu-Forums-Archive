---
title: "Firefox can't access home folder"
date: 2007-01-25
forum: General Help
---

### Post by PigCorpse on 2007-01-25
Hi,

I'm having a very weird problem with Firefox and I don't know how it happened.

Anyway, I started up FireFTP and went to /home/mike. It told me that it didn't have the necessary permissions to access the folder. I go to file:///home. It opened fine. When I click on my home folder, it doesn't respond. However, if I go to file:///home/mike/documents or anything else INSIDE the folder, it works fine. I just can't browse the home folder. Plus, all my settings are fine, so that means it can access /home/mike/.mozilla and all right?

Any ideas?

---

### Post by taurus on 2007-01-25
What's the output of this command from a terminal?

```
id
ls -la /home/mike
```

---

### Post by PigCorpse on 2007-01-25
```
[SIZE="2"][FONT="Courier New"]mike@mike-kubuntu:~$ id
uid=1000(mike) gid=1000(mike) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),111(admin),1000(mike)
mike@mike-kubuntu:~$ lla /home/mike
total 25445048
drwxr-xr-x 26 mike mike        4096 2007-01-25 22:38 .
drwxr-xr-x  4 root root        4096 2007-01-07 18:30 ..
-rw-r--r--  1 mike mike         189 2007-01-24 21:39 .bash_aliases
-rw-------  1 mike mike        4318 2007-01-25 20:48 .bash_history
-rw-r--r--  1 mike mike         220 2007-01-07 18:30 .bash_logout
-rw-r--r--  1 mike mike         414 2007-01-07 18:30 .bash_profile
-rw-r--r--  1 mike mike        2362 2007-01-18 18:08 .bashrc
drwxr-xr-x 10 mike mike        4096 2007-01-24 01:52 cs
-rw-r--r--  1 mike mike          59 2007-01-25 22:33 .DCOPserver_mike-kubuntu__0
lrwxrwxrwx  1 mike mike          38 2007-01-25 22:33 .DCOPserver_mike-kubuntu_:0 -> /home/mike/.DCOPserver_mike-kubuntu__0
drwx------  2 mike mike        4096 2007-01-16 17:43 Desktop
-rw-------  1 mike mike          26 2007-01-07 18:30 .dmrc
drwxr-xr-x  9 mike mike        4096 2007-01-25 14:43 documents
drwxr-x---  2 mike mike        4096 2007-01-08 19:23 .easytag
-rw-r--r--  1 mike mike        5522 2007-01-07 18:30 .face.icon
drwxr-xr-x  3 mike mike        4096 2007-01-23 21:21 .folding
-rw-r--r--  1 mike mike           0 2007-01-12 22:53 .fonts.cache-1
-rw-r--r--  1 mike mike         516 2007-01-07 18:30 .fonts.conf
drwxr-xr-x  3 mike mike        4096 2007-01-07 18:45 .fullcircle
drwx------  5 mike mike        4096 2007-01-25 22:38 .gaim
drwx------  3 mike mike        4096 2007-01-25 22:36 .gconf
drwx------  2 mike mike        4096 2007-01-25 22:41 .gconfd
drwx------  4 mike mike        4096 2007-01-07 18:31 .gnome2
drwx------  2 mike mike        4096 2007-01-07 18:31 .gnome2_private
drwx------  2 mike mike        4096 2007-01-07 18:31 .gnupg
-rw-r--r--  1 mike mike       24556 2007-01-07 18:30 .gtk_qt_engine_rc
-rw-r--r--  1 mike mike         277 2007-01-07 18:30 .gtkrc-2.0
-rw-r--r--  1 mike mike 26030012744 2007-01-25 19:58 home.tgz
-rw-------  1 mike mike         402 2007-01-25 22:33 .ICEauthority
drwxr-xr-x  2 mike mike        4096 2007-01-07 18:45 .icons
drwxr-xr-x  4 mike mike        4096 2006-12-24 22:34 .IntelliJIdea60
drwxr-xr-x  4 mike mike        4096 2007-01-07 18:45 .java
drwx------  4 mike mike        4096 2007-01-07 18:30 .kde
-rw-------  1 mike mike         409 2007-01-17 22:41 .kderc
-rw-------  1 mike mike          35 2007-01-25 21:27 .lesshst
drwx------  3 mike mike        4096 2007-01-15 15:16 .local
drwx------  3 mike mike        4096 2007-01-07 18:31 .macromedia
drwxr-xr-x  3 mike mike        4096 2007-01-07 18:30 .mcop
drwx------  3 mike mike        4096 2007-01-07 18:30 .mozilla
drwx------  3 mike mike        4096 2007-01-25 22:24 .openoffice.org2
drwxr-xr-x  2 mike mike        4096 2007-01-25 22:33 .qt
drwxr-xr-x  4 mike mike        4096 2007-01-25 20:30 .shared
-rw-r--r--  1 mike mike           0 2007-01-07 18:30 .sudo_as_admin_successful
-rw-------  1 mike mike         167 2007-01-25 22:33 .Xauthority
drwxr-xr-x  2 mike mike        4096 2007-01-07 18:31 .xine
-rw-------  1 mike mike       56560 2007-01-25 22:51 .xsession-errors
[/FONT][/SIZE]
```

---

### Post by PigCorpse on 2007-01-26
Bump?

Update:

I removed my .mozilla folder and put it elsewhere so Firefox would start a new profile, but the problem still remains.

---

### Post by PigCorpse on 2007-01-27
Bump? No one has this problem and/or a solution?

Update:

This is the Firefox 2.0 I downloaded from Mozilla, not from the repos. I downloaded it again and did a fresh install, still the same.

Double update:

I did 'kdesu firefox' to run as root. I can go to file:///root, but I still can't go to file:///home/mike...

wtf...

---

