---
title: "Will not back up to external drive 14.04 &amp; 14.10"
date: 2014-10-27
forum: General Help
---

### Post by Cloggsy on 2014-10-27
Our computer has three users - all as administrators plus the usual guest login. While running 12.04LTS I set up the backup software to automatically back up each user to an external HDD connected via a USB. What would happen would be that the first person to log in on first boot would find the drive automatically mounted and, if due a backup, this would automatically take place. Since upgrade to 14.04 and subsequently 14.10 this has failed.

The first user is me and the backup system has continued to work perfectly; however, for my wife and daughter as the other two users it has not been possible to back up since upgrading to 14.04 in May. The automatic system fails and a manual attempt receives a dialog box saying that there are no permissions. The drive is mounted OK and the files are present if viewed through the file manager. I've clicked on the "permissions" tab and attempted to change them but they refuse to change.

---

### Post by nerdtron on 2014-10-27
The backup programs run as sudo or root?

---

### Post by Cloggsy on 2014-10-27
Erm...
...my guess is neither as it's the backup software shipped with the distribution.

---

### Post by nerdtron on 2014-10-27
ahh.. so we need to change permissions. The file to be backed up are on the home folder of each user right?

First let's see the current permissionsfo folders and files. Let's see the output of:
```
sudo ls -lah /home/
sudo ls -lah /home/user1
sudo ls -lah /home/user2
sudo ls -lah /home/user3

```

BTW what is the filesystem of the mounted external drive?
Let's also see the permissions of the destination of the backup.
```
 sudo ls -lah /folder/of/external/drive 
```

---

### Post by yancek on 2014-10-27
> The automatic system fails and a manual attempt receives a dialog box saying that there are no permissions. 

What manual attempt, how exactly are you doing this?  If you are doing it from a terminal, you need to precede the command with "sudo", if you are doing it from a file manager it must be open with root privileges, i.e.  gksu nautilus.  If you are doing it using the "Backups" software under System Settings, maybe something changed with the upgrade.   If someone has sudo privileges, they are not in use any time that user is logged in, you still need to give yourself "root" or "sudo" privileges.  More details on exactly how you are doing this.  Also, it would be useful to know the permissions on the directory "to" which you are writing the backups.

---

### Post by CaptainMark on 2014-10-27
I can't remember off hand exactly which release it was changed with but I hit the same problem when Ubuntu all of a sudden went from mounting external media in /media to mounting it in /media/user and my backup scripts all stopped working, a simple way round it is to use fstab to mount your backup drive in /media [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) and set the appropriate permissions as already recommended

---

### Post by Cloggsy on 2014-10-28
For NERDTRON

