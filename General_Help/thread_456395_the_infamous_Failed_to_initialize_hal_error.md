---
title: "the infamous Failed to initialize hal error"
date: 2007-05-27
forum: General Help
---

### Post by dacnomania on 2007-05-27
I recently installed Ubuntu 7.04 and just after logging in (even on the live cd for installation) i recieve the error "Failed to initialize hal" and after some searching this seems to be a very common problem, so i will tell you guys what i have tried and what i haven't managed to try hopefully someone can help...

first off... my hardware is as follows
```

Motherboard = biostar m7ncd
Video Card = nvidia geforce 5200
Optical = Samsung dvd-ram drive (can find specific model number if necessary)
mouse = ps/2 micro innovations laser mouse (hey it was cheap =P)
keyboard = usb logitech "Elite keyboard"
hardrives are layed out as follows
HDA = 30gb primary drive
hda1 = 15gb ntfs (windows xp media center) mounted as /windows
hda2 = 20gb ext3 mounted as /
hda3 = 768mb swap
HDB = 80gb slave
hdb1 = 80gb fat32 for easy access to files for both windows and linux (i hope)

```

Things i have already tried

[LIST]
[*]start the computer with an audio cd in the drive (no change)
[*]Turn off automatic login (was never enabled to begin with)
[*]set samba shares not to auto load in etc/fstab (no samba shares setup)
[*]remove samba shares from /etc/fstab (again no samba shares to begin with)
[*]try waiting awhile before logging in (tried waiting about an hour, still fails)
[/LIST]

