---
title: "locked sudo"
date: 2007-01-30
forum: General Help
---

### Post by QÉD² on 2007-01-30
I am locked out of sudo. Does anyone know how to re-enable it?

This was what I did before finding out the proper way of doing the thing:

$ sudo chmod -rw-r----- /etc/sudoers


I tried to chmod it back by

$ sudo chmod u+rw /etc/sudoers

But it's **too late**! I am locked out, getting this message about permission 00, should be 0440. Please help!

---

### Post by Ramses de Norre on 2007-01-30
Boot into recovery mode and run **chmod 0440 /etc/sudoers**. And don't mess with things like sudoers if you don't know exactly what you're doing...

---

### Post by QÉD² on 2007-01-30
I cannot boot into Recovery. I followed [https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy]("https://help.ubuntu.com/community/EncryptedFilesystemHowtoEdgy") and edited my grub pointing the kernels to /dev/mapper/cryptroot. When I tried to boot into Recovery, I got a black screen with a blinking cursor. So I rebooted normally, entered the luks passphrase, and here I am.

Please help me get my sudo back!

---

### Post by taurus on 2007-01-30
Boot with the LiveCD.  Then mount the partition where / is and change the permission back to what it was before.

Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming that / is on /dev/hda...)
sudo chmod 440 /mnt/ubuntu/etc/sudoers
sudo umount /mnt/ubuntu
```
Reboot.

---

### Post by QÉD² on 2007-01-30
I don't have a live CD. Which one should I download? Is it ***CD Image for Desktop and laptop PCs*** or ***Other Installation Options***?

---

### Post by Ramses de Norre on 2007-01-30
The first.

---

### Post by QÉD² on 2007-01-30
The Live CD is downloading now. Meanwhile, this is how my hda is partitioned:

hda1  /boot 
hda2 /dev/mapper/cryptroot
hda3 /dev/mapper/crypthome
hda5 /dev/mapper/cryptswap


About the mount -t  by Taurus,  do I mount /dev/hda1, or /dev/hda2, or /dev/mapper/cryptroot, to /mnt/ubuntu?

---

### Post by taurus on 2007-01-30
You want to mount / which looks like it would be /dev/hda2.  After mounting /dev/hda2 to /mnt/ubuntu and you can't see /mnt/ubuntu/etc, then unmount it and mount the /dev/hda1 but I guess this is your partition table:

/dev/hda1 --> /boot
/dev/hda2 --> /
/dev/hda3 --> /home
/dev/hda5 --> swap

---

### Post by QÉD² on 2007-01-31
Thanx guys! My sudo is back:KS  ! 

It was trying to get Firestarter to autoload that got me into trouble. This article [http://www.fs-security.com/docs/faq.php]("http://www.fs-security.com/docs/faq.php") said to edit /etc/sudoers, but I kept getting Permission Denied. Could you tell me how to add that line to /etc/sudoers?

---

### Post by taurus on 2007-01-31
You need to use visudo to edit /etc/sudoers.  

```
sudo visudo
```
Remember, you are using vi/vim as your text editor so if you want to insert text, use the arrows to move the cursor and then hit **i** for insert.  And when you are done inserting text, hit **Esc** and then **:wq!** to save and exit.

---

### Post by QÉD² on 2007-01-31
It's great I added that **NOPASSWD** line and changed to sbin into /etc/sudoers but Firestarter did not show up in ps -x.  I am using Edgy, did I miss something?

---

### Post by taurus on 2007-01-31
Post your /etc/sudoers and the output of this command.

```
sudo cat /etc/sudoers
ps -A
```

---

### Post by QÉD² on 2007-01-31
This is **/etc/sudoers**:

# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
nescio ALL= NOPASSWD: /usr/sbin/firestarter


And **ps -A**:

PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 migration/0
    3 ?        00:00:00 ksoftirqd/0
    4 ?        00:00:00 watchdog/0
    5 ?        00:00:00 events/0
    6 ?        00:00:00 khelper
    7 ?        00:00:00 kthread
    9 ?        00:00:00 kblockd/0
   10 ?        00:00:00 kacpid
   11 ?        00:00:00 kacpi_notify
  108 ?        00:00:00 kseriod
  141 ?        00:00:00 pdflush
  142 ?        00:00:00 pdflush
  143 ?        00:00:00 kswapd0
  144 ?        00:00:00 aio/0
 1613 ?        00:00:00 ata/0
 1749 ?        00:00:00 khubd
 1760 ?        00:00:00 khpsbpkt
 1770 ?        00:00:00 knodemgrd_0
 1847 ?        00:00:00 kjournald
 1926 ?        00:00:00 logd
 2073 ?        00:00:00 udevd
 2840 ?        00:00:00 shpchpd
 2946 ?        00:00:00 kpsmoused
 3396 ?        00:00:00 dhclient3
 3602 tty1     00:00:00 getty
 3603 tty2     00:00:00 getty
 3604 tty3     00:00:00 getty
 3605 tty4     00:00:00 getty
 3606 tty5     00:00:00 getty
 3607 tty6     00:00:00 getty
 3818 ?        00:00:00 acpid
 3912 ?        00:00:00 syslogd
 3938 ?        00:00:00 dd
 3940 ?        00:00:00 klogd
 4012 ?        00:00:00 gdm
 4029 ?        00:00:00 gdm
 4037 tty7     00:00:23 Xorg
 4046 ?        00:00:00 cupsd
 4081 ?        00:00:00 hpiod
 4084 ?        00:00:00 python
 4132 ?        00:00:00 dbus-daemon
 4149 ?        00:00:01 hald
 4150 ?        00:00:00 hald-runner
 4156 ?        00:00:00 hald-addon-acpi
 4165 ?        00:00:00 hald-addon-keyb
 4185 ?        00:00:00 hald-addon-stor
 4187 ?        00:00:00 hald-addon-stor
 4205 ?        00:00:00 perl
 4281 ?        00:00:00 hcid
 4288 ?        00:00:00 sdpd
 4298 ?        00:00:00 krfcommd
 4331 ?        00:00:00 atd
 4344 ?        00:00:00 cron
 4432 ?        00:00:00 x-session-manag
 4467 ?        00:00:00 ssh-agent
 4470 ?        00:00:00 dbus-launch
 4471 ?        00:00:00 dbus-daemon
 4473 ?        00:00:00 gconfd-2
 4476 ?        00:00:00 gnome-keyring-d
 4479 ?        00:00:00 gnome-settings-
 4488 ?        00:00:00 sh
 4489 ?        00:00:00 esd
 4496 ?        00:00:01 metacity
 4501 ?        00:00:01 gnome-panel
 4503 ?        00:00:03 nautilus
 4507 ?        00:00:00 bonobo-activati
 4511 ?        00:00:00 gnome-vfs-daemo
 4512 ?        00:00:00 gnome-volume-ma
 4522 ?        00:00:00 update-notifier
 4526 ?        00:00:00 evolution-alarm
 4536 ?        00:00:00 gnome-cups-icon
 4548 ?        00:00:00 gnome-power-man
 4550 ?        00:00:00 trashapplet
 4567 ?        00:00:00 mapping-daemon
 4573 ?        00:00:00 mixer_applet2
 4582 ?        00:00:23 firefox-bin
 4604 ?        00:00:00 gnome-screensav
 4691 ?        00:00:00 gnome-terminal
 4693 ?        00:00:00 gnome-pty-helpe
 4696 pts/0    00:00:00 bash
 5466 pts/0    00:00:00 ps

---

### Post by taurus on 2007-01-31
I don't have firestarter installed on my desktop (only on the laptop in the office) but are you sure firestarter is in /usr/sbin!

```
whereis firestarter
```

---

### Post by QÉD² on 2007-01-31
It is in **sbin**:


```
~$ whereis firestarter
firestarter: /usr/sbin/firestarter /etc/firestarter /usr/share/firestarter /usr/share/man/man8/firestarter.8.gz
```

---

### Post by taurus on 2007-01-31
It is in /usr/sbin alright.  And I assume you can run firestarter from a terminal, yes?  Maybe this is nothing but what happens if you put an empty line between the last two commands in /etc/sudoers?

```

