---
title: "2 problems. Flash install error, windows dont open sometimes"
date: 2007-08-07
forum: General Help
---

### Post by whorobj on 2007-08-07
first problem-
installer doesn't work on 64 bit apparently-
```
rob@rob-desktop:~/install_flash_player_9_linux$ ./flashplayer-installer

ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.

```


if i try to uninstall/install anything flash based or flash itself in another way i always get this-
```
(it's an error with lib-howl0 or something,(trying to recreate error)
```




My second problem-
Alot of the time nothing will open. computer, home, etc ill click it and it will say starting .... etc.. and never open. Sometimes gaim and firefox take like 30 seconds to open which is stupid with a gig of ram and an amd 64 3000.  This happens in both metacity and emerald. sometimes if i reload each a few times i can get folders to open.

---

### Post by dougfractal on 2007-08-07
check this out
> **pay said:**
> You can use nspluginwrapper to install 32bit plugins with a 64bit browser or you can install a 32bit browser with a 32bit plugin. Read this for the latter [http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit](http://www.ubuntuforums.org/showthread.php?t=202537&highlight=flash+64bit)


> My second problem-
That a big problem. I'll get back on that.

---

### Post by whorobj on 2007-08-07
> **dougfractal said:**
> check this out




That a big problem. I'll get back on that.
yeah none of my folders will open at all right now :mad:

also, my wallpaper never saves .yes it's local. and i noticed that my network drive mount doesnt show on my desktop when i have the folder problem. sometimes my network manager icon doesnt show alot of the time.

---

### Post by dougfractal on 2007-08-07
> **whorobj said:**
> yeah none of my folders will open at all right now :mad:

also, my wallpaper never saves. yes it's local.


[https://bugs.launchpad.net/ubuntu/+bug/94048](https://bugs.launchpad.net/ubuntu/+bug/94048)
> Having used Feisty as my primary desktop, I noticed that applications take some time to load, even when another instance is already open; for example, gnome-terminal would take 5-10 seconds to load a new window even if another is already open, and without significant application load. Having done some research*, I modified /etc/hosts, changing this line:

127.0.0.1 localhost

to this ('inspiron' being my hostname):

127.0.0.1 localhost inspiron

After this little modification, most gnome applications seem to load much faster and persist in cache longer, so opening another gnome-terminal take usually ~1sec rather than 10 seconds, and other application follow the same pattern.

sudo nano /etc/hosts


But I think you have bigger probs.
boot from liveCD check you harddrive.
**partition must not be mounted**

    * e2fsck program is used to check and repair a linux ext2 or ext3 filesystem. 

So something like:

e2fsck -f /dev/hdxx

WARNING COULD GO BADLY WRONG. check around first

---

### Post by whorobj on 2007-08-07
```
Setting up libavahi-compat-howl0 (0.6.17-0ubuntu3) ...
Bus error (core dumped)
dpkg: error processing libavahi-compat-howl0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libsilc-1.0-2 (0.9.12-6) ...
Bus error (core dumped)
dpkg: error processing libsilc-1.0-2 (--configure):
 subprocess post-installation script returned error exit status 135

```

---

### Post by whorobj on 2007-08-07
the hostname fix made a HUGE difference. now if i didnt have that folder problem....
I only have one hdd so how exactly should i run e2fsck?

---

### Post by dougfractal on 2007-08-07
> the hostname fix made a HUGE difference
I don't know why launchpad dismissed it.

make a post. to [https://bugs.launchpad.net/ubuntu/+bug/94048](https://bugs.launchpad.net/ubuntu/+bug/94048)


> **whorobj said:**
> ```
Setting up libavahi-compat-howl0 (0.6.17-0ubuntu3) ...
Bus error (core dumped)
dpkg: error processing libavahi-compat-howl0 (--configure):
 subprocess post-installation script returned error exit status 135
Setting up libsilc-1.0-2 (0.9.12-6) ...
Bus error (core dumped)
dpkg: error processing libsilc-1.0-2 (--configure):
 subprocess post-installation script returned error exit status 135

```


forget e2fsck for now it looks as if its a library problem.

You have to sort out apt-get.
sudo apt-get install --reinstall libavahi-compat-howl0 libsilc-1.0-2

or 
sudo apt-get remove libavahi-compat-howl0 libsilc-1.0-2

if it wants to remove loads, you could copy that list to file then install again.

Either way this could take a few attempts.
just keep posting those logs ;-)

---

### Post by whorobj on 2007-08-07
it ran fsck on boot, fixed some errors for about half an hour now everyhting just seems laggy. mouse lags.

folders still wont open.






```

rob@rob-desktop:~$ sudo apt-get install --reinstall libavahi-compat-howl0 libsilc-1.0-2
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  sysutils procinfo tofrodos memtester liblog4j1.2-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libavahi-compat-howl0 (0.6.17-0ubuntu3) ...

Setting up libsilc-1.0-2 (0.9.12-6) ...

rob@rob-desktop:~$ 

```
:)

---

### Post by dougfractal on 2007-08-07
```
killall firefox
```
```
sudo /etc/init.d/gdm #restart X
```
```
sudo shutdown -r now   # restart
```

I'm sure firefox in ubuntu (+ flash) has a memory leak, bringing feisty down to it's knees. so killing firefox once a day helps.
I think its better in gusty.


You **MUST use a liveCD** to use e2fsck  any linux distro will do.

---

### Post by dougfractal on 2007-08-07
> now everyhting just seems laggy

are you running compiz?

---

### Post by whorobj on 2007-08-07
beryl. yes. just restarted using default gnome/metacity. sill no folders open and no icons show on the desktop and thr gnome panel menu is very slow and laggy.  system has been up for about 5 minutes and the network icon just loaded

---

### Post by whorobj on 2007-08-08
this is pretty annoying

```

rob@rob-desktop:/var/log$ tail -f syslog
Aug  7 23:59:34 localhost kernel: [  255.446018] end_request: I/O error, dev hda, sector 22723263
Aug  8 00:03:25 localhost kernel: [  402.201726] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Aug  8 00:03:25 localhost kernel: [  402.201734] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=21145855, high=1, low=4368639, sector=21145855
Aug  8 00:03:25 localhost kernel: [  402.201746] ide: failed opcode was: unknown
Aug  8 00:03:25 localhost kernel: [  402.201751] end_request: I/O error, dev hda, sector 21145855
Aug  8 00:03:27 localhost kernel: [  404.142391] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Aug  8 00:03:27 localhost kernel: [  404.142398] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=21145855, high=1, low=4368639, sector=21145855
Aug  8 00:03:27 localhost kernel: [  404.142410] ide: failed opcode was: unknown
Aug  8 00:03:27 localhost kernel: [  404.142415] end_request: I/O error, dev hda, sector 21145855
Aug  8 00:04:12 localhost kernel: [  449.392564] nautilus[5719]: segfault at 0000000000000008 rip 00002b48a9589bf2 rsp 00007fff01529b20 error 4

```
```

rob@rob-desktop:/var/log$ tail -f /var/log/messages
Aug  8 00:03:27 localhost kernel: [  404.142415] end_request: I/O error, dev hda, sector 21145855
Aug  8 00:04:12 localhost kernel: [  449.392564] nautilus[5719]: segfault at 0000000000000008 rip 00002b48a9589bf2 rsp 00007fff01529b20 error 4
Aug  8 00:14:10 localhost gconfd (root-6138): starting (version 2.18.0.1), pid 6138 user 'root'
Aug  8 00:14:10 localhost gconfd (root-6138): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Aug  8 00:14:10 localhost gconfd (root-6138): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Aug  8 00:14:10 localhost gconfd (root-6138): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Aug  8 00:14:10 localhost gconfd (root-6138): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Aug  8 00:14:10 localhost gconfd (root-6138): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Aug  8 00:14:40 localhost gconfd (root-6138): GConf server is not in use, shutting down.
Aug  8 00:14:40 localhost gconfd (root-6138): Exiting

```
still seems like a disk problem to me. 
i booted into the livecd and ran e2fsck about 3 times, found errors every time.

---

### Post by dougfractal on 2007-08-08
Bad luck.
New drive time.

---

### Post by whorobj on 2007-08-08
> **dougfractal said:**
> Bad luck.
New drive time.:(

---