here is a copy of the contents of my /etc/fstab (not that i really understand half of it

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=24c91672-d9f2-4724-a1b7-bcb8cb2d73d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=A08A-F3FF  /storage        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda1
UUID=0CB8EA3FB8EA2744 /windows        ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=6176b577-131a-4a9c-b38a-ff304fca4f07 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

please bear with me for i am not extremely experienced with linux, 

Thanks in advance

---

### Post by dacnomania on 2007-05-27
oh and if anyone could tell me why it says i have no netwrok connection but yet i'm obviously connected to the internet that would be appreciated as well... =P

---

### Post by dacnomania on 2007-05-27
bump I REALLLLLLY need help

---

### Post by confused57 on 2007-05-27
This may help:
[http://ubuntuforums.org/showthread.php?t=396445&highlight=Missing](http://ubuntuforums.org/showthread.php?t=396445&highlight=Missing)

---

### Post by dacnomania on 2007-05-29
has nothing to do with windows not booting, (though i havn't even bothered to try and will probably be deleteing the partition anyways) it's just annoying as all helll when nothing is auto detected like it should be

---

### Post by king20878 on 2007-06-17
I managed to get rid of the error by changing the priority of the dbus service in the Services control panel.  If you right-click on the entry you can edit its properties and change it from 20 to 1 for run-levels 3,4, and 5.  That seems to give it enough time to initialize.

---

### Post by jerremy-tamlin on 2007-06-21
I'm having the same problem it appeared after I installed Google Earth and avidemux but whether this has anything to do with I have no idea.

However, I do think I know why your network connection stopped working - mine did too until I switched it back to manual configuration by un-commenting/adding the appropriate lines in /etc/network/interfaces.
I'm not sure what version of Ubuntu you are using but Feisty (what I use) has a network manager that automatically detects network connections - when it's working that is. I assume this works with hal *(Hardware Abstraction Layer - for newbies, it provides a list of all hardware so that programs can easily find it and use it without having to be setup individually - at least that's the idea.)*
Anyway if hal is not working neither can network manager so setup you network manually by editing /etc/network/interfaces and running ```
/etc/init.d/networking restart
```

More info can easily be found about /etc/network/interfaces by typing ```
man interfaces
```
Also this site [http://www.debian.org/doc/manuals/reference/ch-gateway.en.html](http://www.debian.org/doc/manuals/reference/ch-gateway.en.html) gives a thorough description of networking in Debian which is very similar to Ubuntu.

---

### Post by jerremy-tamlin on 2007-06-21
Find info on HAL at [https://launchpad.net/hal](https://launchpad.net/hal) and/or [http://www.freedesktop.org/wiki/Software/hal](http://www.freedesktop.org/wiki/Software/hal)

I removed and then reinstalled HAL and all it's dependancies. This got rid of the failed to innitialize hal message but unfortunatly HAL still isn't running. I think this just stoped it trying to be run when I logon.

Since Hal is basically a list of all installed hardware, it interfaces with and is used by lots of diferent things. I think this must be why there are so many different fixes to similar bugs. The errors must have different causes but HAL doesn't tell us why it couldn't load it just says "Failed to Innitialize".

To get some idea of why it's failing start it from a terminal with the don't daemonise option (I think a daemon is a little process that separates off from the terminal that started it.)
```
sudo hald --daemon=no --verbose=yes
```
hald = the **hal d**aemon

The output this gives me is```
21:22:16.293 [I] hald.c:529: hal 0.5.9
21:22:16.296 [I] hald.c:594: Will not daemonize
21:22:16.297 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-dV1ZQMTwRP,guid=1a678c8d1f489aaa8e5cfd00467a7b88
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
21:22:16.302 [I] hald_runner.c:299: Runner has pid 16819
21:22:16.302 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
21:22:16.302 [E] hald_dbus.c:4461: Cannot get caller info for org.freedesktop.DBus
21:22:16.303 [I] hald_runner.c:180: runner connection is 0x8093588
21:22:16.304 [I] mmap_cache.c:242: Cache needs update
21:22:16.304 [I] mmap_cache.c:161: Regenerating fdi cache..
Run started hald-generate-fdi-cache (10000) (0) 
!  full path is '/usr/lib/hal/hald-generate-fdi-cache', program_dir is '/usr/lib/hal'
21:22:16.307 [I] create_cache.c:608: Loading rules
21:22:16.575 [E] create_cache.c:669: Cannot rename '/var/cache/hald/fdi-cache~' to '/var/cache/hald/fdi-cache': Operation not permitted
/usr/lib/hal/hald-generate-fdi-cache exited
21:22:16.576 [I] mmap_cache.c:137: In regen_cache_cb exit_type=0, return_code=1
21:22:16.576 [E] mmap_cache.c:190: fdi cache regeneration failed!
21:22:16.576 [I] mmap_cache.c:193: fdi cache generation done
21:22:16.576 [I] mmap_cache.c:251: cache mtime is 1182408630
*** [DIE] mmap_cache.c:di_rules_init():68 : Unable to open cache /var/cache/hald/fdi-cache


```

So my Hal can't load because it can't open /var/cache/hald/fdi-cache
This isn't suprising since /var/cache/hald/fid-cache has it's permissions set to ?-w--wx-w- and is owned by 988807168```
?-w--wx-w- 12 988807168 798147 0 1970-01-01 08:02 /var/cache/hald/fdi-cache
```The weird thing is that I can't change this even with sudo```
jesse@jesse-laptop:~$ sudo chmod 755 /var/cache/hald/fdi-cache 
chmod: changing permissions of `/var/cache/hald/fdi-cache': Operation not permitted

```
I've seen somewhere else something about Hal having policy rules? I don't know what these are but tomorrow I'm going to ask a question of the team at [https://launchpad.net/hal](https://launchpad.net/hal) Perhaps they can tell me whether 988807168 is some sort of Hal user connected with these policies and/or what fid-cache is/does.

If anyone else has any other info/errors regarding HAL please post them here. There are heaps of HAL errors with various fixes floating around perhaps we can start to build up an understanding of HAL and how to keep it working here on this thread. Then if we manage to get somewhere we could move it to the more official Hal Wiki at [http://www.freedesktop.org/wiki/Software/hal](http://www.freedesktop.org/wiki/Software/hal) - It sure needs some user friendly (non-programmer) documentation.
The purpose of HAL is to make hardware "Just Work" and it's great when it does but unfortunately HAL it's self doesn't "Just Work" a fair bit of the time. So we need some user friendly documentation both for those interested and for when problems occur.

---

### Post by jerremy-tamlin on 2007-06-22
**I Fixed My Problem!**

The problem _was_ to do with the permissions of /var/cache/hald/fdi-cache
It should not have been owned by 988807168 as this was actually filesystem error not a user.

/var is mounted on it's own ext3 partition on my system. I've had problems with my ext3 partitions before and am contemplating switching them to ext2. I haven't lost any data yet but have had to run fsck to fix things on three occasions now.

Anyway once I ran fsck to fix the filesystem Hal worked like it should.

---

### Post by mikeize on 2007-06-28
This is driving me crazy!  I tried this solution, but I don't have an "fdi-cache" file at all!
--------------------------------------------------------------------------
11:21:59.216 [I] hald.c:529: hal 0.5.9
11:21:59.217 [I] hald.c:594: Will not daemonize
11:21:59.217 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-VDcISvigtP,guid=b6f998e8d10b0a222050c0004683d217
11:21:59.268 [I] hald_runner.c:299: Runner has pid 6923
11:21:59.270 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
11:21:59.270 [E] hald_dbus.c:4461: Cannot get caller info for org.freedesktop.DBus
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
11:21:59.272 [I] hald_runner.c:180: runner connection is 0x8093a38
11:21:59.390 [I] mmap_cache.c:161: Regenerating fdi cache..
Run started hald-generate-fdi-cache (10000) (0) 
!  full path is '/usr/lib/hal/hald-generate-fdi-cache', program_dir is '/usr/lib/hal'
11:21:59.435 [I] create_cache.c:608: Loading rules
11:22:09.436 [I] mmap_cache.c:137: In regen_cache_cb exit_type=1, return_code=0
11:22:09.436 [E] mmap_cache.c:190: fdi cache regeneration failed!
11:22:09.437 [I] mmap_cache.c:193: fdi cache generation done
11:22:09.437 [I] mmap_cache.c:251: cache mtime is 1183041677
*** [DIE] mmap_cache.c:di_rules_init():68 : Unable to open cache /var/cache/hald/fdi-cache
---------------------------------------------------------------

Maybe that's the problem, I don't know.  Please help.

-mike


edit: here's the output from fsck:

----------------------------------------------------------
mikeize@ubuntu:~$ fsck
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
/media/host/wubi/disks/system.virtual.disk is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/media/host/wubi/disks/system.virtual.disk: recovering journal

/media/host/wubi/disks/system.virtual.disk: clean, 124329/1098880 files, 626942/2197265 blocks
e2fsck 1.40-WIP (14-Nov-2006)
/media/host/wubi/disks/home.virtual.disk is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes

/media/host/wubi/disks/home.virtual.disk: recovering journal
/media/host/wubi/disks/home.virtual.disk: clean, 974/91584 files, 33000/183105 blocks
----------------------------------------------------------------------

---

### Post by cabral on 2007-06-28
People,
Just try this simple command at a terminal:

sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12

After that, all  discs were mounted again!
Cheers!
Cabral

Source of this solution: [http://josevitor.blog.br/2007/06/03/failed-to-initialize-hal/#comment-876](http://josevitor.blog.br/2007/06/03/failed-to-initialize-hal/#comment-876)
:popcorn:

---

### Post by jerremy-tamlin on 2007-07-04
What does this do? ```
sudo update-rc.d -f dbus remove
sudo update-rc.d dbus defaults 12
```

The man page for update-rc.d seems to indicate that this will just ensure that dbus is set to be started 12th in the default runlevels. Do you know or have any ideas of why this would help?
```
       update-rc.d updates the System V style init  script  links  /etc/rcrun&#8208;
       level.d/NNname  whose  target  is  the  script /etc/init.d/name.  These
       links are run by init when it changes  runlevels;  they  are  generally
       used  to  start  and stop system services such as daemons.  runlevel is
       one of the runlevels supported by init, namely, 0123456789S, and NN  is
       the  two-digit  sequence  number  that determines where in the sequence
       init will run the scripts.
```
Wikipedia has a nice simple explanation of what a runlevel is [http://en.wikipedia.org/wiki/Runlevel]("http://en.wikipedia.org/wiki/Runlevel")

Cabral:
If update-rc.d doesn't fix your problem, it looks like your problem is that hal can't open fdi-cache because it can't create it for some reason```
Run started hald-generate-fdi-cache (10000) (0)
! full path is '/usr/lib/hal/hald-generate-fdi-cache', program_dir is '/usr/lib/hal'
11:21:59.435 [i] create_cache.c:608: Loading rules
11:22:09.436 [i] mmap_cache.c:137: In regen_cache_cb exit_type=1, return_code=0
11:22:09.436 [E] mmap_cache.c:190: fdi cache regeneration failed!
11:22:09.437 [i] mmap_cache.c:193: fdi cache generation done
```

I think you need to find out why this is. The line "In regen_cache_cb exit_type=1, return_code=0" looks like a reference to a sub or function in hald-generate-fdi-cache. Unfortunately this is a compiled program so you cant just look and see what it's doing there unless you download the source.

My advice would be to completely remove hal and then reinstall it. But before you do that double check that fdi-cache doesn't exist. Type: ```
sudo locate -u
sudo locate fdi-cache
```(locate -u updates the database used by locate.)
This should tell you for sure if fdi-cache exists and if it is in it's default location /var/cache/hald/fdi-cache

P.S.

> WARNING!!! Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)? yes


You answered yes! I've never been game to do that. I fixed mine when the boot process told me it had errors and asked for the root password to manually fix it. This gave me a prompt where I could run fsck before /var was mounted. (one of the advantages of having it on a different partition.) If yours doesn't do this then I would suspect that there are no errors on it and your problem with Hal is caused by something else. If you wanted to check it anyway I'd boot from the ubuntu CD.

---

### Post by inoxllor on 2007-07-08
In my case I was using an Ubuntu Wubi installation on my laptop and the HAL issue appeared after I installed Google Earth.

I´ve found that  "/var/cache/hald/fdi-cache"  _was somehow renamed_ into  "/var/cache/hald/fdi-cache~"

Use
**sudo cp /var/cache/hald/fdi-cache~ /var/cache/hald/fdi-cache**

Then 
**sudo chmod 755 /var/cache/hald/fdi-cache**

No more HAL issues...
Hope this helps. :D

---

### Post by mikeize on 2007-07-08
I'm also running Feisty with WUBI (on a Dell laptop), and get the HAL error.  Unfortunately the above solution did not fix it.  Still taking suggestions...

-mike

---

### Post by jerremy-tamlin on 2007-07-10
What is the output of ```
sudo hald --daemon=no --verbose=yes
``` Please post it so we can try to help.

---

### Post by mikeize on 2007-07-10
Okay, I don't know why but it is working now!  I just rebooted from windows xp over to feisty, and it skipped the login screen (like I set it to), and I didn't get the hal error, and it sees my cd drive and wireless card.  Just to test, I restarted nautilus (ctrl alt bkspce), and I had to sign in, and then got a bonobo error keeping nautilus from running.  Ctrl alt bspace again and everything is fine (hal and nautilus and all).  I hope it is totally fixed (however it happened), but I'll include the terminal readout below anyway.  Thanks for your response jerremy-tamlin.

------------------------------------------------------------

mikeize@ubuntu:~$ sudo hald --daemon=no --verbose=yes
Password:
14:14:09.022 [I] hald.c:529: hal 0.5.9
14:14:09.022 [I] hald.c:594: Will not daemonize
14:14:09.022 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-Is3Id2Hbcy,guid=37ae2c16903aaa12de4973004693cc71
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
14:14:09.028 [I] hald_runner.c:299: Runner has pid 6549
14:14:09.029 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
14:14:09.029 [E] hald_dbus.c:4461: Cannot get caller info for org.freedesktop.DBus
14:14:09.029 [I] hald_runner.c:180: runner connection is 0x8093a38
14:14:09.195 [I] mmap_cache.c:251: cache mtime is 1183846516
Error binding udev_event socket: Address already in use
mikeize@ubuntu:~$

--------------------------------------------------------------

---

### Post by Uncle Spellbinder on 2007-07-12
> **inoxllor said:**
> In my case I was using an Ubuntu Wubi installation on my laptop and the HAL issue appeared after I installed Google Earth.

I´ve found that  "/var/cache/hald/fdi-cache"  _was somehow renamed_ into  "/var/cache/hald/fdi-cache~"

Use
**sudo cp /var/cache/hald/fdi-cache~ /var/cache/hald/fdi-cache**

Then 
**sudo chmod 755 /var/cache/hald/fdi-cache**

No more HAL issues...
Hope this helps. :D

Worked for me.  No more error message.  But now, my 2 external hard drives do not show up on the desktop. Also, when I go to *places > computer*, they show, but they show as empty and I cannot open them.

Ideas anyone?

---

### Post by mikeize on 2007-07-12
Uncle spellbinder,

how about your cd/dvd drive?  does that work?  I too fixed my HAL problem, but have noticed that my cd drive shows up under "computer" (but not on the desktop), and gives a mount error when doubleclicked.  Still searching for the solution.

-mike

---

### Post by Uncle Spellbinder on 2007-07-12
Well, I've since re-installed. I've not yet been offered the Hal update.  All I know, if/when I am, I will not update.

---

### Post by bem9132 on 2007-07-22
Howdy, I wish I could say I was here to help, but just having began to try Ubuntu, I can not, in fact I have never used anything but windows so please bear with me in my lack on knowledge.....

I too am recieving this HAL error, I have found the error, (i think) but now what? how do I fix this? 
I am using Ubuntu 6.10 

this is the error.

18:58:29.119 [I] hald.c:469: hal 0.5.7.1
18:58:29.120 [I] hald.c:534: Will not daemonize
18:58:29.120 [I] hald_dbus.c:3236: local server is listening at unix:abstract=/tmp/hald-local/dbus-ifZNo9ePIH,guid=35fda3469cb799e0d5e2458c4f925f00
Runner started - allowed paths are '/usr/lib/hal:/usr/share/hal/scripts'
18:58:29.126 [I] hald_runner.c:115: Runner has pid 9982
Error binding udev_event socket: Address already in use


if anyone can point me in the correct direction, I would certainly appreciate it.

---

### Post by jzurawski99 on 2007-07-23
I also suffered from this problem.  After much searching, it seems that these hal issues might be the result of a recent hal update (just speculating).

Now, with me being a newbie at Ubuntu, take everything I say with a grain of salt.  But, these are the steps I followed (gathered from a few other posts) that got me up and running again.

In short, you need to roll back the hal update.  Below are the steps I followed to accomplish this.

First, when this error occured I lost all  USB, DVD drives and also my network connectivety (wireless and wired).

The line below allowed me to restart dbus and hal (I needed to get my connectivity back for the roll back).

sudo /etc/init.d/dbus restart

Whatever the above line did, it allowed me to manually reconfigure my wired connection (even though it didn't look like it was working, I was able to connect to the internet).

I then followed the instrucitions below to force the hal rollback.

The info below was pasted from a thread titled "Recent HAL update caused frequently failure for "suspend when lid closes"

***********************************************************************************

[COLOR="Blue"]Re: Recent HAL update caused frequently failure for "suspend when lid closes" 

--------------------------------------------------------------------------------

I think i found a temp workaround for this: rollback to older versions of those hal packages.

This can be done pretty easily with Synaptic package manager in Ubuntu:

1. Open Synaptic

2. Menu: file -> history, find the history of the day you installed the hal update. For me it is under "5/11":

Code:
Commit Log for Fri May 11 15:08:47 2007

Upgraded the following packages:
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)3. Now, search for each of the first 4 packages in Synaptic, then use "force version" in Package menu to force the latest version for each of them to be 0.5.8.1-4ubuntu12. When doing this for the first package, Synaptic automatically prompts to remove hal-info, which is what we want.

4. Now click on the "Apply" button. These packages will be downgraded to the good version.

5. After that, you'll immediately see the update manager pops up again to tell you there are new hal updates, this is the sign that the downgrading was successful. Of course this time you want to ignore the hal update...[/COLOR]

***************************************************************************************

Again, I have no idea what any of this effects.  All I know is that after following the above I regained all hardware functionality.  I hope this helps some of you.

JZ

---

### Post by jerremy-tamlin on 2007-07-23
bem9132
Please forgive me if I'm just stating the obvious but your Hal give the error
"Error binding udev_event socket: Address already in use"

A quick search for "undev_event socket Linux OR ubuntu" found me this post [http://bbs.archlinux.org/viewtopic.php?pid=254102](http://bbs.archlinux.org/viewtopic.php?pid=254102) which says that undev_event is started by hal
[QUOTE=http://bbs.archlinux.org/viewtopic.php?pid=254102]
It's complaining that there's already a hald running. If there's not, maybe it crashed and left udev bound to it? You might have to reboot if udev got screwed up.[/QUOTE]

The next step I would take would be to attempt to find out why hal crashed the first time. This would require you to find out where your startup logs are (I haven't figgured this out myself yet so I can't help you here, except to say that there seem to be several bootup logs and finding the right one is the trick) There is a common command that I think might give you what you need if you ran it just after boot. It is usually piped through 'tail' or something like that and shows the output of recent processes. Can anyone think of the command I'm describing?

I also like to understand how things work so I can fix them better in future so if I had time I'd probably try to find out what udev does and is for too. That might give you a way of closing it down so you can run hal again and see what the real problem is without having to find the logs.

Good luck.

---

### Post by ingo on 2008-01-25
> **inoxllor said:**
> **sudo cp /var/cache/hald/fdi-cache~ /var/cache/hald/fdi-cache**

Then 

**sudo chmod 755 /var/cache/hald/fdi-cache**It did it!!! Brilliant :guitar:
Thank you very much.

-- edited--

Now my system has stopped mounting usb sticks and cd roms/dvds altogether...???

---

### Post by ingo on 2008-01-26
Better way is to > sudo mv /var/cache/hald/fdi-cache~ /var/cache/hald/fdi-cacheor even better  > sudo /usr/lib/hal/hald-generate-fdi-cacheFound it [here.]("https://bugs.launchpad.net/ubuntu/+source/hal/+bug/139155")

---

### Post by spidernik84 on 2008-01-30
if manually starting dbus (with sudo /etc/init.d/dbus restart) does NOT give you errors, the problem may be related to dbus starting "too late" in the boot process.

To solve this it is possible to make the process fire up earlier in the services queue, doing this in a terminal:

```

# cd /etc/init.d/
# sudo mv S50dbus S12dbus

```

This is how i personally solved the problem. Oh my, i'm so happy, that error haunted me for two weeks :lolflag:

---