%admin ALL=(ALL) ALL

nescio ALL= NOPASSWD: /usr/sbin/firestarter

```

---

### Post by QÉD² on 2007-01-31
No, I just discovered that  System ->Administration ->Firestarter does not run either.  It said "Starting Firestarter ...", after a few seconds it disappered and nothing happened.

I added an empty line in /etc/sudoers, no change either. 

Does firestarter needs addtional library or packages?

> Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:4960): Gtk-WARNING **: cannot open display:  


---

### Post by taurus on 2007-01-31
Try to run it from a terminal to see exactly what the error message is.

```
firestarter
```

---

### Post by QÉD² on 2007-01-31
I had to use sudo firestarter, and this is what I got:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:4960): Gtk-WARNING **: cannot open display:  

```

---

### Post by taurus on 2007-01-31
Use gksudo when you open a GUI app.

```
gksudo firestarter
```
How did you install firestarter anyway?

---

### Post by QÉD² on 2007-01-31
I got exactly the same message:

```
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(firestarter:5447): Gtk-WARNING **: cannot open display:  

```

I tried both Synaptic and sudo apt-get install. Neither seemed to work.

---

### Post by QÉD² on 2007-01-31
The problem must be with the line of NOPASSWD command. I removed it from /etc/sudoers and firestarter works now.

---

