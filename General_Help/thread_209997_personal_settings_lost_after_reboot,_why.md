---
title: "personal settings lost after reboot, why?"
date: 2006-07-06
forum: General Help
---

### Post by blackpaw on 2006-07-06
hello!

This time I am really clueless and kindly have to ask for your help.

Every time I restart my system, many personal settings are lost.

For example Forefox forgets the bookmarks but remembers the plugins.
Streamtuner forgets all the bookmarks.
Opera remembers everything
the desktop and xserver settings are kept (ATI dualhead) but the xgamma settings are back to default.
and so on.. 

What I did is, I installed from CD (from scratch), additionally had "xubuntu-desktop" installed but it was bitchy with ATI's driver and I couldn't get the twin monitors working so I removed it with synaptic.
furthermore I installed and uninstalled the ATI driver a couple of times (proprietary and "out-of-the-box" driver) but reverted to the mesa driver that came with ubuntu later in order to get some sleep. :roll: 

Can anyone give me a hint

- where to find out why my ubuntu loses some of its settings
(my suggestion are bad file permission somewhere but I have no clue)

- how I can stop this

thank you very much! 


andreas

---

### Post by aysiu on 2006-07-06
Any chance you did *sudo graphicalapp*? More details here on how that can screw up your system:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

Can you post the output of these two commands? ```
cd
ls -al
``` I'm particularly interested in the lines for **.mozilla** and **.opera**.

---

### Post by blackpaw on 2006-07-06
hiho.

no graphical sudo, no. I am hearing of it for the first time.

here my ls -al

```
bazi@blackpaw:~$ ls -al
total 412
drwxr-xr-x  50 bazi bazi  4096 2006-07-06 07:48 .
drwxr-xr-x   3 root root  4096 2006-06-29 13:11 ..
drwxr-xr-x   3 bazi bazi  4096 2006-06-29 18:35 .adobe
-rw-r--r--   1 bazi bazi   188 2006-07-04 07:49 .asoundrc
-rw-r--r--   1 bazi bazi   344 2006-07-04 07:49 .asoundrc.asoundconf
-rw-------   1 bazi bazi 10747 2006-07-06 00:50 .bash_history
-rw-r--r--   1 bazi bazi   220 2006-06-29 13:11 .bash_logout
-rw-r--r--   1 bazi bazi   414 2006-06-29 13:11 .bash_profile
-rw-r--r--   1 bazi bazi  2227 2006-06-29 13:11 .bashrc
drwx------   4 bazi bazi  4096 2006-07-04 00:28 .cache
drwx------   2 bazi bazi  4096 2006-07-04 19:42 .camel_certs
drwx------   2 bazi bazi  4096 2006-07-04 08:12 .chewing
drwx------   6 bazi bazi  4096 2006-07-04 07:48 .config
-rw-r--r--   1 bazi bazi   324 2006-07-04 20:06 .cowbell
drwx------   2 bazi bazi  4096 2006-06-29 18:52 .cups
drwxr-xr-x   2 bazi bazi  4096 2006-07-06 07:53 Desktop
-rw-------   1 bazi bazi    24 2006-07-04 07:49 .dmrc
-rw-------   1 bazi bazi    16 2006-06-29 11:14 .esd_auth
drwxr-xr-x   8 bazi bazi  4096 2006-07-06 07:56 .evolution
lrwxrwxrwx   1 bazi bazi    26 2006-06-29 13:11 Examples -> /usr/share/example-content
-rw-r--r--   1 root root 87242 2006-06-29 14:52 .fonts.cache-1
drwx------   5 bazi bazi  4096 2006-07-06 07:05 .gconf
drwx------   2 bazi bazi  4096 2006-07-06 07:58 .gconfd
-rw-r-----   1 bazi bazi     0 2006-07-06 07:54 .gksu.lock
drwxr-xr-x   3 bazi bazi  4096 2006-06-29 11:14 .gnome
drwx------  21 bazi bazi  4096 2006-07-06 07:44 .gnome2
drwx------   2 bazi bazi  4096 2006-07-04 19:41 .gnome2_private
drwx------   2 bazi bazi  4096 2006-06-30 10:56 .gnupg
drwxr-xr-x   2 bazi bazi  4096 2006-06-14 12:05 GPG
drwx------   2 bazi bazi  4096 2006-07-06 07:43 .gpilotd
-rw-r--r--   1 bazi bazi     5 2006-07-06 07:43 .gpilotd.pid
drwxr-xr-x   2 bazi bazi  4096 2006-06-29 15:08 .gstreamer-0.10
-rw-------   1 bazi bazi    24 2006-06-29 22:45 .gtk-bookmarks
-rw-r--r--   1 bazi bazi    86 2006-06-29 11:14 .gtkrc-1.2-gnome2
-rw-------   1 bazi bazi  1469 2006-07-06 07:05 .ICEauthority
drwxr-xr-x   2 bazi bazi  4096 2006-06-29 23:48 .icons
drwxr-xr-x   2 bazi bazi  4096 2006-06-30 11:27 icq
drwxr-xr-x   3 bazi bazi  4096 2006-07-05 08:34 .java
drwxr-xr-x   5 bazi bazi  4096 2006-06-14 12:06 kochen
drwx------   5 bazi bazi  4096 2006-07-06 00:50 .licq
drwx------   3 bazi bazi  4096 2006-06-30 10:59 .local
drwxr-xr-x  11 bazi bazi  4096 2006-06-14 11:56 manga_and_comix
drwx------   3 bazi bazi  4096 2006-06-29 11:14 .metacity
drwx------   3 bazi bazi  4096 2006-06-29 11:56 .mozilla
drwx------   3 bazi bazi  4096 2006-06-29 11:56 .mozilla-thunderbird
drwx------   3 bazi bazi  4096 2006-07-06 07:44 .multisync
drwxr-xr-x 289 bazi bazi  8192 2006-06-14 09:03 musik
drwx------   2 bazi bazi  4096 2006-06-30 10:57 MyDownloads
drwxr-xr-x   3 bazi bazi  4096 2006-06-29 11:14 .nautilus
drwxr-x---   2 bazi bazi  4096 2006-06-29 12:11 .ntrc_2
drwx------   3 bazi bazi  4096 2006-06-29 16:14 .openoffice.org2
drwxr-xr-x   9 bazi bazi  4096 2006-07-06 07:21 .opera
drwxr-xr-x   3 bazi bazi  4096 2006-06-14 15:17 pictures
drwxr-xr-x   2 bazi bazi  4096 2006-06-29 14:43 .qt
-rw-------   1 bazi bazi     0 2006-06-29 12:44 radeon~
-rw-------   1 bazi bazi  2480 2006-07-06 07:50 .recently-used
-rw-r--r--   1 bazi bazi   237 2006-06-30 10:59 .registry
drwx------   3 bazi bazi  4096 2006-07-04 08:12 .scim
drwx------   3 bazi bazi  4096 2006-07-06 00:50 .Skype
-rw-r--r--   1 bazi bazi     0 2006-06-29 11:16 .sudo_as_admin_successful
drwx------   2 bazi bazi  4096 2006-07-06 07:35 .synce
drwxr-xr-x   2 bazi bazi  4096 2006-07-06 07:49 sync_test
drwxr-xr-x   2 bazi bazi  4096 2006-06-29 23:48 .themes
drwx------   4 bazi bazi  4096 2006-06-29 22:44 .thumbnails
drwx------   5 bazi bazi  4096 2006-06-30 10:57 .Trash
-rw-r--r--   1 bazi bazi 24803 2006-06-27 16:30 Ubuntu_Dapper_Installation_Guide
drwx------   2 bazi bazi  4096 2006-06-30 08:50 .update-notifier
drwxr-xr-x   2 bazi bazi  4096 2005-11-22 10:43 vpnclient
drwxr-xr-x   2 bazi bazi  4096 2006-07-04 20:06 .wapi
-rw-------   1 bazi bazi   119 2006-07-06 07:05 .Xauthority
drwxr-xr-x   4 bazi bazi  4096 2006-06-29 15:15 .xmms
-rw-r--r--   1 bazi bazi  4844 2006-07-05 08:42 .Xscrc
-rw-r--r--   1 bazi bazi  8093 2006-07-06 07:57 .xsession-errors
drwxr-xr-x   2 bazi bazi  4096 2006-07-05 08:27 xten-xlite

```

