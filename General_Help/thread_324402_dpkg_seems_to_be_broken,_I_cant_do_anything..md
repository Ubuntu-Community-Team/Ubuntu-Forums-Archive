---
title: "dpkg seems to be broken, I cant do anything."
date: 2006-12-23
forum: General Help
---

### Post by slimdog360 on 2006-12-23
Yesterday I was trying to install some extra fonts using Automatix and now nothing works. Everytime I try to sudo apt-get install something I get this message.
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

so I do that and then this is what happens
```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
nick@nick-desktop:~$ sudo dpkg --configure -a
Setting up msttcorefonts (1.2ubuntu3) ...
warning: /usr/share/fonts/X11/truetype does not exist or is not a directory
warning: /usr/lib/X11/fonts/truetype does not exist or is not a directory
These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.
--09:26:12--  http://belnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving belnet.dl.sourceforge.net... failed: Connection timed out.
--09:26:22--  http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... failed: Connection timed out.
--09:26:32--  http://twtelecom.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving twtelecom.dl.sourceforge.net... failed: Connection timed out.
--09:26:42--  http://aleron.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving aleron.dl.sourceforge.net... failed: Connection timed out.
--09:26:52--  http://cesnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving cesnet.dl.sourceforge.net... failed: Connection timed out.
--09:27:02--  http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... failed: Connection timed out.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts
nick@nick-desktop:~$
```

Can someone help me please

---

### Post by riven0 on 2006-12-23
Alright, what happens if you try:

> sudo apt-get -f remove msttcorefonts

And if that doesn't work, (be careful on this, though, make sure it doesn't try to remove your entire desktop!):

> sudo apt-get -f autoremove msttcorefonts

---

### Post by towsonu2003 on 2006-12-23
are you connected to the net? you need t be connected to the net then dpkg --configure -a should work. because the package is trying to get fonts from another website.  

if you can't, what does dpkg -r msttcorefonts say?

---

### Post by slimdog360 on 2006-12-23
thanks, Im back to a working desktop now. It was just a matter of removing the msttcorefonts package. Thanks again.

---

### Post by stucky on 2006-12-23
I'm having a similar issue but it's affecting EVERYTHING I try to updat/upgrade/remove/reconfigure. It always ends with the following:

```

(Reading database ... dpkg: error processing kde (--remove):
 failed in buffer_read(fd): files list for package `libart-2.0-dev': Invalid argument
Errors were encountered while processing:
 kde
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

At least I can still listen to Mingus and browse the web, but this is getting frustrating.:cry:

---

### Post by towsonu2003 on 2006-12-23
can you post the whole error message? and also, what did you do right before apt / dpkg was broken?

---

### Post by stucky on 2006-12-23
I used cruft solely as an example since it was one of the packages I tried installing when I first saw things going wrong. 

To answer your main question, I have no idea what I had just done. Everything had been working fine and I got a notification that there were updates available. When I tried to apply them that's the first time I saw this occur.

```

sudo apt-get install cruft
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cruft
0 upgraded, 1 newly installed, 0 to remove and 88 not upgraded.
Need to get 0B/47.3kB of archives.
After unpacking 1122kB of additional disk space will be used.
(Reading database ... dpkg: error processing /var/cache/apt/archives/cruft_0.9.6-0.15_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libart-2.0-dev': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/cruft_0.9.6-0.15_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by towsonu2003 on 2006-12-23
**edited**
I was expecting a bit longer of an error thingy. 

What does ```
sudo apt-get clean
dpkg -r libart-2.0-dev
```say?

If that fails, backup your files. I found this: [http://www.ubuntuforums.org/archive/index.php/t-12272.html](http://www.ubuntuforums.org/archive/index.php/t-12272.html) 

so, if the above fails, pls do
```

sudo apt-get install cruft
dmesg| tail
``` and let's see what dmesg tells us. 

than copy paste the errors of ```
dpkg -r libart-2.0-dev
```
**done editing**

---

### Post by stucky on 2006-12-24
Sorry, that's all it gives me,

Here's the results of the first two:
```

