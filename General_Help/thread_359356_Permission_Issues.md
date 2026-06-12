---
title: "Permission Issues"
date: 2007-02-11
forum: General Help
---

### Post by Inhumane on 2007-02-11
I'm having permission issues on my computer.
At first I couldn't mount drives, even though I had those privilages in Users and Groups
Now I can't edit menus with Alcarte, but I can if I login as root.
I fixed the mounting issue by making fstab use different permissions, but now it's just getting annoying, and who knows how many more problems I'll run into liket his.

How can I make my user have full read/write permissions and be almost, if not as powerful as root? My user is the root group, too.

---

### Post by taurus on 2007-02-11
You are not supposed to change permissions of anything outside your $HOME directory.  Doing do will only trash your machine sooner or later.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Inhumane on 2007-02-11
> **taurus said:**
> You are not supposed to change permissions of anything outside your $HOME directory.  Doing do will only trash your machine sooner or later.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

I'm more than willing to take the risk.
Edit: I don't want to flat out change permissions for everything. But I want to fix the perimssions ISSUE I'm having. I didn't have this problem on my last Ubuntu setup. I could mount and change menus around just fine as a user

---

### Post by Inhumane on 2007-02-12
Please help me fix the permission problems..

---

### Post by Topsiho on 2007-02-12
I think you should edit your /etc/fstab file.

As a working example I'll show you mine:

====
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=22fd0b6c-139e-4da5-a9fe-7b663b2a8ab6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=44D5-2489  /gedeeld        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda9
UUID=e2fad798-96fc-4342-b50f-5693f1696073 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0B23-1DEF  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=2422-1BE9  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=27966463-ff46-409d-809b-60bc19ed5237 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,sync  0       0
====

The option user in the lines for the cdroms and fd0 makes it possible for any user to mount or umount these cdroms and floppy disk.

Success

Topsiho

---

### Post by Inhumane on 2007-02-12
> **Topsiho said:**
> I think you should edit your /etc/fstab file.

As a working example I'll show you mine:

====
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda6
UUID=22fd0b6c-139e-4da5-a9fe-7b663b2a8ab6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda8
UUID=44D5-2489  /gedeeld        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda9
UUID=e2fad798-96fc-4342-b50f-5693f1696073 /home           ext3    defaults        0       2
# /dev/hda1
UUID=0B23-1DEF  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=2422-1BE9  /media/hda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=27966463-ff46-409d-809b-60bc19ed5237 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,sync  0       0
====

The option user in the lines for the cdroms and fd0 makes it possible for any user to mount or umount these cdroms and floppy disk.

Success

Topsiho

Mounting is no longer my issue, I fixed it already, but now I have a new problem, I can't change menu options using Alcarate, and I might run into other problem. So it's obvious my user is having permission issues even though I'm not sure why... which is why I'm here

---

### Post by sdide on 2007-02-12
Hey, 

Can you give us the error message you get, when you try to edit the menus?

---

### Post by Inhumane on 2007-02-12
> **sdide said:**
> Hey, 

Can you give us the error message you get, when you try to edit the menus?

There's no error, I just can't move stuff up and down, and clicking the little checkbox to hide/undehide entries doesn't do anything. But it works just fine if I login as root

---

### Post by taurus on 2007-02-12
```
ls -la ~
```

---

### Post by sdide on 2007-02-12
Hey 

Inhumane, what is your default umask set to?
```
$ umask
```

---

### Post by Inhumane on 2007-02-12
> **taurus said:**
> ```
ls -la ~
```

