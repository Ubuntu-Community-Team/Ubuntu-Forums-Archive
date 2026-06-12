---
title: "Losing tmp file"
date: 2013-08-21
forum: General Help
---

### Post by free10 on 2013-08-21
I am running 12.04 LTS I am losing the tmp file several times, while on my computer, and then when I reboot it says errors and corrects them on the tmp file. Seems kind of funny it is just that one file. Got any suggestions as to cause, or a simple fix. Thanks

---

### Post by sudodus on 2013-08-21
The tmp files are only temporary, and are supposed to be wiped at reboot.

Or do you mean that the /tmp directory is wiped? It should stay and have the following permissions, as seen by

```
 ls -l /
```

```
 drwxrwxrwt  14 root root   4096 aug 21 08:00 tmp
```

---

### Post by free10 on 2013-08-21
> **sudodus said:**
> The tmp files are only temporary, and are supposed to be wiped at reboot.

Or do you mean that the /tmp directory is wiped? It should stay and have the following permissions, as seen by

```
 ls -l
```

```
 drwxrwxrwt  14 root root   4096 aug 21 08:00 tmp
```

When I run the command in terminal I get

```


total 1430776
-rw-rw-r--   1 dwight dwight 484200000 Mar 10 19:17 001.kinofx.dv
-rw-rw-r--   1 dwight dwight 484200000 Mar 10 19:19 002.kinofx.dv
-rw-rw-r--   1 dwight dwight 484200000 Mar 10 19:23 003.kinofx.dv
-rw-rw-rw-   1 dwight dwight  10373120 Nov 12  2006 06 - Hardin Wouldn't Run.mp3
drwxrwxr-x  51 dwight dwight      4096 Jun 26 01:14 Azureus Downloads
-rw-rw-r--   1 dwight dwight       288 Jun 26 09:16 C:\nppdf32Log\debuglog.txt
drwxr-xr-x   9 dwight dwight      4096 Aug 11 23:04 Desktop
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Documents
drwxr-xr-x 114 dwight dwight     32768 Aug 20 23:54 Downloads
-rw-rw-r--   1 dwight dwight   2007669 Dec 17  2012 DSC_1719.jpg
-rw-rw-r--   1 dwight dwight      2466 Dec 17  2012 DSC_1719.jpg.out.pp3
drwxr-xr-x   3 dwight dwight      4096 Aug 14 15:14 dwhelper
-rw-r--r--   1 dwight dwight      8445 Sep 24  2012 examples.desktop
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Music
drwxr-xr-x   3 dwight dwight      4096 Aug  7 08:31 Pictures
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Public
-rw-rw-r--   1 dwight dwight      3273 Oct 22  2012 StarMaster (1982) (Activision)_1.png
-rw-rw-r--   1 dwight dwight      3244 Oct 22  2012 StarMaster (1982) (Activision).png
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Templates
-rw-rw-r--   1 dwight dwight      7577 Dec 21  2012 testdisk.log
drwxrwxr-x   2 dwight dwight      4096 Sep 27  2012 Ubuntu One
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Videos

```

But it is losing one of the two it seems, while running, and then Unbuntu has to correct errors to get it back on reboot. When running it will start not saving drafts in Thunderbird for example, or a torrent can't be started in transmission saying file is read only.

---

### Post by sudodus on 2013-08-21
Sorry, I forgot to mention that you need to change directory to root '/' and run ***ls*** there, or run

```
ls -l /
``` to see /tmp

But if you have problems with not saving drafts in Thunderbird for example, or a torrent can't be started in transmission saying file is read only, I think there are problems with the hidden directories in your home directory.

You can see those hidden directories like this

```
cd  # to change directory to your home directory
ls -la  # to list also the hidden files and directories, with names starting with **.** (dot).
```

---

### Post by free10 on 2013-08-21
> **sudodus said:**
> Sorry, I forgot to mention that you need to change directory to root '/' and run ***ls*** there, or run

```
ls -l /
``` to see /tmp

But if you have problems with not saving drafts in Thunderbird for example, or a torrent can't be started in transmission saying file is read only, I think there are problems with the hidden directories in your home directory.

You can see those hidden directories like this

```
cd  # to change directory to your home directory
ls -la  # to list also the hidden files and directories, with names starting with **.** (dot).
```

Well the list for root shows

```
total 88
drwxr-xr-x   2 root root  4096 Jun 13 21:59 bin
drwxr-xr-x   3 root root  4096 Aug 11 22:50 boot
drwxr-xr-x   2 root root  4096 Sep 24  2012 cdrom
drwxr-xr-x  16 root root  4520 Aug 20 22:21 dev
drwxr-xr-x 146 root root 12288 Aug 20 22:21 etc
drwxr-xr-x   3 root root  4096 Sep 24  2012 home
lrwxrwxrwx   1 root root    37 Aug 11 22:49 initrd.img -> /boot/initrd.img-3.2.0-51-generic-pae
lrwxrwxrwx   1 root root    37 Jun 13 22:00 initrd.img.old -> /boot/initrd.img-3.2.0-48-generic-pae
drwxr-xr-x  22 root root  4096 May 30 10:35 lib
drwx------   2 root root 16384 Sep 24  2012 lost+found
drwxr-xr-x   2 root root  4096 Aug 15 08:11 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   3 root root  4096 May 21 10:43 opt
dr-xr-xr-x 179 root root     0 Aug 20 22:21 proc
drwx------  11 root root  4096 May 18 13:15 root
drwxr-xr-x  20 root root   740 Aug 20 23:28 run
drwxr-xr-x   2 root root  4096 Aug  2 07:56 sbin
drwxr-xr-x   2 root root  4096 Mar  5  2012 selinux
drwxr-xr-x   2 root root  4096 Aug 17  2012 srv
drwxr-xr-x  13 root root     0 Aug 20 22:21 sys
drwxrwxrwt  11 root root  4096 Aug 21 06:17 tmp
drwxr-xr-x  11 root root  4096 Sep 24  2012 usr
drwxr-xr-x  13 root root  4096 Aug 15 08:10 var
lrwxrwxrwx   1 root root    33 Aug 11 22:49 vmlinuz -> boot/vmlinuz-3.2.0-51-generic-pae
lrwxrwxrwx   1 root root    33 Jun 13 22:00 vmlinuz.old -> boot/vmlinuz-3.2.0-48-generic-pae
```


