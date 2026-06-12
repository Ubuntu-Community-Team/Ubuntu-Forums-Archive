---
title: "Date/Time not being updated"
date: 2006-10-30
forum: General Help
---

### Post by TexLogic on 2006-10-30
Hello,

I'm running Edgy (6.10) in a Parallels virtual machine under OS X on an Intel iMac.  It works great (very fast with 512MB RAM assigned to the VM), however, for some reason the system does not appear to be querying ntp servers to update time and date information.  In particular, if I put the iMac to sleep, when it wakes up, the clock in the Ubuntu session is several hours behind.  (The Mac host itself updates immediately upon waking up.)  I can update the time/date info with a one-time query to an ntp server, but when I then tell the system to update automatically, nothing happens.  I have several ntp servers selected, of course.  No other network problems other than this.

Any help here much appreciated.

TexLogic

---

### Post by blind0wl on 2006-10-30
Make sure ntp-server is running at your boot time, if you havent already got it

```
sudo apt-get install rcconf
```

run rcconf from the console and see if ntp-server is in the list and selected.

Cheers

Blindy

---

### Post by TexLogic on 2006-10-30
> **blind0wl said:**
> Make sure ntp-server is running at your boot time, if you havent already got it

```
sudo apt-get install rcconf
```

run rcconf from the console and see if ntp-server is in the list and selected.

Thanks; I'm beginning to remember how things work in Linux after using only Mac OS X and FreeBSD for several years.  ntp-server isn't in the list that rcconf displays, but I started ntp-server manually and then opened the KDE time/date control thingy and told it to to auto updates.  That did the trick for now.  I see ntp-server in /etc/rc3.d -- isn't tha supposed to be the directory under Linux that determines what servers start at boot?  It seems ntp-server wasn't running despite its presence in rc3.d.  Anything I can do to make sure it's starting?

TexLogic

---

### Post by blind0wl on 2006-10-30
in your rcconf, just tick it, or you can manually add it

```
sudo update-rc.d ntp-server default
```

Cheers

Blindy

---

### Post by TexLogic on 2006-10-30
> **blind0wl said:**
> in your rcconf, just tick it, or you can manually add it

```
sudo update-rc.d ntp-server default
```

Cheers

Blindy

Hm, there seems to be a disconnect betwixt these two.  rcconf only shows lists dbus, gdm, hplip, and usplash as starting, and ntp-server isn't even an option.  However, 
```
sudo update-rc.d ntp-server defaults
```
Yields:
> System startup links for /etc/init.d/ntp-server already exist.
Why are these two out of sync?

TexLogic

---

### Post by blind0wl on 2006-10-31
Ok, can you log the output of your rcconf and then output the log of 

```
ls -al /etc/rc*
```

It sounds strange because rcconf should read the /etc/init.d/ directory and all of the rc.?d directorys.

Cheers

Blindy

---

### Post by TexLogic on 2006-10-31
> **blind0wl said:**
> in your rcconf, just tick it, or you can manually add it

```
sudo update-rc.d ntp-server default
```
Cheers

Blindy

> **blind0wl said:**
> Ok, can you log the output of your rcconf and then output the log of 

```
ls -al /etc/rc*
```

It sounds strange because rcconf should read the /etc/init.d/ directory and all of the rc.?d directorys.


Well, I don't know where rcconf is looking.  All I see is this (I've replaced asterisks with x's, as things weren't displaying properly in the preview with the former):

```
[FONT="Courier New"]
[x] dbus                  simple interprocess messaging syst
[x] gdm                   GNOME Display Manager             
[x] hplip                 HP Linux Printing and Imaging Syst
[x] usplash               Userspace bootsplash utility      
[ ] avahi-daemon          Avahi mDNS/DNS-SD daemon          
[ ] bootclean             Scripts for initializing and shutt
[ ] bootlogd              Scripts for initializing and shutt
[ ] hdparm                tune hard disk parameters for high
[ ] laptop-mode           Scripts to spin down hard drive an
[ ] stop-bootlogd         Scripts for initializing and shutt[/FONT]
```
IIRC, Linux looks in rc3.d at startup, which looks like this:

```
[FONT="Courier New"]/etc/rc3.d:
README       S19cupsys        S20nvidia-kernel  S89cron
S01apport    S19hplip         S20powernowd      S90binfmt-support
S05vbesave   S20apmd          S20rsync          S98usplash
S10acpid     S20dbus          S25bluetooth      S99acpi-support
S10sysklogd  S20festival      S50ntp-server     S99rc.local
S11klogd     S20hotkey-setup  S89anacron        S99rmnologin
S13gdm       S20makedev       S89atd[/FONT]
```

None of the rc[0-6].d dirs reflect rcconf.

Thanks.

TexLogic

---

### Post by blind0wl on 2006-10-31
hmm...can you try download bum (its a gui Boot Up Manager)

```
sudo apt-get install bum
```

I want to see if it displays anything different...it could be something that rcconf is reading something out of rc.local or something similar.

---

### Post by TexLogic on 2006-11-02
> **blind0wl said:**
> hmm...can you try download bum (its a gui Boot Up Manager)

```
sudo apt-get install bum
```

I want to see if it displays anything different...it could be something that rcconf is reading something out of rc.local or something similar.

Sure, but before I do, I want to make sure I don't hose anything.  I am in fact running Ubuntu in a Parallels Virtual Machine under Mac OS X (an amazing piece of software, Parallels) and I made some changes to the way Ubuntu boots in /boot/grub/menu.lst to deal with some problems with clock synchronization (see [http://www.xs4all.nl/~hajk/pbook-install.pdf)](http://www.xs4all.nl/~hajk/pbook-install.pdf)).  Will installing or using bum ignore or alter those changes?

TexLogic

---