thanks

---

### Post by aysiu on 2006-07-06
Well, the top-level directories look okay. Can you try this? ```
cp -R ~/.mozilla ~/.mozilla.backup
cp -R ~/.opera ~/.opera.backup
sudo chown -R bazi:bazi ~/.mozilla
sudo chown -R bazi:bazi ~/.opera
``` and then see if you still have those problems? It's possible that somehow the lower-level directories may have changed ownership.

---

### Post by blackpaw on 2006-07-08
hmmm.. Firefox now remembers :)

streamtuner won't :(

[edit: offtopic]

I now changed some permissions and it runs much better now. But not perfect.

thanks 


andreas

---

### Post by blackpaw on 2006-07-09
nm

---

### Post by blackpaw on 2006-07-12
There is a new problem... maybe it's related...

Trying to open font manager it says:
> Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

what did I do wrong???


andreas

---

### Post by blackpaw on 2006-07-19
another weird thing.. 

when I try to set mp3-tags they are "forgotten" after a reboot, too
I set permissions and ownership on the music folder, no change. 
Reboot and everything is as I began with last time.

Can I just reinstall ubuntu over my installation?
Is there some disaster-recovery switch that will re-create permissions and users rights?

help anyone?


andreas

---

### Post by Ramses de Norre on 2006-07-19
```

sudo chown -R bazi:bazi ~/
chmod -R u+rwx ~/
chmod 600 ~/.Xauthority

```

---

### Post by Jofaba on 2007-08-12
I have this problem as well. For the life of me I can't find an answer =(

I absolutely need to find a fix for this. I can't lose everything everytime I turn my computer off. Does anyone know how to fix this?

---

### Post by cainmark on 2007-11-25
> **Jofaba said:**
> I have this problem as well. For the life of me I can't find an answer =(

I absolutely need to find a fix for this. I can't lose everything everytime I turn my computer off. Does anyone know how to fix this?

Read Ramses de Norre post right above yours. Open a terminal, enter each line one at a time, and
 replace bazi:bazi with the name of your home folder on each side of the colon.  

I had the same problem and that fixed most of my issues.

---