And running the CD and then list on hidden files list this

```
total 1431528
drwxr-xr-x  46 dwight dwight      4096 Aug 20 22:21 .
drwxr-xr-x   3 root   root        4096 Sep 24  2012 ..
-rw-rw-r--   1 dwight dwight 484200000 Mar 10 19:17 001.kinofx.dv
-rw-rw-r--   1 dwight dwight 484200000 Mar 10 19:19 002.kinofx.dv
-rw-rw-r--   1 dwight dwight 484200000 Mar 10 19:23 003.kinofx.dv
-rw-rw-rw-   1 dwight dwight  10373120 Nov 12  2006 06 - Hardin Wouldn't Run.mp3
drwx------   4 dwight dwight      4096 Jun 13 13:43 .adobe
drwxrwxr-x  12 dwight dwight      4096 Jun 26 21:19 .azureus
drwxrwxr-x  51 dwight dwight      4096 Jun 26 01:14 Azureus Downloads
-rw-------   1 dwight dwight       359 Aug 21 00:35 .bash_history
-rw-r--r--   1 dwight dwight       220 Sep 24  2012 .bash_logout
-rw-r--r--   1 dwight dwight      3486 Sep 24  2012 .bashrc
-rw-rw-r--   1 dwight dwight        83 Apr  4 00:06 .BillardGL.conf.v7
drwx------  27 dwight dwight      4096 Aug 15 08:24 .cache
-rw-rw-r--   1 dwight dwight       288 Jun 26 09:16 C:\nppdf32Log\debuglog.txt
drwxrwxr-x   3 dwight dwight      4096 Sep 24  2012 .compiz-1
drwx------  26 dwight dwight      4096 Feb 21 00:08 .config
drwx------   3 dwight dwight      4096 Sep 24  2012 .dbus
drwxr-xr-x   9 dwight dwight      4096 Aug 11 23:04 Desktop
-rw-r--r--   1 dwight dwight        26 Aug 20 22:21 .dmrc
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Documents
drwxr-xr-x 114 dwight dwight     32768 Aug 20 23:54 Downloads
-rw-rw-r--   1 dwight dwight   2007669 Dec 17  2012 DSC_1719.jpg
-rw-rw-r--   1 dwight dwight      2466 Dec 17  2012 DSC_1719.jpg.out.pp3
drwxr-xr-x   3 dwight dwight      4096 Aug 14 15:14 dwhelper
-rw-r--r--   1 dwight dwight      8445 Sep 24  2012 examples.desktop
drwxr-xr-x   2 dwight dwight      4096 Apr 10 10:37 .fontconfig
drwx------   5 dwight dwight      4096 Aug 20 22:21 .gconf
drwx------   4 dwight dwight      4096 Sep 27  2012 .gegl-0.0
drwxr-xr-x  22 dwight dwight      4096 Aug  1 00:46 .gimp-2.6
-rw-r-----   1 dwight dwight         0 Feb 25 23:50 .gksu.lock
drwx------   5 dwight dwight      4096 Aug 15 08:10 .gnome2
drwx------   2 dwight dwight      4096 Sep 25  2012 .gnome2_private
-rw-------   1 dwight dwight         0 Oct  2  2012 .goutputstream-4D5ILW
-rw-------   1 dwight dwight         0 Sep 27  2012 .goutputstream-8LSHLW
-rw-------   1 dwight dwight         0 Sep 24  2012 .goutputstream-DU5DLW
-rw-------   1 dwight dwight         0 Apr  1 00:12 .goutputstream-FFYRUW
-rw-------   1 dwight dwight         0 Dec  2  2012 .goutputstream-JBWQOW
-rw-------   1 dwight dwight         0 Oct  3  2012 .goutputstream-O52LLW
-rw-------   1 dwight dwight         0 Dec 31  2007 .goutputstream-QZ8G4T
-rw-------   1 dwight dwight         0 Oct 18  2012 .goutputstream-V4GPMW
-rw-------   1 dwight dwight         0 Jan 16  2013 .goutputstream-V5M2QW
-rw-------   1 dwight dwight         0 Dec  7  2012 .goutputstream-VQ5XOW
-rw-------   1 dwight dwight         0 Oct  4  2012 .goutputstream-WCIDLW
drwx------   2 dwight dwight      4096 Oct 18  2012 .gphoto
drwxrwxr-x   3 dwight dwight      4096 Aug 19 21:18 .gstreamer-0.10
-rw-rw-r--   1 dwight dwight       142 Aug 20 22:21 .gtk-bookmarks
dr-x------   2 dwight dwight         0 Aug 20 22:21 .gvfs
-rw-------   1 dwight dwight     20650 Aug 20 22:21 .ICEauthority
drwx------   3 dwight dwight      4096 Oct 22  2012 .kde
drwx------   2 dwight dwight      4096 Mar 11 11:30 .kino-history
-rw-rw-r--   1 dwight dwight      2973 Mar 11 11:30 .kinorc
drwx------   3 dwight dwight      4096 Nov 14  2012 .launchpadlib
drwxr-xr-x   3 dwight dwight      4096 Sep 24  2012 .local
drwx------   3 dwight dwight      4096 Sep 24  2012 .macromedia
drwx------   3 dwight dwight      4096 Sep 24  2012 .mission-control
drwx------   4 dwight dwight      4096 Sep 24  2012 .mozilla
drwxrwxr-x   2 dwight dwight      4096 Nov 28  2012 .mp3splt-gtk
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Music
-rw-rw-r--   1 dwight dwight      1116 Apr  4 17:32 .nvidia-settings-rc
drwxr-xr-x   3 dwight dwight      4096 Aug  7 08:31 Pictures
drwx------   3 dwight dwight      4096 Sep 29  2012 .pki
-rw-r--r--   1 dwight dwight       675 Sep 24  2012 .profile
drwxrwxr-x   2 dwight dwight      4096 May 18 19:47 .psensor
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Public
drwx------   2 dwight dwight      4096 Aug 20 22:21 .pulse
-rw-------   1 dwight dwight       256 Sep 24  2012 .pulse-cookie
drwx------   6 dwight dwight      4096 Aug 21 06:18 .purple
drwxrwxr-x   4 dwight dwight      4096 Dec 17  2012 .shotwell
-rw-rw-r--   1 dwight dwight      3273 Oct 22  2012 StarMaster (1982) (Activision)_1.png
-rw-rw-r--   1 dwight dwight      3244 Oct 22  2012 StarMaster (1982) (Activision).png
drwxrwxr-x   4 dwight dwight      4096 Oct 22  2012 .stella
drwxrwxr-x   3 dwight dwight      4096 Sep 24  2012 .swt
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Templates
-rw-rw-r--   1 dwight dwight      7577 Dec 21  2012 testdisk.log
drwx------   5 dwight dwight      4096 Jan 24  2013 .thumbnails
drwx------   4 dwight dwight      4096 Sep 24  2012 .thunderbird
drwxrwxr-x   2 dwight dwight      4096 Sep 27  2012 Ubuntu One
-rw-rw-r--   1 dwight dwight       622 Oct 20  2012 .ufrawrc
drwxrwxr-x   2 dwight dwight      4096 May 16 07:29 .vidalia
drwxr-xr-x   2 dwight dwight      4096 Sep 24  2012 Videos
-rw-------   1 dwight dwight        59 Aug 20 22:21 .Xauthority
-rw-------   1 dwight dwight     43832 Aug 21 06:19 .xsession-errors
```