andrew@allcock-server:~$ sudo ls -lah /home/
[sudo] password for andrew: 
total 32K
drwxr-xr-x  6 root      root      4.0K Feb  3  2012 .
drwxr-xr-x 22 root      root      4.0K Oct 27 12:14 ..
drwxr-xr-x 62 andrew    andrew    4.0K Oct 28 11:32 andrew
drwxr-xr-x 32 guest     guest     4.0K Jun  7 09:23 guest
drwxr-xr-x 48 katherine katherine  12K Oct 28 11:29 katherine
drwxr-xr-x 54 rachel    rachel    4.0K Oct 19 19:33 rachel
andrew@allcock-server:~$ sudo ls -lah /home/user1
ls: cannot access /home/user1: No such file or directory
andrew@allcock-server:~$ sudo ls -lah /home/andrew
ls: cannot access /home/andrew/WualaDrive: Permission denied
total 1.4M
drwxr-xr-x 62 andrew andrew 4.0K Oct 28 11:32 .
drwxr-xr-x  6 root   root   4.0K Feb  3  2012 ..
drwx------  3 andrew andrew 4.0K May 27  2011 .adobe
-rw-------  1 andrew andrew   57 Oct 28 12:23 .bash_history
-rw-r--r--  1 andrew andrew  220 May 27  2011 .bash_logout
-rw-r--r--  1 andrew andrew 3.1K May 27  2011 .bashrc
drwxrwxr-x  6 andrew andrew 4.0K Feb 11  2013 .bibletime
lrwxrwxrwx  1 andrew andrew   31 Aug 13  2011 .byobu -> /home/andrew/.local/share/byobu
drwx------ 48 andrew andrew 4.0K Aug 25 11:52 .cache
drwxrwxr-x  6 andrew andrew 4.0K Nov 15  2013 .clamtk
drwx------  3 andrew andrew 4.0K Jun  6 11:57 .compiz
drwxrwxr-x  3 andrew andrew 4.0K Sep 16  2012 .compiz-1
drwxr-xr-x 52 andrew andrew 4.0K Oct 27 13:51 .config
drwx------  3 andrew andrew 4.0K May 27  2011 .dbus
-rw-rw-r--  1 andrew andrew 200K Aug 12 11:14 DefAc Headed.doc
drwxrwxrwx  2 andrew andrew 4.0K Oct 27 14:30 Desktop
-rw-r--r--  1 andrew andrew   93 Jun  7 17:09 .dmrc
drwxrwxrwx 18 andrew andrew 4.0K Jul  5 11:09 Documents
drwxrwxrwx  2 andrew andrew 4.0K Oct 17 08:13 Downloads
-rw-------  1 andrew andrew   16 May 27  2011 .esd_auth
-rw-r--r--  1 andrew andrew  179 May 27  2011 examples.desktop
-rw-r--r--  1 andrew andrew 5.4K Aug 13  2011 .face
-rw-r--r--  1 andrew andrew 661K Jan 24  2013 Firefox_wallpaper.png
drwx------  2 andrew andrew 4.0K May 24  2013 .fluendo-dvd
drwxr-xr-x  2 andrew andrew 4.0K Jun  6 07:08 fontconfig
drwxr-xr-x  2 andrew andrew 4.0K Jun  6 07:08 .fontconfig
drwx------  5 andrew andrew 4.0K Oct 28 11:32 .gconf
drwx------  2 andrew andrew 4.0K Sep 16  2012 .gconfd
drwx------  4 andrew andrew 4.0K Jun 22  2013 .gegl-0.0
drwxr-xr-x 22 andrew andrew 4.0K Feb 28  2014 .gimp-2.6
drwxr-xr-x 24 andrew andrew 4.0K Oct 17 10:26 .gimp-2.8
-rw-r-----  1 andrew andrew    0 Jun  5 21:36 .gksu.lock
drwx------  8 andrew andrew 4.0K Sep 27 19:51 .gnome2
drwx------  2 andrew andrew 4.0K May 27  2011 .gnome2_private
drwx------  2 andrew andrew 4.0K Oct 27 09:29 .gnupg
-rw-------  1 andrew andrew    0 Oct  7  2013 .goutputstream-0TEP4W
-rw-------  1 andrew andrew    0 Sep 24  2012 .goutputstream-1L67KW
-rw-------  1 andrew andrew    0 Oct 11  2012 .goutputstream-1QF7LW
-rw-------  1 andrew andrew    0 Sep 24  2012 .goutputstream-24QMLW
-rw-------  1 andrew andrew    0 Jun 15  2013 .goutputstream-2A18XW
-rw-------  1 andrew andrew    0 Feb 25  2013 .goutputstream-2RQMSW
-rw-------  1 andrew andrew    0 Jan 12  2013 .goutputstream-3DT0QW
-rw-------  1 andrew andrew    0 Feb 14  2014 .goutputstream-3WMQAX
-rw-------  1 andrew andrew    0 May 17 17:34 .goutputstream-3WN2FX
-rw-------  1 andrew andrew    0 Apr 24  2014 .goutputstream-417GEX
-rw-------  1 andrew andrew    0 Feb  1  2014 .goutputstream-4S9OAX
-rw-------  1 andrew andrew    0 Sep 27  2013 .goutputstream-5EE53W
-rw-------  1 andrew andrew    0 Jun 16  2013 .goutputstream-60DOYW
-rw-------  1 andrew andrew    0 Feb 23  2013 .goutputstream-60SZSW
-rw-------  1 andrew andrew    0 Mar  8  2013 .goutputstream-6BGCTW
-rw-------  1 andrew andrew    0 Aug 31  2013 .goutputstream-A8IN2W
-rw-------  1 andrew andrew    0 Sep 17  2012 .goutputstream-A8UNKW
-rw-------  1 andrew andrew    0 Aug 16  2013 .goutputstream-AI9R1W
-rw-------  1 andrew andrew    0 Jun 23  2013 .goutputstream-BG8EZW
-rw-------  1 andrew andrew    0 Dec  7  2013 .goutputstream-BYEM7W
-rw-------  1 andrew andrew    0 Sep 17  2012 .goutputstream-BZFYKW
-rw-------  1 andrew andrew    0 Oct 12  2012 .goutputstream-D7LAMW
-rw-------  1 andrew andrew    0 Jun 29  2013 .goutputstream-DUL1YW
-rw-------  1 andrew andrew    0 Sep 16  2013 .goutputstream-FF0P3W
-rw-------  1 andrew andrew    0 May 25  2013 .goutputstream-FINTXW
-rw-------  1 andrew andrew    0 Jul 15  2013 .goutputstream-G3NC0W
-rw-------  1 andrew andrew    0 Jan 18  2013 .goutputstream-L89UQW
-rw-------  1 andrew andrew    0 Mar 10  2013 .goutputstream-LA0LTW
-rw-------  1 andrew andrew    0 Jan 27  2013 .goutputstream-LKCHRW
-rw-------  1 andrew andrew    0 Sep  2  2013 .goutputstream-MKN62W
-rw-------  1 andrew andrew    0 Jul  8  2013 .goutputstream-MREYZW
-rw-------  1 andrew andrew    0 Jul 14  2013 .goutputstream-NLFQ0W
-rw-------  1 andrew andrew    0 Jan 27  2014 .goutputstream-NQN79W
-rw-------  1 andrew andrew    0 Sep 30  2012 .goutputstream-OOVBLW
-rw-------  1 andrew andrew    0 Nov 30  2013 .goutputstream-P1NL7W
-rw-------  1 andrew andrew    0 Oct  4  2013 .goutputstream-PUY73W
-rw-------  1 andrew andrew    0 Jan  4  2014 .goutputstream-Q1638W
-rw-------  1 andrew andrew    0 Jan 27  2014 .goutputstream-Q9H59W
-rw-------  1 andrew andrew    0 Sep  9  2013 .goutputstream-QDIT2W
-rw-------  1 andrew andrew    0 Jul  1  2013 .goutputstream-REEIZW
-rw-------  1 andrew andrew    0 Jul  7  2013 .goutputstream-RQ2NZW
-rw-------  1 andrew andrew    0 Feb 15  2013 .goutputstream-T1S8RW
-rw-------  1 andrew andrew    0 Jan 24  2013 .goutputstream-U2HURW
-rw-------  1 andrew andrew    0 Sep 16  2012 .goutputstream-VQUMKW
-rw-------  1 andrew andrew    0 Mar 29  2014 .goutputstream-WP6MDX
-rw-------  1 andrew andrew    0 Jul 28  2013 .goutputstream-WV340W
-rw-------  1 andrew andrew    0 Aug  3  2013 .goutputstream-XKUR0W
-rw-------  1 andrew andrew    0 Sep 24  2012 .goutputstream-YZKDLW
-rw-------  1 andrew andrew    0 Jan 20  2014 .goutputstream-ZVBV9W
-rw-------  1 andrew andrew    0 May 28  2013 .goutputstream-ZVV0XW
drwxr-xr-x  3 andrew andrew 4.0K Jun 12 20:40 .gstreamer-0.10
-rw-rw-r--  1 andrew andrew  297 Jun  7 16:42 .gtk-bookmarks
drwx------  2 andrew andrew 4.0K May 27  2011 .gvfs
drwxr-----  2 andrew andrew 4.0K Aug  8  2011 .hplip
-rw-------  1 andrew andrew 144K Oct 28 11:32 .ICEauthority
drwxr-xr-x  5 andrew andrew 4.0K May 19  2013 .icedtea
drwxr-xr-x  2 andrew andrew 4.0K Aug 13  2011 .icons
drwx------  3 andrew andrew 4.0K Sep 30  2012 .launchpadlib
drwxr-xr-x  3 andrew andrew 4.0K May 29  2011 .libreoffice
-rw-------  1 andrew andrew 2.0K Dec  7  2013 .linphonerc
drwx------  3 andrew andrew 4.0K May 27  2011 .local
drwx------  3 andrew andrew 4.0K May 27  2011 .macromedia
drwx------  3 andrew andrew 4.0K May 31  2011 .mission-control
drwx------  4 andrew andrew 4.0K May 28  2011 .mozilla
drwxr-xr-x 19 andrew andrew 4.0K Apr  4  2014 Music
drwxrwxr-x  2 andrew andrew 4.0K Feb  8  2014 My PageManager
drwxrwxr-x  2 andrew andrew 4.0K Jul  5 13:01 My Pictures
drwxr-xr-x  2 andrew andrew 4.0K May 20  2012 .OpenSong
drwxrwxrwx 15 andrew andrew 4.0K Aug 16 10:11 Pictures
drwx------  3 andrew andrew 4.0K Feb 16  2012 .pki
-rw-r--r--  1 andrew andrew  675 May 27  2011 .profile
drwxr-xr-x  2 andrew andrew 4.0K May 27  2011 Public
drwx------  2 andrew andrew 4.0K Oct 27 09:29 .pulse
-rw-------  1 andrew andrew  256 May 27  2011 .pulse-cookie
drwx------  2 andrew andrew 4.0K Jan 20  2014 .remmina
-rw-r--r--  1 andrew andrew    0 Aug 13  2011 .screenrc
drwxr-xr-x  2 andrew andrew 4.0K May 29  2011 .shotwell
drwx------  6 andrew andrew 4.0K Dec  7  2013 .Skype
drwx------  2 andrew andrew 4.0K Jun  7 09:21 .ssh
drwxr-xr-x  4 andrew andrew 4.0K Jan 28  2012 .stellarium
-rw-r--r--  1 andrew andrew    0 May 27  2011 .sudo_as_admin_successful
drwx------  5 andrew andrew 4.0K Feb 14  2013 .sword
drwxr-xr-x  2 andrew andrew 4.0K May 27  2011 Templates
drwxr-xr-x  2 andrew andrew 4.0K Aug 13  2011 .themes
drwx------  5 andrew andrew 4.0K Jan 11  2013 .thumbnails
drwx------  4 andrew andrew 4.0K Oct 12  2012 .thunderbird
drwxrwxr-x  2 andrew andrew 4.0K May 28  2011 Ubuntu One
drwx------  2 andrew andrew 4.0K May 27  2011 .update-notifier
drwxr-xr-x  3 andrew andrew 4.0K May 27  2011 Videos
drwxrwxrwx 33 andrew andrew  12K May  2 16:25 Windows Files
drwxrwxr-x  4 andrew andrew 4.0K Jul  5 13:02 .wine
drwxrwxr-x  6 andrew andrew 4.0K Apr 10  2014 wuala
drwxrwxr-x  7 andrew andrew 4.0K Oct 28 11:32 .wuala
d?????????  ? ?      ?         ?            ? WualaDrive
-rw-------  1 andrew andrew  177 Oct 28 11:32 .Xauthority
drwx------  4 andrew andrew 4.0K Sep 27 19:50 .xiphos
-rw-rw-r--  1 andrew andrew 7.4K May 24  2013 .xscreensaver
-rw-------  1 andrew andrew  826 Oct 28 11:32 .xsession-errors
-rw-------  1 andrew andrew 1.1K Oct 28 11:26 .xsession-errors.old
andrew@allcock-server:~$ sudo ls -lah /home/katherine
total 9.8M
drwxr-xr-x 48 katherine katherine  12K Oct 28 11:29 .
drwxr-xr-x  6 root      root      4.0K Feb  3  2012 ..
drwx------  3 katherine katherine 4.0K May 28  2011 .adobe
-rw-r--r--  1 katherine katherine  220 May 27  2011 .bash_logout
-rw-r--r--  1 katherine katherine 3.1K May 27  2011 .bashrc
drwx------ 41 katherine katherine 4.0K Oct 28 11:31 .cache
drwxrwxr-x  6 katherine katherine 4.0K Nov 15  2013 .clamtk
drwx------  3 katherine katherine 4.0K Jun  4 20:08 .compiz
drwxrwxr-x  3 katherine katherine 4.0K Sep 17  2012 .compiz-1
drwxr-xr-x 39 katherine katherine 4.0K Oct 27 13:46 .config
drwx------  3 katherine katherine 4.0K May 28  2011 .dbus
drwxr-xr-x  2 katherine katherine 4.0K Jun  8 20:10 Desktop
-rw-r--r--  1 katherine katherine   78 Jul  2 20:09 .dmrc
drwxrwxrwx 22 katherine katherine  12K Mar  5  2014 Documents
drwxrwxrwx  2 katherine katherine 4.0K Jun 14 10:18 Downloads
-rw-------  1 katherine katherine   16 May 28  2011 .esd_auth
-rw-r--r--  1 katherine katherine  179 May 27  2011 examples.desktop
-rw-r--r--  1 katherine katherine  18K Apr 24  2012 .face
-rw-r--r--  1 katherine katherine 1.4M Jun 13  2012 Firefox_wallpaper.png
drwx------  2 katherine katherine 4.0K Aug 13  2011 .fluendo-dvd
drwxr-xr-x  2 katherine katherine 4.0K Jan 15  2014 .fontconfig
drwx------  5 katherine katherine 4.0K Oct 28 11:29 .gconf
drwx------  2 katherine katherine 4.0K Sep 16  2012 .gconfd
-rw-r--r--  1 katherine katherine 3.2K Jun 12  2012 give.gif
drwx------  8 katherine katherine 4.0K Jul 21 21:37 .gnome2
drwx------  2 katherine katherine 4.0K May 28  2011 .gnome2_private
drwx------  2 katherine katherine 4.0K Jul  2 20:01 .gnupg
-rw-------  1 katherine katherine    0 May 14 19:47 .goutputstream-118AGX
-rw-------  1 katherine katherine    0 Apr 17  2013 .goutputstream-18EPVW
-rw-------  1 katherine katherine    0 Jul 16  2013 .goutputstream-1GO9ZW
-rw-------  1 katherine katherine    0 Mar 25  2014 .goutputstream-1IQCDX
-rw-------  1 katherine katherine    0 May  7 19:59 .goutputstream-1O28EX
-rw-------  1 katherine katherine    0 Sep 17  2012 .goutputstream-1PVMKW
-rw-------  1 katherine katherine    0 Jan 21  2013 .goutputstream-26FRQW
-rw-------  1 katherine katherine    0 Aug 20  2013 .goutputstream-2CZZ1W
-rw-------  1 katherine katherine    0 Jan 20  2014 .goutputstream-2SWW9W
-rw-------  1 katherine katherine    0 Sep 25  2013 .goutputstream-34N63W
-rw-------  1 katherine katherine    0 Dec 28  2012 .goutputstream-3D8VPW
-rw-------  1 katherine katherine   59 Nov 19  2012 .goutputstream-3U6QNW
-rw-------  1 katherine katherine    0 May 21 19:22 .goutputstream-4I71FX
-rw-------  1 katherine katherine    0 Dec  2  2012 .goutputstream-4KAEOW
-rw-------  1 katherine katherine    0 May  6 11:57 .goutputstream-4OQNFX
-rw-------  1 katherine katherine    0 Dec 14  2012 .goutputstream-4R45OW
-rw-------  1 katherine katherine    0 Jan 29  2013 .goutputstream-4V3XRW
-rw-------  1 katherine katherine    0 Apr  7  2014 .goutputstream-55DVDX
-rw-------  1 katherine katherine    0 Mar 17  2014 .goutputstream-585VCX
-rw-------  1 katherine katherine    0 May 21 19:06 .goutputstream-5A9YFX
-rw-------  1 katherine katherine    0 Feb  6  2013 .goutputstream-5BC2RW
-rw-------  1 katherine katherine   59 Oct 31  2012 .goutputstream-5QD8MW
-rw-------  1 katherine katherine   59 Nov  9  2012 .goutputstream-5STDNW
-rw-------  1 katherine katherine    0 Apr 14  2014 .goutputstream-6AJ4DX
-rw-------  1 katherine katherine    0 May  5 14:27 .goutputstream-6E9IFX
-rw-------  1 katherine katherine   59 Nov  5  2012 .goutputstream-6H3CNW
-rw-------  1 katherine katherine    0 Sep 18  2012 .goutputstream-76KRKW
-rw-------  1 katherine katherine    0 Feb  5  2013 .goutputstream-7MT9RW
-rw-------  1 katherine katherine    0 Sep 12  2013 .goutputstream-7XKA3W
-rw-------  1 katherine katherine    0 Oct  1  2012 .goutputstream-868PLW
-rw-------  1 katherine katherine    0 May  2  2013 .goutputstream-8FPYWW
-rw-------  1 katherine katherine   59 Nov 20  2012 .goutputstream-8HYQNW
-rw-------  1 katherine katherine    0 Mar  9  2014 .goutputstream-8Q97BX
-rw-------  1 katherine katherine   59 Nov  2  2012 .goutputstream-8TILNW
-rw-------  1 katherine katherine    0 May  3  2013 .goutputstream-8Y2QWW
-rw-------  1 katherine katherine    0 Jan 30  2013 .goutputstream-9OAORW
-rw-------  1 katherine katherine    0 May  1 17:04 .goutputstream-AEGJFX
-rw-------  1 katherine katherine    0 Oct 15  2013 .goutputstream-APRX4W
-rw-------  1 katherine katherine    0 Apr 30  2013 .goutputstream-B1MWWW
-rw-------  1 katherine katherine    0 Feb 10  2014 .goutputstream-BYV2AX
-rw-------  1 katherine katherine    0 Jan 15  2013 .goutputstream-CJH6QW
-rw-------  1 katherine katherine   59 Nov  9  2012 .goutputstream-CKZ1MW
-rw-------  1 katherine katherine    0 Dec  4  2012 .goutputstream-CNEVOW
-rw-------  1 katherine katherine    0 Nov 28  2012 .goutputstream-CODCOW
-rw-------  1 katherine katherine    0 Nov 25  2012 .goutputstream-CWBAOW
-rw-------  1 katherine katherine    0 Sep 24  2012 .goutputstream-DG6FLW
-rw-------  1 katherine katherine    0 Jan 28  2014 .goutputstream-DJVNAX
-rw-------  1 katherine katherine    0 Jun  4  2013 .goutputstream-DR94XW
-rw-------  1 katherine katherine    0 Sep 24  2012 .goutputstream-DV5NLW
-rw-------  1 katherine katherine    0 May 12 20:57 .goutputstream-E9S7FX
-rw-------  1 katherine katherine    0 Oct 11  2012 .goutputstream-ERBTLW
-rw-------  1 katherine katherine    0 Jan 26  2014 .goutputstream-ERCBAX
-rw-------  1 katherine katherine    0 May  6 13:01 .goutputstream-EWV3EX
-rw-------  1 katherine katherine    0 Jan 14  2013 .goutputstream-EZJXQW
-rw-------  1 katherine katherine    0 Dec  5  2012 .goutputstream-F82MOW
-rw-------  1 katherine katherine    0 Nov 24  2012 .goutputstream-FGBCOW
-rw-------  1 katherine katherine    0 Oct  8  2012 .goutputstream-FH21LW
-rw-------  1 katherine katherine    0 May  1  2013 .goutputstream-FOFLWW
-rw-------  1 katherine katherine    0 Sep 17  2013 .goutputstream-G8LS3W
-rw-------  1 katherine katherine    0 Jan 22  2013 .goutputstream-GGTUQW
-rw-------  1 katherine katherine    0 May 20 07:21 .goutputstream-GL9RFX
-rw-------  1 katherine katherine    0 Dec 28  2012 .goutputstream-HPVWPW
-rw-------  1 katherine katherine    0 Sep 19  2012 .goutputstream-IBFIKW
-rw-------  1 katherine katherine    0 Feb 28  2013 .goutputstream-IMV2SW
-rw-------  1 katherine katherine    0 Oct 26  2013 .goutputstream-IO9D5W
-rw-------  1 katherine katherine    0 May  5  2013 .goutputstream-J1PGWW
-rw-------  1 katherine katherine    0 Feb  5  2014 .goutputstream-JCY9AX
-rw-------  1 katherine katherine    0 Mar 24  2014 .goutputstream-JG4KDX
-rw-------  1 katherine katherine    0 Dec  1  2012 .goutputstream-JG8MOW
-rw-------  1 katherine katherine    0 Mar 27  2014 .goutputstream-JJZFDX
-rw-------  1 katherine katherine    0 May 29 15:35 .goutputstream-JNCKGX
-rw-------  1 katherine katherine    0 Feb  3  2013 .goutputstream-JOJGRW
-rw-------  1 katherine katherine    0 Jun  2 20:55 .goutputstream-K64PGX
-rw-------  1 katherine katherine    0 Dec  8  2012 .goutputstream-K8P8OW
-rw-------  1 katherine katherine    0 Oct  9  2013 .goutputstream-K9GL4W
-rw-------  1 katherine katherine    0 May 20 12:25 .goutputstream-MI07FX
-rw-------  1 katherine katherine    0 Feb 26  2013 .goutputstream-MUQ4SW
-rw-------  1 katherine katherine    0 Oct 30  2013 .goutputstream-MXW35W
-rw-------  1 katherine katherine    0 Oct 10  2012 .goutputstream-N440LW
-rw-------  1 katherine katherine    0 Mar 24  2013 .goutputstream-NQ95TW
-rw-------  1 katherine katherine   59 Nov  8  2012 .goutputstream-O4QBNW
-rw-------  1 katherine katherine    0 Dec 17  2012 .goutputstream-OI26OW
-rw-------  1 katherine katherine    0 Jun 12  2013 .goutputstream-P2DTYW
-rw-------  1 katherine katherine    0 Feb 11  2014 .goutputstream-PK63AX
-rw-------  1 katherine katherine    0 May 30 16:36 .goutputstream-QFCXGX
-rw-------  1 katherine katherine    0 Sep 18  2012 .goutputstream-QN2YKW
-rw-------  1 katherine katherine    0 Apr 29 20:22 .goutputstream-QSQREX
-rw-------  1 katherine katherine    0 Mar 12  2014 .goutputstream-RCWVCX
-rw-------  1 katherine katherine    0 Nov 28  2013 .goutputstream-RCXI7W
-rw-------  1 katherine katherine    0 Apr 20  2013 .goutputstream-ROH5VW
-rw-------  1 katherine katherine   59 Nov 21  2012 .goutputstream-RRM6NW
-rw-------  1 katherine katherine    0 Nov 24  2013 .goutputstream-RWH96W
-rw-------  1 katherine katherine    0 Jun  3 18:01 .goutputstream-RYTNGX
-rw-------  1 katherine katherine   59 Nov 20  2012 .goutputstream-SAVUNW
-rw-------  1 katherine katherine    0 Mar 30  2014 .goutputstream-SQAHDX
-rw-------  1 katherine katherine    0 Oct 27  2012 .goutputstream-TD3OMW
-rw-------  1 katherine katherine    0 Nov 25  2013 .goutputstream-TDR66W
-rw-------  1 katherine katherine    0 Feb  4  2014 .goutputstream-U9GUAX
-rw-------  1 katherine katherine    0 May 11 16:18 .goutputstream-ULRMFX
-rw-------  1 katherine katherine    0 Nov 26  2012 .goutputstream-URRDOW
-rw-------  1 katherine katherine    0 May 11 21:20 .goutputstream-VGYLFX
-rw-------  1 katherine katherine    0 May 14 17:59 .goutputstream-VRF3FX
-rw-------  1 katherine katherine    0 May 26 16:31 .goutputstream-W5SIGX
-rw-------  1 katherine katherine    0 Nov 13  2013 .goutputstream-W9YP6W
-rw-------  1 katherine katherine    0 May  6 20:59 .goutputstream-WSEEFX
-rw-------  1 katherine katherine    0 Mar 18  2014 .goutputstream-WZQSCX
-rw-------  1 katherine katherine    0 Jan 25  2014 .goutputstream-X40BAX
-rw-------  1 katherine katherine    0 Nov 12  2013 .goutputstream-XG2P6W
-rw-------  1 katherine katherine    0 Apr  6  2014 .goutputstream-XO95DX
-rw-------  1 katherine katherine    0 Jun 13  2013 .goutputstream-XRMLYW
-rw-------  1 katherine katherine    0 Sep 24  2012 .goutputstream-XSLLLW
-rw-------  1 katherine katherine    0 Nov  7  2013 .goutputstream-XYL95W
-rw-------  1 katherine katherine    0 Mar 23  2014 .goutputstream-YF81CX
-rw-------  1 katherine katherine    0 Jan  7  2014 .goutputstream-YXUB9W
-rw-------  1 katherine katherine    0 Apr 28  2013 .goutputstream-ZA9SVW
-rw-------  1 katherine katherine    0 Jun 25  2013 .goutputstream-ZTU7YW
drwxr-xr-x  2 katherine katherine 4.0K Jun  9 19:19 .gstreamer-0.10
-rw-rw-r--  1 katherine katherine  157 Jun  8 20:03 .gtk-bookmarks
drwx------  2 katherine katherine 4.0K May 28  2011 .gvfs
drwxr-----  2 katherine katherine 4.0K Nov 27  2011 .hplip
-rw-------  1 katherine katherine 203K Oct 28 11:29 .ICEauthority
drwxr-xr-x  4 katherine katherine 4.0K Oct 10  2011 .icedtea
drwxr-xr-x  2 katherine katherine 4.0K Jul 30  2011 .icons
drwxrwxr-x  3 katherine katherine 4.0K Nov 26  2012 .java
drwx------  3 katherine katherine 4.0K Jan 29  2013 .launchpadlib
drwxr-xr-x  3 katherine katherine 4.0K Jun  8  2011 .libreoffice
-rw-r--r--  1 katherine katherine 5.0K Jun  8 20:10 .linphone-history.db
-rw-------  1 katherine katherine 6.1K Aug 26 17:51 .linphonerc
drwxr-xr-x  3 katherine katherine 4.0K May 28  2011 .local
drwx------  3 katherine katherine 4.0K May 28  2011 .macromedia
drwx------  3 katherine katherine 4.0K Sep 17  2012 .mission-control
drwx------  4 katherine katherine 4.0K May 29  2011 .mozilla
drwxr-xr-x  3 katherine katherine 4.0K Jun  8 20:08 Music
drwxr-xr-x 18 katherine katherine 4.0K Feb 24  2012 Old Computer
drwxr-x---  6 katherine katherine 4.0K Jun 14  2011 .openshot
drwxr-xr-x  5 katherine katherine 4.0K Jul 23 22:15 Pictures
drwx------  3 katherine katherine 4.0K Jul 16  2011 .pki
-rw-r--r--  1 katherine katherine  675 May 27  2011 .profile
drwxr-xr-x  2 katherine katherine 4.0K May 28  2011 Public
drwx------  2 katherine katherine 4.0K Jun  4 19:33 .pulse
-rw-------  1 katherine katherine  256 May 28  2011 .pulse-cookie
-rw-r--r--  1 katherine katherine  22K Sep  6  2011 School request.odt
-rw-r--r--  1 katherine katherine 527K Jul 12  2011 Screenshot-1.png
drwxr-xr-x  4 katherine katherine 4.0K Nov 20  2012 .shotwell
drwx------  8 katherine katherine 4.0K Oct 21 22:01 .Skype
-rw-r--r--  1 katherine katherine 1.1M Jan 30  2012 slave.gif
drwx------  2 katherine katherine 4.0K Jul  2 20:01 .ssh
drwxr-xr-x  2 katherine katherine 4.0K May 28  2011 Templates
drwxr-xr-x  2 katherine katherine 4.0K Jul 30  2011 .themes
drwx------  5 katherine katherine 4.0K Nov  2  2011 .thumbnails
drwx------  4 katherine katherine 4.0K Dec  1  2012 .thunderbird
drwxrwxr-x  2 katherine katherine 4.0K Jun 18  2011 Ubuntu One
-rw-r--r--  1 katherine katherine 6.3M Oct  2  2012 video-2012-10-02-18-52-02.mp4
drwxr-xr-x  3 katherine katherine 4.0K Nov  6  2011 Videos
drwxrwxr-x  4 katherine katherine 4.0K Sep 26  2012 .wine
-rw-------  1 katherine katherine  354 Oct 28 11:31 .Xauthority
-rw-r--r--  1 katherine katherine  834 Nov  2  2011 .xscreensaver-getimage.cache
-rw-------  1 katherine katherine  982 Oct 28 11:31 .xsession-errors
-rw-------  1 katherine katherine 1.4K Oct 28 11:28 .xsession-errors.old
andrew@allcock-server:~$ sudo ls -lah /home/rachel
total 2.5M
drwxr-xr-x 54 rachel rachel 4.0K Oct 19 19:33 .
drwxr-xr-x  6 root   root   4.0K Feb  3  2012 ..
drwx------  3 rachel rachel 4.0K May 31  2011 .adobe
-rw-r--r--  1 rachel rachel  220 May 27  2011 .bash_logout
-rw-r--r--  1 rachel rachel 3.1K May 27  2011 .bashrc
drwx------ 43 rachel rachel 4.0K Oct 19 19:33 .cache
drwxrwxr-x  6 rachel rachel 4.0K Mar  2  2013 .clamtk
drwx------  3 rachel rachel 4.0K May  5 19:36 .compiz
drwxrwxr-x  3 rachel rachel 4.0K Sep 17  2012 .compiz-1
drwxr-xr-x 40 rachel rachel 4.0K Aug 22 18:08 .config
drwx------  3 rachel rachel 4.0K May 29  2011 .dbus
drwxr-xr-x  2 rachel rachel 4.0K Aug 29 18:55 Desktop
-rw-r--r--  1 rachel rachel   78 Sep  9 19:12 .dmrc
drwxrwxrwx 18 rachel rachel 4.0K Oct 14 21:10 Documents
drwxr-xr-x  5 rachel rachel 4.0K Oct 11 11:59 Downloads
-rw-------  1 rachel rachel 695K Sep 10  2012 DSC00158.JPG
-rw-------  1 rachel rachel   16 May 29  2011 .esd_auth
-rw-r--r--  1 rachel rachel  179 May 27  2011 examples.desktop
-rw-r--r--  1 rachel rachel  33K Sep 14  2011 .face
-rw-r--r--  1 rachel rachel 635K Apr 29  2012 Firefox_wallpaper.png
drwxr-xr-x  3 rachel rachel 4.0K Jun 12  2011 .fltk
drwx------  2 rachel rachel 4.0K Jul 22  2013 .fluendo-dvd
drwxr-xr-x  2 rachel rachel 4.0K Dec 22  2013 .fontconfig
drwxr-xr-x  2 rachel rachel 4.0K Oct 31  2013 .freemind
drwx------  4 rachel rachel 4.0K Oct 19 19:32 .gconf
drwx------  2 rachel rachel 4.0K Sep 16  2012 .gconfd
drwx------  4 rachel rachel 4.0K Nov  1  2013 .gegl-0.0
drwxr-xr-x 22 rachel rachel 4.0K Dec 22  2013 .gimp-2.6
-rw-r-----  1 rachel rachel    0 Oct  7  2012 .gksu.lock
drwx------  8 rachel rachel 4.0K Oct 14 21:18 .gnome2
drwx------  2 rachel rachel 4.0K May 31  2011 .gnome2_private
drwx------  2 rachel rachel 4.0K Sep  9 19:10 .gnupg
-rw-------  1 rachel rachel    0 Jul 11  2013 .goutputstream-1TQ0ZW
-rw-------  1 rachel rachel    0 Jul 23  2013 .goutputstream-2JEO0W
-rw-------  1 rachel rachel    0 Nov  8  2012 .goutputstream-49MINW
-rw-------  1 rachel rachel    0 Nov 24  2012 .goutputstream-69OFOW
-rw-------  1 rachel rachel    0 Sep 28  2013 .goutputstream-83TC4W
-rw-------  1 rachel rachel    0 Jan  7  2013 .goutputstream-8NCEQW
-rw-------  1 rachel rachel    0 Sep 29  2013 .goutputstream-9ZVB4W
-rw-------  1 rachel rachel    0 Jun 21  2013 .goutputstream-AJLEZW
-rw-------  1 rachel rachel    0 Oct 29  2012 .goutputstream-GH2YMW
-rw-------  1 rachel rachel    0 Dec 18  2012 .goutputstream-GSENPW
-rw-------  1 rachel rachel    0 Apr 14  2013 .goutputstream-K4QIVW
-rw-------  1 rachel rachel    0 Apr 28  2013 .goutputstream-KJE4VW
-rw-------  1 rachel rachel    0 Dec 17  2013 .goutputstream-KM2G8W
-rw-------  1 rachel rachel    0 Dec  8  2013 .goutputstream-M85U7W
-rw-------  1 rachel rachel    0 May  8  2013 .goutputstream-MFPDWW
-rw-------  1 rachel rachel    0 Oct  7  2012 .goutputstream-PUEWLW
-rw-------  1 rachel rachel    0 Feb 23  2014 .goutputstream-Q5WFBX
-rw-------  1 rachel rachel    0 Jun 23  2013 .goutputstream-QLBZYW
-rw-------  1 rachel rachel    0 Mar 18  2013 .goutputstream-RSG8TW
-rw-------  1 rachel rachel    0 Feb  3  2014 .goutputstream-RTE9AX
-rw-------  1 rachel rachel    0 Nov 20  2012 .goutputstream-SSU2NW
-rw-------  1 rachel rachel    0 Feb  3  2013 .goutputstream-T8FTRW
-rw-------  1 rachel rachel    0 Feb 11  2013 .goutputstream-VCE9RW
-rw-------  1 rachel rachel    0 Sep 29  2013 .goutputstream-VPZZ3W
-rw-------  1 rachel rachel    0 Jan 25  2014 .goutputstream-W3WJAX
-rw-------  1 rachel rachel    0 Jul 25  2013 .goutputstream-ZNV20W
drwxr-xr-x  3 rachel rachel 4.0K Apr 20  2014 .gstreamer-0.10
-rw-rw-r--  1 rachel rachel  298 Jul 22 14:44 .gtk-bookmarks
drwx------  2 rachel rachel 4.0K May 29  2011 .gvfs
drwxr-----  2 rachel rachel 4.0K Aug 30  2011 .hplip
-rw-------  1 rachel rachel 112K Oct 19 19:32 .ICEauthority
drwxr-xr-x  5 rachel rachel 4.0K Dec  1  2013 .icedtea
drwxr-xr-x  3 rachel rachel 4.0K Jun 25  2011 .java
drwx------  3 rachel rachel 4.0K Aug  6  2011 .kde
-rw-r--r--  1 rachel rachel 106K Jun 12  2011 .libquicktime_codecs
drwxr-xr-x  3 rachel rachel 4.0K May 31  2011 .libreoffice
-rw-------  1 rachel rachel 4.6K May  5 19:30 .linphonerc
drwxr-xr-x  3 rachel rachel 4.0K May 29  2011 .local
drwx------  3 rachel rachel 4.0K May 31  2011 .macromedia
drwx------  3 rachel rachel 4.0K Sep 17  2012 .mission-control
drwx------  4 rachel rachel 4.0K May 31  2011 .mozilla
drwxr-xr-x 10 rachel rachel 4.0K Aug 25  2013 Music
drwx------  3 rachel rachel 4.0K Jun 12  2011 .openme
-rw-r--r--  1 rachel rachel  358 Jun 12  2011 .openme.prefs
-rw-r--r--  1 rachel rachel   71 Jun 12  2011 .openme.presets
drwxr-x---  6 rachel rachel 4.0K Jun 12  2011 .openshot
drwxr-xr-x 18 rachel rachel 4.0K May  5 19:32 Pictures
drwx------  3 rachel rachel 4.0K Nov 16  2011 .pki
-rw-r--r--  1 rachel rachel  675 May 27  2011 .profile
drwxr-xr-x  2 rachel rachel 4.0K May 29  2011 Public
drwx------  2 rachel rachel 4.0K May  5 19:29 .pulse
-rw-------  1 rachel rachel  256 May 29  2011 .pulse-cookie
drwxr-xr-x  3 rachel rachel 4.0K Mar 17  2012 Rachel network server
drwxr-xr-x  2 rachel rachel 4.0K Apr  2  2012 .shotwell
drwx------  7 rachel rachel 4.0K Oct 19 20:02 .Skype
drwx------  2 rachel rachel 4.0K Sep  9 19:04 .ssh
drwxr-xr-x  2 rachel rachel 4.0K Apr 10  2014 Templates
drwx------  5 rachel rachel 4.0K Mar 31  2013 .thumbnails
drwx------  4 rachel rachel 4.0K Sep 22  2012 .thunderbird
drwxrwxr-x  2 rachel rachel 4.0K Sep 18  2012 Ubuntu One
-rw-rw-r--  1 rachel rachel 687K Oct 15 20:33 Untitled 1.doc
drwxr-xr-x  2 rachel rachel 4.0K Jun 12  2011 Video Projects
drwxr-xr-x  4 rachel rachel 4.0K Jan 12  2013 Videos
drwxr-xr-x  4 rachel rachel 4.0K Nov 19  2011 .wine
drwxrwxr-x  6 rachel rachel 4.0K Oct 19 19:33 .wuala
drwxrwxr-x  2 rachel rachel 4.0K Oct 19 19:33 WualaDrive
-rw-------  1 rachel rachel  295 Oct 19 20:02 .Xauthority
-rw-rw-r--  1 rachel rachel  131 Aug 29 14:13 .xinputrc
-rw-------  1 rachel rachel  562 Oct 19 20:02 .xsession-errors
-rw-------  1 rachel rachel  691 Oct 15 21:27 .xsession-errors.old
andrew@allcock-server:~$