drwxr-xr-x 46 tylerdurden tylerdurden    4096 2007-02-12 16:22 .
drwxr-xr-x  3 root        root           4096 2007-02-08 13:44 ..
drwxr-xr-x  9 tylerdurden root           4096 2007-02-12 08:06 .azureus
-rw-------  1 tylerdurden tylerdurden   12489 2007-02-12 00:35 .bash_history
-rw-r--r--  1 tylerdurden tylerdurden     220 2007-02-08 13:44 .bash_logout
-rw-r--r--  1 tylerdurden tylerdurden     414 2007-02-08 13:44 .bash_profile
-rw-r--r--  1 tylerdurden tylerdurden    2227 2007-02-08 13:44 .bashrc
drwxr-xr-x  2 tylerdurden admin          4096 2007-02-12 16:22 .beryl
-rw-r--r--  1 tylerdurden root            185 2007-02-12 16:22 .beryl-managerrc
drwxr-xr-x  7 tylerdurden root           4096 2007-02-11 17:47 .cedega
-rw-r--r--  1 tylerdurden admin          1105 2007-02-11 17:46 .cedegarc
drwxr-xr-x  4 tylerdurden root           4096 2007-02-11 21:32 .codered
drwxr-xr-x  3 tylerdurden admin          4096 2007-02-10 18:09 computer:
drwx------  5 tylerdurden tylerdurden    4096 2007-02-09 22:34 .config
-rw-r--r--  1 tylerdurden admin          2476 2007-02-10 20:03 .conkyrc
-rw-r--r--  1 tylerdurden admin          6465 2007-02-10 19:31 .conkyrc~
-rw-r--r--  1 tylerdurden admin            58 2007-02-10 18:07 .DCOPserver_FightClub__0
lrwxrwxrwx  1 tylerdurden admin            42 2007-02-10 01:46 .DCOPserver_FightClub_:0 -> /home/tylerdurden/.DCOPserver_FightClub__0
drwxr-xr-x  3 tylerdurden tylerdurden    4096 2007-02-12 00:56 Desktop
-rw-------  1 tylerdurden tylerdurden      26 2007-02-08 13:55 .dmrc
drwxr-xr-x  4 tylerdurden admin          4096 2007-02-11 02:18 .emerald
-rw-------  1 tylerdurden tylerdurden      16 2007-02-08 13:55 .esd_auth
drwxr-xr-x  4 root        root           4096 2007-02-12 08:05 .etwolf
drwxr-xr-x  3 tylerdurden tylerdurden    4096 2007-02-09 20:29 .evolution
-rw-r--r--  1 tylerdurden root          73664 2007-02-10 21:40 .fonts.cache-1
drwx------  4 tylerdurden tylerdurden    4096 2007-02-12 16:23 .gaim
drwx------  6 tylerdurden tylerdurden    4096 2007-02-12 16:22 .gconf
drwx------  2 tylerdurden tylerdurden    4096 2007-02-12 16:23 .gconfd
drwxr-xr-x 21 tylerdurden admin          4096 2007-02-11 19:36 .gimp-2.2
-rw-r-----  1 tylerdurden tylerdurden       0 2007-02-11 21:18 .gksu.lock
drwxr-xr-x  6 tylerdurden tylerdurden    4096 2007-02-11 00:40 .gnome
drwx------ 10 tylerdurden tylerdurden    4096 2007-02-11 22:56 .gnome2
drwx------  2 tylerdurden tylerdurden    4096 2007-02-08 13:55 .gnome2_private
drwxr-xr-x  2 tylerdurden admin          4096 2007-02-10 02:34 .gstreamer-0.10
drwxr-xr-x  2 tylerdurden admin          4096 2007-02-09 21:08 .gtkpod
-rw-r--r--  1 tylerdurden tylerdurden      93 2007-02-08 13:55 .gtkrc-1.2-gnome2
-rw-------  1 tylerdurden admin           359 2007-02-10 14:15 .gtkrc-2.0
-rw-------  1 tylerdurden admin             0 2007-02-10 14:08 .gtkrc-2.0~
-rw-------  1 tylerdurden root           7322 2007-02-12 16:22 .ICEauthority
drwxr-xr-x  4 tylerdurden admin          4096 2007-02-11 18:44 .icons
drwx------  3 tylerdurden admin          4096 2007-02-10 18:07 .kde
-rw-------  1 tylerdurden admin            35 2007-02-10 02:12 .lesshst
drwx------  3 root        root           4096 2007-02-08 20:02 .local
drwx------  3 tylerdurden admin          4096 2007-02-10 01:44 .macromedia
drwxr-xr-x  3 tylerdurden admin          4096 2007-02-10 01:50 .mcop
-rw-------  1 tylerdurden admin            31 2007-02-10 01:50 .mcoprc
drwx------  3 tylerdurden tylerdurden    4096 2007-02-08 13:55 .metacity
drwx------  4 tylerdurden tylerdurden    4096 2007-02-10 01:43 .mozilla
drwxr-xr-x  2 tylerdurden admin          8192 2007-02-10 18:40 Music
drwxr-xr-x  3 tylerdurden tylerdurden    4096 2007-02-11 22:56 .nautilus
-rw-r--r--  1 tylerdurden tylerdurden    1064 2007-02-11 23:17 .nvidia-settings-rc
drwx------  3 tylerdurden root           4096 2007-02-11 23:09 .openoffice.org2
drwxr-xr-x  2 root        root           4096 2007-02-08 14:26 .qt
-rw-------  1 tylerdurden tylerdurden    3616 2007-02-11 23:09 .recently-used
-rw-r--r--  1 tylerdurden root          32969 2007-02-11 23:59 .recently-used.xbel
-rwx------  1 root        root         634912 2007-02-12 08:05 .setup23868
-rw-r--r--  1 tylerdurden tylerdurden       0 2007-02-08 13:58 .sudo_as_admin_successful
-rw-r--r--  1 tylerdurden admin       1561866 2007-02-11 02:17 Swiftfox_wallpaper.png
drwxr-xr-x  2 tylerdurden admin          4096 2007-02-11 18:44 .themes
drwx------  4 tylerdurden tylerdurden    4096 2007-02-09 19:22 .thumbnails
drwxr-xr-x  3 tylerdurden admin          4096 2007-02-09 23:33 .tomboy
drwxr-xr-x  4 tylerdurden root           4096 2007-02-12 00:22 Torrents
lrwxrwxrwx  1 tylerdurden root             51 2007-02-11 16:11 TransGaming_Drive -> /home/tylerdurden/.cedega/World of Warcraft/c_drive
drwxr-xr-x  4 tylerdurden root           4096 2007-02-10 21:12 .transgaming_global
drwx------  2 tylerdurden tylerdurden    4096 2007-02-11 01:46 .Trash
drwxr-xr-x  2 tylerdurden tylerdurden    4096 2007-02-08 15:52 .update-manager
drwx------  2 tylerdurden tylerdurden    4096 2007-02-08 13:55 .update-notifier
drwxr-xr-x  3 tylerdurden admin          4096 2007-02-10 02:28 .vlc
drwxr-xr-x  2 tylerdurden admin          4096 2007-02-09 23:33 .wapi
drwxr-xr-x  4 tylerdurden root           4096 2007-02-11 01:23 .wine
-rw-------  1 tylerdurden root            120 2007-02-12 16:22 .Xauthority
drwx------  3 tylerdurden admin          4096 2007-02-10 23:37 .xchat2
drwxr-xr-x  2 tylerdurden admin          4096 2007-02-10 01:47 .xine
drwxr-xr-x  4 tylerdurden admin          4096 2007-02-09 22:57 .xmms
-rw-r--r--  1 tylerdurden root            717 2007-02-12 16:22 .xsession-errors
>  	Hey

Inhumane, what is your default umask set to?
0022

---

### Post by sdide on 2007-02-13
Hmmm seems normal to me.
Only why is .qt and .local owned by root? and none of them with write permission to others?

I suggest (as root or with sudo) 
# chown -R tylerdurden: .qt .local

---

### Post by Inhumane on 2007-02-13
> **sdide said:**
> Hmmm seems normal to me.
Only why is .qt and .local owned by root? and none of them with write permission to others?

I suggest (as root or with sudo) 
# chown -R tylerdurden: .qt .local

That worked! Thanks :guitar:

---