Sorry for the slow reponse needed sleep.

---

### Post by sudodus on 2013-08-21
Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

Your /tmp directory has the same permissions as mine

```
drwxrwxrwt  11 root root  4096 Aug 21 06:17 tmp
```

but your .thunderbird directory has

```
drwx------   4 dwight dwight      4096 Sep 24  2012 .thunderbird
```

while mine has
```
drwxrwx---   4 sudodus sudodus 4096 apr 25  2012 .thunderbird
```

I'm not sure if that makes a difference. You can also check the files and directories inside it.

---

### Post by free10 on 2013-08-21
> **sudodus said:**
> Please post the output between code tags like this
 
[noparse]```
output
```[/noparse]
 
to get output like this
 
```
output
```

Your /tmp directory has the same permissions as mine

```
drwxrwxrwt  11 root root  4096 Aug 21 06:17 tmp
```

but your .thunderbird directory has

```
drwx------   4 dwight dwight      4096 Sep 24  2012 .thunderbird
```

while mine has
```
drwxrwx---   4 sudodus sudodus 4096 apr 25  2012 .thunderbird
```

I'm not sure if that makes a difference. You can also check the files and directories inside it.

Well when I tried output terminal said

The program 'output' is currently not installed.  You can install it by typing:
sudo apt-get install yagiuda


Should I install that?? yagiuda

---

### Post by sudodus on 2013-08-21
No, that was just a way to show how to put your own commands and output from commands between code tags. Sorry, I did not mean to make you confused.

---

### Post by free10 on 2013-08-21
> **sudodus said:**
> No, that was just a way to show how to put your own commands and output from commands between code tags. Sorry, I did not mean to make you confused.

Its OK. I am use to confusion as I work through something new and it doesn't bother me a bit. Still can't figure out why the coding in the temp directory evidently is fouling up and causing it to fail after days of uptime, and then needs being correct before reboot is possible. If it was hitting different places I would suspect hardware problems, but both times now it was just in tmp.

---

### Post by sudodus on 2013-08-21
Try to change the permissions of the .thunderbird directory (and also of its subdirectories and files inside) to be

```
 drwxrwx---   4 dwight dwight 4096 apr 25  2012 .thunderbird
```

with the following command

```
chmod -R ug+rwx ~/.thunderbird
```

Does it help? If not, maybe you should reinstall ***thunderbird***.

---

### Post by free10 on 2013-08-21
Well tried to reset thunderbird permissions manually and didn't work and the trashed it, and reinstalled and it has the same permissions as before. Remember too, that transmission and other apps are effected when the tmp disappears suddenly.

---

### Post by Bashing-om on 2013-08-21
I have to wonder how /tmp is mounted ...to see; Terminal code:
```

cat /etc/fstab

```

[INDENT][INDENT]just a thought
[/INDENT][/INDENT]

---

### Post by free10 on 2013-08-21
This came back

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=682931a0-b9fd-4382-abb0-3af17cfac385 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=49e2de60-fa88-4862-b53b-e696a9bce461 none            swap    sw              0       0

---

### Post by Bashing-om on 2013-08-21
free10; Well ..

No /tmp to be mounted ???.. I will have to boot into a standard install and check what that fstab shows ...in the meantime .. lets see what is mounted on your system.
```

mount

```
[INDENT]maybe yes ??
[/INDENT]

---

### Post by free10 on 2013-08-21
Got this back

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dwight/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dwight)

---

### Post by Bashing-om on 2013-08-21
free10; Hi !

That "mount" output looks good to me ..let me at this time reboot into a standard install and compare what is to what I think ..back in a bit.

[INDENT][INDENT]soonest
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-08-21
free10; 