---

### Post by Cloggsy on 2014-10-28
Hello Nerdtron
See also below
andrew@allcock-server:~$  sudo ls -lah /media/andrew/Elements
total 17K
drwx------  1 andrew andrew 4.0K Sep 18  2012 .
drwxr-x---+ 4 root   root   4.0K Oct 28 13:47 ..
drwx------  1 andrew andrew    0 May  5  2011 autorun
-rw-------  1 andrew andrew   36 Oct 17  2002 autorun.inf
drwx------  1 andrew andrew 4.0K Sep 18  2012 Laptop
drwx------  1 andrew andrew 4.0K Feb  3  2013 Server
drwx------  1 andrew andrew    0 May  5  2011 System Volume Information
drwx------  1 andrew andrew    0 Sep 19  2012 .Trash-1000
andrew@allcock-server:~$

---

### Post by Cloggsy on 2014-10-28
File system on "Elements" external drive is NTFS

---

### Post by nerdtron on 2014-10-29
```
andrew@allcock-server:~$  sudo ls -lah /media/andrew/Elements
total 17K
drwx------  1 andrew andrew 4.0K Sep 18  2012 .
drwxr-x---+ 4 root   root   4.0K Oct 28 13:47 ..

```

Permissions on the individual folders are OK. So it seems the destination is the problem.
So here we can see that the backup folder is owned by you and you can save/edit/delete files on that folder.
If the other user is logged in, example rachel, the permissions/ownership should change to rachel.
Can you test that and run the command again?

---

### Post by Cloggsy on 2014-10-29
Captain Mark
Thanks also for your advice. Fstab a foreign country to me but will look when I have a moment.

---