dave@Loki:~$ sudo apt-get clean
dave@Loki:~$ sudo dpkg -r libart-2.0-dev
dpkg: dependency problems prevent removal of libart-2.0-dev:
 kdelibs4-dev depends on libart-2.0-dev (>= 2.3.17).
dpkg: error processing libart-2.0-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libart-2.0-dev
dave@Loki:~$ 

```

Second part:

```

dave@Loki:~$ sudo apt-get install cruft
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cruft
0 upgraded, 1 newly installed, 0 to remove and 88 not upgraded.
Need to get 47.3kB of archives.
After unpacking 1122kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com edgy/universe cruft 0.9.6-0.15 [47.3kB]
Fetched 47.3kB in 12s (3707B/s)                                                
(Reading database ... dpkg: error processing /var/cache/apt/archives/cruft_0.9.6-0.15_i386.deb (--unpack):
 failed in buffer_read(fd): files list for package `libart-2.0-dev': Invalid argument
Errors were encountered while processing:
 /var/cache/apt/archives/cruft_0.9.6-0.15_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
dave@Loki:~$ dmesg| tail
[17199982.732000] Inbound IN=wlan0 OUT=  LEN=48 TOS=0x00 PREC=0x20 TTL=105 ID=47527 DF PROTO=TCP SPT=2946 DPT=48086 WINDOW=64512 RES=0x00 SYN URGP=0 
[17199985.756000] Inbound IN=wlan0 OUT=  LEN=48 TOS=0x00 PREC=0x20 TTL=105 ID=47665 DF PROTO=TCP SPT=2946 DPT=48086 WINDOW=64512 RES=0x00 SYN URGP=0 
[17199991.688000] Inbound IN=wlan0 OUT=  LEN=48 TOS=0x00 PREC=0x20 TTL=105 ID=47935 DF PROTO=TCP SPT=2946 DPT=48086 WINDOW=64512 RES=0x00 SYN URGP=0 
[17208900.516000] init_special_inode: bogus i_mode (110602)
[17209337.148000] init_special_inode: bogus i_mode (110602)
[17209379.064000] cdrom: This disc doesn't have any tracks I recognize!
[17209475.156000] scsi: unknown opcode 0x01
[17209753.500000] cdrom: This disc doesn't have any tracks I recognize!
[17210708.996000] init_special_inode: bogus i_mode (110602)
[17211285.380000] init_special_inode: bogus i_mode (110602)
dave@Loki:~$ 

```

Finally:

```

dave@Loki:~$ sudo dpkg -r libart-2.0-dev
dpkg: dependency problems prevent removal of libart-2.0-dev:
 kdelibs4-dev depends on libart-2.0-dev (>= 2.3.17).
dpkg: error processing libart-2.0-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libart-2.0-dev
dave@Loki:~$ 


```
```

dave@Loki:~$ sudo dpkg -r kdelibs4-dev libart-2.0-dev
dpkg: dependency problems prevent removal of kdelibs4-dev:
 kdemultimedia-dev depends on kdelibs4-dev (>= 4:3.5.3).
dpkg: error processing kdelibs4-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libart-2.0-dev:
 kdelibs4-dev depends on libart-2.0-dev (>= 2.3.17).
dpkg: error processing libart-2.0-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 kdelibs4-dev
 libart-2.0-dev

```

---

### Post by stucky on 2006-12-24
dupe

---

### Post by towsonu2003 on 2006-12-24
> ~$ sudo dpkg -r kdelibs4-dev libart-2.0-dev
dpkg: dependency problems prevent removal of kdelibs4-dev:
 kdemultimedia-dev depends on kdelibs4-dev (>= 4:3.5.3).

what happens when you go recursive on dpkg? so try removing kdemultimedia-dev
if it has some dependency, remove that etc etc until you encounter an important package (any package that doesn't end with -dev may be important). (go one by one, not everything in one line)

also, edit you previous post and remove the 3 lines that start with "Inbound" from there. you don't want pple to know mac and ip addresses of your network ;)

Also, I wonder if this is relevant in your dmesg:
```
[17208900.516000] init_special_inode: bogus i_mode (110602)
[17209337.148000] init_special_inode: bogus i_mode (110602)
[17209379.064000] cdrom: This disc doesn't have any tracks I recognize!
[17209475.156000] scsi: unknown opcode 0x01
[17209753.500000] cdrom: This disc doesn't have any tracks I recognize!
[17210708.996000] init_special_inode: bogus i_mode (110602)
[17211285.380000] init_special_inode: bogus i_mode (110602)
```

but I have no idea at all... maybe someone else?

---

### Post by towsonu2003 on 2006-12-24
note that it may as well be a corrupt filesystem issue, as mentioned at [http://www.ubuntuforums.org/archive/index.php/t-12272.html](http://www.ubuntuforums.org/archive/index.php/t-12272.html)

---

### Post by stucky on 2006-12-24
Thanks for pointing out that little security breach. I should have known better.

I went recursive and practically medieval as you suggested, to no avail.

```
dave@Loki:~$ sudo dpkg -r kdelibs4-dev libart-2.0-dev kdemultimedia-dev
dpkg: dependency problems prevent removal of kdemultimedia-dev:
 libarts1-audiofile depends on kdemultimedia-dev.
dpkg: error processing kdemultimedia-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of kdelibs4-dev:
 kdemultimedia-dev depends on kdelibs4-dev (>= 4:3.5.3).
dpkg: error processing kdelibs4-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libart-2.0-dev:
 kdelibs4-dev depends on libart-2.0-dev (>= 2.3.17).
dpkg: error processing libart-2.0-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 kdemultimedia-dev
 kdelibs4-dev
 libart-2.0-dev
dave@Loki:~$ sudo dpkg -r kdelibs4-dev libart-2.0-dev kdemultimedia-dev libarts1-audiofile
dpkg: dependency problems prevent removal of libarts1-audiofile:
 kdemultimedia depends on libarts1-audiofile (>= 4:3.5.5-0ubuntu1).
dpkg: error processing libarts1-audiofile (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of kdemultimedia-dev:
 libarts1-audiofile depends on kdemultimedia-dev.
dpkg: error processing kdemultimedia-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of kdelibs4-dev:
 kdemultimedia-dev depends on kdelibs4-dev (>= 4:3.5.3).
dpkg: error processing kdelibs4-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libart-2.0-dev:
 kdelibs4-dev depends on libart-2.0-dev (>= 2.3.17).
dpkg: error processing libart-2.0-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libarts1-audiofile
 kdemultimedia-dev
 kdelibs4-dev
 libart-2.0-dev
dave@Loki:~$ sudo dpkg -r kdelibs4-dev libart-2.0-dev kdemultimedia-dev libarts1-audiofile kdemultimedia
dpkg: dependency problems prevent removal of kdemultimedia:
 kde depends on kdemultimedia (>= 4:3.4.3).
dpkg: error processing kdemultimedia (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libarts1-audiofile:
 kdemultimedia depends on libarts1-audiofile (>= 4:3.5.5-0ubuntu1).
dpkg: error processing libarts1-audiofile (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of kdemultimedia-dev:
 libarts1-audiofile depends on kdemultimedia-dev.
dpkg: error processing kdemultimedia-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of kdelibs4-dev:
 kdemultimedia-dev depends on kdelibs4-dev (>= 4:3.5.3).
dpkg: error processing kdelibs4-dev (--remove):
 dependency problems - not removing
dpkg: dependency problems prevent removal of libart-2.0-dev:
 kdelibs4-dev depends on libart-2.0-dev (>= 2.3.17).
dpkg: error processing libart-2.0-dev (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 kdemultimedia
 libarts1-audiofile
 kdemultimedia-dev
 kdelibs4-dev
 libart-2.0-dev
dave@Loki:~$ sudo dpkg -r kdelibs4-dev libart-2.0-dev kdemultimedia-dev libarts1-audiofile kdemultimedia kde
(Reading database ... dpkg: error processing kde (--remove):
 failed in buffer_read(fd): files list for package `libart-2.0-dev': Invalid argument
Errors were encountered while processing:
 kde
Processing was halted because there were too many errors.
dave@Loki:~$ 


```

I hate having to start from scratch again. I'll study the other link in the morning. Thanks for the help.

---