Nope .. your "fstab" is valid .. looks same as from my standard install.
Your mount is also valid.
Sorry to say but I do not have the knowledge to advise further ...

[INDENT][INDENT]it was but a thought
[/INDENT][/INDENT]

---

### Post by VMC on 2013-08-21
If you list tmp now ( ls /tmp ), what files are there inside that directory that gets deleted?

---

### Post by free10 on 2013-08-21
> **Bashing-om said:**
> free10; 

Nope .. your "fstab" is valid .. looks same as from my standard install.
Your mount is also valid.
Sorry to say but I do not have the knowledge to advise further ...

[INDENT][INDENT]it was but a thought
[/INDENT][/INDENT]

Well thanks for the help. I thought this action was pretty strange and that I had better ask, so we will carry the candle forward to see what we can see. Ok who has any ideas--Dwight

---

### Post by free10 on 2013-08-21
> **VMC said:**
> If you list tmp now ( ls /tmp ), what files are there inside that directory that gets deleted?

This what I get with ls/tmp

CRX_75DAF8CB7768  pulse-B9MQNRFLZ6Vz      tmpD_sHZ7
keyring-OzoZQQ    pulse-PKdhtXMmr18n      unity_support_test.0
orbit-dwight      sni-qt_vlc_2925-Bv2E3g  xdg-screensaver-dwight--0.0
plugtmp           ssh-DnQtUSUh1351        xdg-screensaver-dwight--0.0.dpms

---

### Post by VMC on 2013-08-21
What tmp files do you think your losing?

---

### Post by free10 on 2013-08-21
> **VMC said:**
> What tmp files do you think your losing?

The whole file or directory, for all practability,  since it affects apps while running and on reboot Ubuntu says its detected bad or corrupted code in tmp, that it can try and correct, before it can reboot. Twice now it fix it before booting, in the last week with the last time yesterday.

---

### Post by VMC on 2013-08-21
Can you try and remove all directories and files in "/tmp" then reboot and see if the errors come up again. You will need to use *sudo* for that

edit: I would look at some log files for any errors. "/var/log/syslog and kern.log".

---

### Post by free10 on 2013-08-21
Do you mean the tmp directory?? Maybe instead of sudo gksudo nautilus might work, and that an interesting idea if that works because I could just zip it up leaving it there as a zip, and then I should see the Firefox and other apps start acting up without rebooting, but not sure that would tell me what is causing it to happen without my commands.

---

### Post by VMC on 2013-08-21
also what's the output of this ```
df -h /tmp
```I want to make sure tmp is on the same partition as root.

---

### Post by free10 on 2013-08-21
> **VMC said:**
> also what's the output of this ```
df -h /tmp
```I want to make sure tmp is on the same partition as root.


That brought back

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       913G  227G  641G  27% /

---

### Post by sudodus on 2013-08-22
> **free10 said:**
> This what I get with ```
ls/tmp
```

```
CRX_75DAF8CB7768  pulse-B9MQNRFLZ6Vz      tmpD_sHZ7
keyring-OzoZQQ    pulse-PKdhtXMmr18n      unity_support_test.0
orbit-dwight      sni-qt_vlc_2925-Bv2E3g  xdg-screensaver-dwight--0.0
plugtmp           ssh-DnQtUSUh1351        xdg-screensaver-dwight--0.0.dpms
```

Please use code tags! It makes it easier to read commands and output of commands :-)

Now I suggest that you make a long listing of /tmp (showing the permissions and ownership too) and post the result

```
sudo ls -l /tmp/*
```

---

### Post by free10 on 2013-08-23
Sorry about my less than speedy reply!

```


dwight@dwight-desktop:~$ sudo ls -l /tmp/*
[sudo] password for dwight: 
-rw------- 1 dwight dwight 20480 Aug 21 18:48 /tmp/_EOC+NMQ.doc.part
-rw------- 1 dwight dwight 59114 Aug 22 14:30 /tmp/_ERCSW5B.bin.part
-rw------- 1 dwight dwight 59114 Aug 22 14:31 /tmp/i+nqPRav.bin.part
-rw------- 1 dwight dwight 59114 Aug 22 14:30 /tmp/IT6noyZe.bin.part
-rw------- 1 dwight dwight     0 Aug 20 22:21 /tmp/tmpD_sHZ7
-rw-rw-r-- 1 dwight dwight     0 Aug 20 22:21 /tmp/unity_support_test.0
-rw------- 1 dwight dwight 59114 Aug 22 14:32 /tmp/XMKZnHV9.bin.part

/tmp/CRX_75DAF8CB7768:
total 8
-rw------- 1 dwight dwight 963 Aug 23 06:43 crl-set
-rw------- 1 dwight dwight  34 Aug 23 06:43 manifest.json

/tmp/keyring-OzoZQQ:
total 0
srwxrwxr-x 1 dwight dwight 0 Aug 20 22:21 control
srwxrwxr-x 1 dwight dwight 0 Aug 20 22:21 gpg
srwxrwxr-x 1 dwight dwight 0 Aug 20 22:21 pkcs11
srwxrwxr-x 1 dwight dwight 0 Aug 20 22:21 ssh

/tmp/orbit-dwight:
total 0

/tmp/plugtmp:
total 0

/tmp/pulse-B9MQNRFLZ6Vz:
total 4
srwxrwxrwx 1 dwight dwight 0 Aug 20 22:21 native
-rw------- 1 dwight dwight 5 Aug 20 22:21 pid

/tmp/pulse-PKdhtXMmr18n:
total 0

/tmp/ssh-DnQtUSUh1351:
total 0
srw------- 1 dwight dwight 0 Aug 20 22:21 agent.1351

```

---

### Post by sudodus on 2013-08-23
I compared your list with mine, and I don't see anything bad. Maybe someone else ...

I suggest that you do something similar with the hidden directories at your home, for example ***.thunderbird***

You can list the subdirectories and files like this (also for /tmp you might find some hidden files which I forgot about in the last tip).

```
sudo find /tmp -ls
```
```
sudo find ~/.thunderbird -ls
```

---

### Post by free10 on 2013-08-23
Will do. I just recently had a thought, and that is if it hapens again maybe using terminal to do a list and then save the terminal response in a gmail email before rebooting.

---

### Post by free10 on 2013-08-23
```

dwight@dwight-desktop:~$ sudo find /tmp -ls
[sudo] password for dwight: 
51642369    4 drwxrwxrwt  12 root     root         4096 Aug 23 09:15 /tmp
51646045   60 -rw-------   1 dwight   dwight      59114 Aug 22 14:30 /tmp/IT6noyZe.bin.part
51642376    0 -rw-rw-r--   1 dwight   dwight          0 Aug 20 22:21 /tmp/unity_support_test.0
51642370    4 drwxrwxrwt   2 root     root         4096 Aug 20 22:21 /tmp/.X11-unix
51642375    0 srwxrwxrwx   1 root     root            0 Aug 20 22:21 /tmp/.X11-unix/X0
51642380    4 drwx------   2 dwight   dwight       4096 Aug 20 22:21 /tmp/keyring-OzoZQQ
51642384    0 srwxrwxr-x   1 dwight   dwight          0 Aug 20 22:21 /tmp/keyring-OzoZQQ/ssh
51642383    0 srwxrwxr-x   1 dwight   dwight          0 Aug 20 22:21 /tmp/keyring-OzoZQQ/gpg
51642382    0 srwxrwxr-x   1 dwight   dwight          0 Aug 20 22:21 /tmp/keyring-OzoZQQ/pkcs11
51642381    0 srwxrwxr-x   1 dwight   dwight          0 Aug 20 22:21 /tmp/keyring-OzoZQQ/control
51646032    4 drwx------   2 dwight   dwight       4096 Aug 23 08:58 /tmp/plugtmp
51642373    4 drwx------   2 root     root         4096 Aug 20 22:21 /tmp/pulse-PKdhtXMmr18n
51642385    4 drwx------   2 dwight   dwight       4096 Aug 20 22:21 /tmp/pulse-B9MQNRFLZ6Vz
51642387    4 -rw-------   1 dwight   dwight          5 Aug 20 22:21 /tmp/pulse-B9MQNRFLZ6Vz/pid
51642388    0 srwxrwxrwx   1 dwight   dwight          0 Aug 20 22:21 /tmp/pulse-B9MQNRFLZ6Vz/native
51646048   60 -rw-------   1 dwight   dwight      59114 Aug 22 14:32 /tmp/XMKZnHV9.bin.part
51642372    4 drwxrwxrwt   2 root     root         4096 Aug 20 22:21 /tmp/.ICE-unix
51642379    0 srwxrwxrwx   1 dwight   dwight          0 Aug 20 22:21 /tmp/.ICE-unix/1351
51646026    4 drwx------   2 dwight   dwight       4096 Aug 23 06:43 /tmp/CRX_75DAF8CB7768
51646027    4 -rw-------   1 dwight   dwight         34 Aug 23 06:43 /tmp/CRX_75DAF8CB7768/manifest.json
51646028    4 -rw-------   1 dwight   dwight        963 Aug 23 06:43 /tmp/CRX_75DAF8CB7768/crl-set
51642386    0 -rw-------   1 dwight   dwight          0 Aug 20 22:21 /tmp/tmpD_sHZ7
51646043   60 -rw-------   1 dwight   dwight      59114 Aug 22 14:30 /tmp/_ERCSW5B.bin.part
51642374    4 -r--r--r--   1 root     root           11 Aug 20 22:21 /tmp/.X0-lock
51646047   60 -rw-------   1 dwight   dwight      59114 Aug 22 14:31 /tmp/i+nqPRav.bin.part
51646037    4 drwx------   2 dwight   dwight       4096 Aug 21 06:36 /tmp/.org.chromium.Chromium.JvVACT
51646038    0 lrwxrwxrwx   1 dwight   dwight         20 Aug 21 06:36 /tmp/.org.chromium.Chromium.JvVACT/SingletonCookie -> 12639561780858012035
51646039    0 srwxrwxr-x   1 dwight   dwight          0 Aug 21 06:36 /tmp/.org.chromium.Chromium.JvVACT/SingletonSocket
51642377    4 drwx------   2 dwight   dwight       4096 Aug 20 22:21 /tmp/ssh-DnQtUSUh1351
51642378    0 srw-------   1 dwight   dwight          0 Aug 20 22:21 /tmp/ssh-DnQtUSUh1351/agent.1351
51646040   20 -rw-------   1 dwight   dwight      20480 Aug 21 18:48 /tmp/_EOC+NMQ.doc.part
51642389    4 drwx------   2 dwight   dwight       4096 Dec 31  1969 /tmp/orbit-dwight


```

```

dwight@dwight-desktop:~$ sudo find ~/.thunderbird -ls
30670942    4 drwxrwx---   4 dwight   dwight       4096 Sep 24  2012 /home/dwight/.thunderbird
30670943    4 drwxrwx---   4 dwight   dwight       4096 Aug  9 05:54 /home/dwight/.thunderbird/Crash\ Reports
30670993    4 -rwxrwx---   1 dwight   dwight         10 Jul  8 00:59 /home/dwight/.thunderbird/Crash\ Reports/LastCrash
30670974    4 -rwxrwxr--   1 dwight   dwight         42 Jul  8 01:00 /home/dwight/.thunderbird/Crash\ Reports/crashreporter.ini
30670975    4 drwxrwx---   2 dwight   dwight       4096 Nov  2  2012 /home/dwight/.thunderbird/Crash\ Reports/submitted
30670976    4 -rwxrwxr--   1 dwight   dwight         50 Nov  2  2012 /home/dwight/.thunderbird/Crash\ Reports/submitted/bp-47b589d0-f043-4dac-b93f-d83ed2121103.txt
30670944    4 -rwxrwx---   1 dwight   dwight         10 Sep 24  2012 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20120827103323
30675401    4 -rwxrwxr--   1 dwight   dwight         70 Nov  2  2012 /home/dwight/.thunderbird/Crash\ Reports/submit.log
30670911    4 -rwxrwx---   1 dwight   dwight         10 Sep 28  2012 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20120912042340
30670928    4 -rwxrwx---   1 dwight   dwight         10 Apr  8 08:03 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130329232318
30671083    4 -rwxrwx---   1 dwight   dwight         10 May 14 16:36 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130510125916
30675391    4 -rwxrwx---   1 dwight   dwight         10 Nov  1  2012 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20121028144814
30671053    4 -rwxrwx---   1 dwight   dwight         10 Jan 10  2013 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130106012405
30670937    4 -rwxrwx---   1 dwight   dwight         10 Jun 28 01:23 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130623215201
30670901    4 -rwxrwx---   1 dwight   dwight         10 Mar 13 07:39 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130308132830
30671323    4 -rwxrwx---   1 dwight   dwight         10 Feb 26 14:02 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130221102350
30670984    4 -rwxrwx---   1 dwight   dwight         10 Nov 21  2012 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20121118023742
30671753    4 -rwxrwx---   1 dwight   dwight         10 Aug  9 05:54 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20130803220105
30675402    4 drwxrwx---   2 dwight   dwight       4096 Jul  8 00:59 /home/dwight/.thunderbird/Crash\ Reports/pending
30670948  676 -rwxrwx---   1 dwight   dwight     688984 Jul  8 00:59 /home/dwight/.thunderbird/Crash\ Reports/pending/54eb8162-7a3e-c5ad-7d1043e4-4a011ee0.dmp
30671921    4 -rwxrwxr--   1 dwight   dwight        718 Jul  8 00:59 /home/dwight/.thunderbird/Crash\ Reports/pending/54eb8162-7a3e-c5ad-7d1043e4-4a011ee0.extra
30670849    4 -rwxrwx---   1 dwight   dwight         10 Oct 18  2012 /home/dwight/.thunderbird/Crash\ Reports/InstallTime20121011010828
30670945    4 drwxrwx---   6 dwight   dwight       4096 Aug 23 09:17 /home/dwight/.thunderbird/34vt6ic0.default
30670961 44260 -rwxrwxr--   1 dwight   dwight   45318144 Aug 23 09:17 /home/dwight/.thunderbird/34vt6ic0.default/global-messages-db.sqlite
30670965  512 -rwxrwxr--   1 dwight   dwight     524288 Sep 24  2012 /home/dwight/.thunderbird/34vt6ic0.default/blist.sqlite
30671879   20 -rwxrwxr--   1 dwight   dwight      17355 Aug 23 09:16 /home/dwight/.thunderbird/34vt6ic0.default/localstore.rdf
30675305  320 -rwxrwxr--   1 dwight   dwight     327680 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/signons.sqlite
30670992   96 -rwxrwxr--   1 dwight   dwight      98304 Sep 24  2012 /home/dwight/.thunderbird/34vt6ic0.default/chromeappsstore.sqlite
30675336  224 -rwxrwxr--   1 dwight   dwight     229376 Apr 10 14:13 /home/dwight/.thunderbird/34vt6ic0.default/content-prefs.sqlite
30670978    4 -rwxrwxr--   1 dwight   dwight        479 Aug 23 09:07 /home/dwight/.thunderbird/34vt6ic0.default/session.json
30675295    4 drwxrwx---   4 dwight   dwight       4096 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/Mail
30675315    4 drwxrwxr-x   2 dwight   dwight       4096 Jun 25 11:34 /home/dwight/.thunderbird/34vt6ic0.default/Mail/Local\ Folders
30675316    0 -rwxrwx---   1 dwight   dwight          0 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/Mail/Local\ Folders/Trash
30675321    4 -rwxrwxr--   1 dwight   dwight       2654 Aug 20 11:09 /home/dwight/.thunderbird/34vt6ic0.default/Mail/Local\ Folders/Unsent\ Messages.msf
30675318    4 -rwxrwxr--   1 dwight   dwight       1962 Aug 20 11:09 /home/dwight/.thunderbird/34vt6ic0.default/Mail/Local\ Folders/Trash.msf
30675320    0 -rwxrwx---   1 dwight   dwight          0 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/Mail/Local\ Folders/Unsent\ Messages
30675309    4 drwxrwxr-x   2 dwight   dwight       4096 Jul 31 23:20 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com
30671792   28 -rwxrwxr--   1 dwight   dwight      26465 Aug 23 08:46 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Drafts.msf
30671754 42672 -rwxrwx---   1 dwight   dwight   43689291 Aug 23 09:15 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Inbox
30671801 13796 -rwxrwx---   1 dwight   dwight   14121014 Aug 23 09:15 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Trash
30671003    4 -rwxrwxr--   1 dwight   dwight         25 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/msgFilterRules.dat
30671791 16872 -rwxrwx---   1 dwight   dwight   17264034 Aug 23 08:40 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Drafts
30671794 8312 -rwxrwxr--   1 dwight   dwight    8506199 Aug 23 09:17 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Sent.msf
30671825 2008 -rwxrwxr--   1 dwight   dwight    2056061 Aug 23 09:17 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Inbox.msf
30671115    8 -rwxrwx---   1 dwight   dwight       4317 Aug 23 09:18 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/popstate.dat
30671804 2276 -rwxrwxr--   1 dwight   dwight    2328686 Aug 23 09:15 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Trash.msf
30671793 66404 -rwxrwx---   1 dwight   dwight   67980791 Aug 23 09:15 /home/dwight/.thunderbird/34vt6ic0.default/Mail/pop3.valornet.com/Sent
30671015    4 -rwxrwx---   1 dwight   dwight          1 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/_CACHE_CLEAN_
30670957   96 -rwxrwx---   1 dwight   dwight     114688 Aug 20 14:03 /home/dwight/.thunderbird/34vt6ic0.default/cert8.db
30671236    4 -rwxrwxr--   1 dwight   dwight        969 Aug 19 09:45 /home/dwight/.thunderbird/34vt6ic0.default/persdict.dat
30675337    4 -rwxrwxr--   1 dwight   dwight         24 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/urlclassifier.pset
30670953   64 -rwxrwxr--   1 dwight   dwight      65536 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/permissions.sqlite
30675330   12 -rwxrwxr--   1 dwight   dwight      11444 Aug 23 09:15 /home/dwight/.thunderbird/34vt6ic0.default/history.mab
30671871    4 -rwxrwxr--   1 dwight   dwight        417 Aug  9 05:54 /home/dwight/.thunderbird/34vt6ic0.default/extensions.ini
30670972   72 -rwxrwxr--   1 dwight   dwight      72412 Jul 10 07:02 /home/dwight/.thunderbird/34vt6ic0.default/training.dat
30671915    4 -rwxrwx---   1 dwight   dwight       3729 Jul 17 01:02 /home/dwight/.thunderbird/34vt6ic0.default/pluginreg.dat
30675307  180 -rwxrwxr--   1 dwight   dwight     178263 Aug 23 09:17 /home/dwight/.thunderbird/34vt6ic0.default/panacea.dat
30671508    4 -rwxrwxr--   1 dwight   dwight       1060 Mar 10 19:03 /home/dwight/.thunderbird/34vt6ic0.default/mimeTypes.rdf
30671073   16 -rwxrwx---   1 dwight   dwight      15070 Aug 15 08:10 /home/dwight/.thunderbird/34vt6ic0.default/prefs-1.js
30671785    4 -rwxrwxr--   1 dwight   dwight      32768 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/places.sqlite-shm
30671111    4 -rwxrwxr--   1 dwight   dwight          8 Jul 10 07:02 /home/dwight/.thunderbird/34vt6ic0.default/traits.dat
30670970    0 lrwxrwxrwx   1 dwight   dwight         15 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/lock -> 127.0.1.1:+2880
30671759   32 -rwxrwxr--   1 dwight   dwight      32768 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/cookies.sqlite-shm
30670947    0 -rwxrwxr--   1 dwight   dwight          0 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/.parentlock
30670958   16 -rwxrwx---   1 dwight   dwight      16384 Aug 20 14:03 /home/dwight/.thunderbird/34vt6ic0.default/key3.db
30671787   16 -rwxrwx---   1 dwight   dwight      15117 Aug 23 01:49 /home/dwight/.thunderbird/34vt6ic0.default/prefs.js
30670991   96 -rwxrwxr--   1 dwight   dwight      98304 Oct  4  2012 /home/dwight/.thunderbird/34vt6ic0.default/webappsstore.sqlite
30671163  512 -rwxrwxr--   1 dwight   dwight     524288 Nov 23  2012 /home/dwight/.thunderbird/34vt6ic0.default/addons.sqlite
30670969  512 -rwxrwxr--   1 dwight   dwight     524288 Aug 20 14:03 /home/dwight/.thunderbird/34vt6ic0.default/cookies.sqlite
30670950    4 -rwxrwx---   1 dwight   dwight        159 Aug 10 12:26 /home/dwight/.thunderbird/34vt6ic0.default/compatibility.ini
30675322    4 -rwxrwxr--   1 dwight   dwight       2620 Jul 15 02:12 /home/dwight/.thunderbird/34vt6ic0.default/abook.mab
30670966 10240 -rwxrwxr--   1 dwight   dwight   10485760 Aug 17 03:30 /home/dwight/.thunderbird/34vt6ic0.default/places.sqlite
33165952    4 drwxrwxr-x   2 dwight   dwight       4096 Aug 10 12:27 /home/dwight/.thunderbird/34vt6ic0.default/startupCache
33165953 1760 -rwxrwxr--   1 dwight   dwight    1802153 Aug 12 08:01 /home/dwight/.thunderbird/34vt6ic0.default/startupCache/startupCache.4.little
32514028    4 drwxrwxr-x  18 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache
35522924    4 drwxrwx---   3 dwight   dwight       4096 Aug 22 14:32 /home/dwight/.thunderbird/34vt6ic0.default/Cache/C
35522930    4 drwx------   2 dwight   dwight       4096 Aug 22 14:34 /home/dwight/.thunderbird/34vt6ic0.default/Cache/C/6C
35522925    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/D
35261941    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/3
35261939    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/1
35522926    4 drwxrwx---   3 dwight   dwight       4096 Aug 22 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/E
35522928    4 drwx------   2 dwight   dwight       4096 Aug 22 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/E/6A
35522929   44 -rw-------   1 dwight   dwight      44511 Aug 22 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/E/6A/E974Dd01
35392769    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/7
35261938    4 drwxrwx---   3 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/0
35654941    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/0/3A
35654942   52 -rwxrwx---   1 dwight   dwight      50877 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/0/3A/ED61Ed01
32514032  104 -rwxrwx---   1 dwight   dwight     105388 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/_CACHE_003_
35392768    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/6
35261940    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/2
35392772    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/A
35392771    4 drwxrwx---   3 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/9
35654943    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/9/C0
35654944   32 -rwxrwx---   1 dwight   dwight      29671 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/9/C0/EFAF1d01
35522923    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/B
35261942    4 drwxrwx---   4 dwight   dwight       4096 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/4
35918986    4 drwxrwx---   2 dwight   dwight       4096 Aug 21 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/4/8E
35918987   44 -rwxrwx---   1 dwight   dwight      44511 Aug 21 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/4/8E/CF8F0d01
35261944    4 drwx------   2 dwight   dwight       4096 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/4/1E
35261945   44 -rw-------   1 dwight   dwight      44511 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/4/1E/6854Dd01
32514031   16 -rwxrwx---   1 dwight   dwight      16192 Aug 23 08:14 /home/dwight/.thunderbird/34vt6ic0.default/Cache/_CACHE_002_
32514029    4 -rwxrwx---   1 dwight   dwight        276 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/_CACHE_MAP_
32514030   28 -rwxrwx---   1 dwight   dwight      28081 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/Cache/_CACHE_001_
35261943    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/5
35522927    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/F
35392770    4 drwxrwx---   2 dwight   dwight       4096 Aug 20 23:57 /home/dwight/.thunderbird/34vt6ic0.default/Cache/8
30671501  228 -rwxrwxr--   1 dwight   dwight     229576 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/cookies.sqlite-wal
30671161   12 -rwxrwxr--   1 dwight   dwight      10489 Aug 12 01:08 /home/dwight/.thunderbird/34vt6ic0.default/search.json
30670853   44 -rw-r--r--   1 dwight   dwight      44511 Aug 23 08:16 /home/dwight/.thunderbird/34vt6ic0.default/blocklist.xml
30670889  448 -rwxrwxr--   1 dwight   dwight     458752 Aug  9 05:54 /home/dwight/.thunderbird/34vt6ic0.default/extensions.sqlite
30670925   64 -rwxrwxr--   1 dwight   dwight      65536 Jul 31 14:46 /home/dwight/.thunderbird/34vt6ic0.default/downloads.sqlite
30675329 5120 -rwxrwxr--   1 dwight   dwight    5242880 Sep 30  2012 /home/dwight/.thunderbird/34vt6ic0.default/urlclassifier3.sqlite
30671784    4 -rwxrwxr--   1 dwight   dwight          2 Aug 11 23:40 /home/dwight/.thunderbird/34vt6ic0.default/directoryTree.json
30670964    4 -rwxrwxr--   1 dwight   dwight        482 Sep 24  2012 /home/dwight/.thunderbird/34vt6ic0.default/mailViews.dat
30670952   16 -rwxrwx---   1 dwight   dwight      16384 Sep 24  2012 /home/dwight/.thunderbird/34vt6ic0.default/secmod.db
30671771    0 -rwxrwxr--   1 dwight   dwight          0 Aug 20 14:04 /home/dwight/.thunderbird/34vt6ic0.default/places.sqlite-wal
30670949    4 drwxrwx---   2 dwight   dwight       4096 Jul  8 00:59 /home/dwight/.thunderbird/34vt6ic0.default/minidumps
30671105    4 -rwxrwxr--   1 dwight   dwight         10 Aug 20 14:03 /home/dwight/.thunderbird/34vt6ic0.default/virtualFolders.dat
30671875    4 -rwxrwxr--   1 dwight   dwight        168 Aug 20 14:03 /home/dwight/.thunderbird/34vt6ic0.default/folderTree.json
30670946    4 -rwxrwxr--   1 dwight   dwight         94 Sep 24  2012 /home/dwight/.thunderbird/profiles.ini


```

---

### Post by sudodus on 2013-08-23
I don't see anything wrong, but now there is a lot of information for some expert to check :-)

---

### Post by free10 on 2013-08-23
OK thanks. We may be hunting in the wrong areas but I don't know where the tiger really lives either:D

Have some blanking out on apps, where for example I have an app hidden in the sidebar like VLC with a movie paused, and when I click to see it it looks blank and resizing can make it visible again. A number of apps can do this and when a lt do it usually killing them and then restarting those apps make them visible again. This has been going on for months and months. 

What made me think of it was when the other probablem with error code happens with tmp Thunderbird besides not saving drafts will kind of go blank, if I try and look at the sent or other folders in thunderbird, and it opens them, but with a list but nothing else. Of course once I reboot and Ubuntu corrects tmp everything is back to normal.

---

### Post by VMC on 2013-08-23
Is the "sticky" bit set on your tmp directory?
```
ls -ld /tmp
drwxrwxrw**t** 10 root root 4096 Aug 23 18:28 
```

---

### Post by free10 on 2013-08-23
When I copied and pasted that command the big T said command not found.

---

### Post by Bashing-om on 2013-08-23
free10; hey;
```

ls -ld /tmp

```(???)

should have returned similar:
> 
sysop@1304mini:~$ ls -ld /tmp
drwxrwxrwt 8 root root 240 Aug 23 22:17 /tmp
sysop@1304mini:~$


just try'n to help

---

### Post by free10 on 2013-08-24
```
dwight@dwight-desktop:~$ $ ls -ld /tmpdrwxrwxrw*t* 10 root root 4096 Aug 23 18:28 /tmp
$: command not found

```

Did not return anything

New command returned

```

drwxrwxrwt 13 root root 4096 Aug 23 21:28 /tmp


```

I know

---

### Post by VMC on 2013-08-24
> **free10 said:**
> When I copied and pasted that command the big T said command not found.
I edit my post to make it more clear. '*ls -d /tmp*' is the command to use.
edit:OK. You have the 'sticky' set correct. I had that issue once.

---

### Post by free10 on 2013-08-24
> **VMC said:**
> I edit my post to make it more clear. '*ls -d /tmp*' is the command to use.
edit:OK. You have the 'sticky' set correct. I had that issue once.

OK, thanks.

---

### Post by free10 on 2013-09-24
Just happend again and when it did went looking around and found all my folders were locked. Of course on reboot it said again can't find /temp or it is not ready yet, and do you want the fix it or the other options):P

---

