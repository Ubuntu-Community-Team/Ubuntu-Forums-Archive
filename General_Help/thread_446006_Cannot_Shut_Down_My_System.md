---
title: "Cannot Shut Down My System"
date: 2007-05-16
forum: General Help
---

### Post by Sushubh on 2007-05-16
I am unable to hibernate my system. It ends up with a flashing cursor.

Now I see that i cannot even shut down my machine. It ends up at this screen...


[[IMG]http://farm1.static.flickr.com/191/501026908_2a4174238e.jpg[/IMG]]("http://www.flickr.com/photo_zoom.gne?id=501026908&size=m")

---

### Post by ago on 2007-05-16
Hybernation is a known bug, but shutdown should work. Can you check if you see /etc/rc6.d/S20fixsedsigs and /etc/rc0.d/S20fixsedsigs? Does rebooting work?

---

### Post by Sushubh on 2007-05-16
I installed Wubi 4-5 days back freshly downloaded from the site. I think shutdown was working before. i have attached the error message in the original post.

---

### Post by ago on 2007-05-16
That depends on /etc/rc6.d/S20fixsedsigs and /etc/rc0.d/S20fixsedsigs are those files there with execute permissions?

---

### Post by Sushubh on 2007-05-16
those two files does not seem to exist. need to check out shutting down to see if it works now. would be right back.

---

### Post by Sushubh on 2007-05-16
/etc/rc6.d/S20fixsedsigs does not exist.

/etc/rc0.d/S20fixsedsigs does not exist either.

---

### Post by ago on 2007-05-16
We install a package called lupin-target. Can you check whether it is installed or whether it was removed?

I'll ask Ecology to upload it on the website. Installing that should fix your issues. I am curious as of why it was removed... deborphan?

---

### Post by Sushubh on 2007-05-16
how do i check if it is installed or removed?

i just used synaptics and automatrix to install some stuff. did not remove any thing :-s

synaptics shows that the above thing is installed. it shows with a green box.

---

### Post by ago on 2007-05-16
Do you see the file /etc/init.d/fixsendsigs?

---

### Post by Sushubh on 2007-05-16
this file exists...

---

### Post by ago on 2007-05-16
Ok I think I know the reason...

---

### Post by ecology2007 on 2007-05-16
Here is the link for lupin-target :
[http://cutlersoftware.com/ubuntusetup/devel/minefield/lupin-target.deb](http://cutlersoftware.com/ubuntusetup/devel/minefield/lupin-target.deb)

---

### Post by ago on 2007-05-16
Open a terminal and cut and paste the following

```

sudo $(
update-rc.d cpkernel start 01 0 6 .
update-rc.d fixsendsigs start 10 0 6 .
update-rc.d umounthost start 32 0 6 .
update-rc.d killntfs3g start 99 0 6 .
)
#finish

```

---

### Post by goandeatsomestuff on 2007-05-17
The post you gave doesn't work, but I put them in individually and got this: 
*@ubuntu:/etc/rc6.d$ sudo update-rc.d cpkernel start 01 0 6 .
 System startup links for /etc/init.d/cpkernel already exist.
*@ubuntu:/etc/rc6.d$ sudo update-rc.d fixsendsigs start 10 0 6 .
 System startup links for /etc/init.d/fixsendsigs already exist.
*@ubuntu:/etc/rc6.d$ sudo update-rc.d umount start 32 0 6 .
**update-rc.d: /etc/init.d/umount: file does not exist**
*@ubuntu:/etc/rc6.d$ sudo update-rc.d killntfs3g start 99 0 6 .
 System startup links for /etc/init.d/killntfs3g already exist.
*@ubuntu:/etc/rc6.d$ 

I'm thinking the problem is in the bolded line?

---

### Post by ago on 2007-05-17
It's update-rc.d **umounthost** start 32 0 6 .

not umount

Anyway, it looks like you already had all the links. What problems did you experience exactly?

---

### Post by goandeatsomestuff on 2007-05-17
Okay, the umounthost is present after all, my mistake.  I'm having the same problems as the thread originator ... shutdown can't finish because of unmount errors.  I can take more pictures when I shut my machine down later today, that should help

---

### Post by Sushubh on 2007-05-17
> xxx@ubuntu:~$ update-rc.d cpkernel start 01 0 6 .
 System startup links for /etc/init.d/cpkernel already exist.
xxx@ubuntu:~$ sudo update-rc.d cpkernel start 01 0 6 .
 System startup links for /etc/init.d/cpkernel already exist.
xxx@ubuntu:~$ sudo update-rc.d fixsendsigs start 10 0 6 .
 System startup links for /etc/init.d/fixsendsigs already exist.
xxx@ubuntu:~$ sudo update-rc.d umounthost start 32 0 6 .
 System startup links for /etc/init.d/umounthost already exist.
xxx@ubuntu:~$ sudo update-rc.d killntfs3g start 99 0 6 .
 System startup links for /etc/init.d/killntfs3g already exist.


The system still does not shut down properly...

Could it be related to me turning on write permissions on the NTFS partitions? I installed something like that from automatix.

---

### Post by ago on 2007-05-17
con il comando

gedit /etc/rc0.d/S10fixsendsigs

vedi un po' di codice?

---

### Post by Sushubh on 2007-05-17
damn. i think i messed up something... 

it seems like i am not running a window manager

i cannot see any title bars... in gnome... how do  i fix this? the os is totally non functional at the moment :(

---

### Post by Sushubh on 2007-05-17
> **ago said:**
> con il comando

gedit /etc/rc0.d/S10fixsendsigs

vedi un po' di codice?

> #! /bin/sh
### BEGIN INIT INFO
# Provides:          fixsendsigs
# Required-Start:
# Required-Stop:
# Default-Start:     6
# Default-Stop:
# Short-Description: patches sendsigs preventing it from killing fuse prcesses.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin

. /lib/lsb/init-functions

do_stop () {
        /bin/sed -i 's/killall5/ps axwww \| grep -v ntfs-3g \| grep -v PID \| grep -v rc \| grep -v init \| awk "\{print \\\$1\}" \|  xargs -n1 kill/g' /etc/init.d/sendsigs
}

case "$1" in
  start)
        # No-op
        ;;
  restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
  stop)
        do_stop
        ;;
  *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac

:

this is what i see in that file...

---

### Post by Sushubh on 2007-05-17
i will try loading KDE for now...

---

### Post by Sushubh on 2007-05-17
ok GNOME failsafe worked fine. i see the titlebar and stuff... 

any ideas what could be the reason... should i stick to this session manager? i think nautilus is not loading on regular gnome session!

---

### Post by jegHegy on 2007-05-18
I had the exact same screen as in the first post when I was trying to reboot into Windows from UbuntuStudio yesterday. I have no idea what triggered the error, the OS has been working fine for me all day and then I just left it there sitting for a while before I decided to reboot. It didn't go into standby (I turned it off in the Power Management option). I could press Ctrl-Alt-Del n times in a row and it would display the splash with the progress bar going backwards and then the error in the OP n times. I had to hard-reset to get anywhere.

---

### Post by ago on 2007-05-18
There should be a program under

/etc/rc6.d/S10fixsendsigs

and

/etc/rc0.d/S10fixsendsigs

If that is missing, the reboot cannot take place properly. There was a bug that cause that links to be deleted after an update. We will post a package that will fix that. If you don't see the program above, run the commands posted earlier.

---

### Post by Sushubh on 2007-05-18
both file exist. still the problem remains!

---

### Post by ago on 2007-05-18
esegui quanto sotto e posta qui il contenuto della finestra ed eventuali errori

sudo /etc/rc0.d/S10fixsendisgs start
nano /etc/init.d/sendisgs

---

### Post by goandeatsomestuff on 2007-05-20
Here's my sendsigs, but your first sudo command pointed to something I don't have...not even anything rc0
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          sendsigs
# Required-Start:    
# Required-Stop: 
# Default-Start:     6
# Default-Stop:       
# Short-Description: Kill all remaining processes.
# Description: 
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin

. /lib/lsb/init-functions

do_stop () {
	# Kill all processes.
	log_action_begin_msg "Terminating all remaining processes"
	ps axwww | grep -v ntfs-3g | grep -v PID | grep -v rc | grep -v init | awk "{print \$1}" |  xargs -n1 kill -15
	log_action_end_msg 0
	sleep 5
	log_action_begin_msg "Sending all processes the KILL signal"
	ps axwww | grep -v ntfs-3g | grep -v PID | grep -v rc | grep -v init | awk "{print \$1}" |  xargs -n1 kill -9
	log_action_end_msg 0
}

case "$1" in
  start)
	# No-op
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	do_stop
	if which usplash_down >/dev/null; then
		usplash_down
	fi
	;;
  *)
	echo "Usage: $0 start|stop" >&2
	exit 3
	;;
esac

:
```

---

### Post by ago on 2007-05-20
my fault it's

sudo /etc/rc0.d/S10fixsendisgs start

hmmm your sendsigs looks good though

---

### Post by goandeatsomestuff on 2007-05-21
hm, I don't seem to have a rc0.d folder, or anything like it, under /etc/init.d/

---

### Post by ago on 2007-05-21
/etc/rc0.d/ 
I mistyped it (twice)

---

### Post by Sushubh on 2007-05-21
> xxx@ubuntu:~$ sudo /etc/rc0.d/S10fixsendisgs start
sudo: /etc/rc0.d/S10fixsendisgs: command not found


this is happening when i run that command :-s

---

### Post by ago on 2007-05-21
ls -al /etc/rc0.d
do you see S10fixsendsigs?

---

### Post by psayre23 on 2007-05-29
I too have this problem, and I'm not finding S10fixsendsigs in either rc6.d or rc0.d

ls doesn't show those files to exist. Is there anyplace that I may be able to get those files.

(Also, is this a problem with Wubi? Or is this something that should be addressed elseware?)

---

### Post by ago on 2007-05-30
in ubunu download [http://cutlersoftware.com/ubuntusetup/wubi/downloads/updates/lupin-target-7.04-test3.deb](http://cutlersoftware.com/ubuntusetup/wubi/downloads/updates/lupin-target-7.04-test3.deb)
then run

sudo dpkg -i lupin-target*

---

### Post by Sushubh on 2007-05-30
> (Reading database ... 126003 files and directories currently installed.)
Preparing to replace lupin-target 1.0 (using lupin-target-7.04-test3.deb) ...
Leaving `diversion of /etc/initramfs-tools/update-initramfs.conf to /etc/initramfs-tools/update-initramfs.conf.orig by lupin-target'
Leaving `diversion of /etc/initramfs-tools/initramfs.conf to /etc/initramfs-tools/initramfs.conf.orig by lupin-target'
Leaving `diversion of /etc/initramfs-tools/modules to /etc/initramfs-tools/modules.orig by lupin-target'
Unpacking replacement lupin-target ...
Removing `diversion of /etc/initramfs-tools/update-initramfs.conf to /etc/initramfs-tools/update-initramfs.conf.orig by lupin-target'
dpkg-divert: rename involves overwriting `/etc/initramfs-tools/update-initramfs.conf' with
  different file `/etc/initramfs-tools/update-initramfs.conf.orig', not allowed
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
Removing `diversion of /etc/initramfs-tools/update-initramfs.conf to /etc/initramfs-tools/update-initramfs.conf.orig by lupin-target'
dpkg-divert: rename involves overwriting `/etc/initramfs-tools/update-initramfs.conf' with
  different file `/etc/initramfs-tools/update-initramfs.conf.orig', not allowed
dpkg: error processing lupin-target-7.04-test3.deb (--install):
 subprocess new post-removal script returned error exit status 2
Leaving `diversion of /etc/initramfs-tools/update-initramfs.conf to /etc/initramfs-tools/update-initramfs.conf.orig by lupin-target'
Leaving `diversion of /etc/initramfs-tools/initramfs.conf to /etc/initramfs-tools/initramfs.conf.orig by lupin-target'
Leaving `diversion of /etc/initramfs-tools/modules to /etc/initramfs-tools/modules.orig by lupin-target'
Removing `diversion of /etc/initramfs-tools/update-initramfs.conf to /etc/initramfs-tools/update-initramfs.conf.orig by lupin-target'
dpkg-divert: rename involves overwriting `/etc/initramfs-tools/update-initramfs.conf' with
  different file `/etc/initramfs-tools/update-initramfs.conf.orig', not allowed
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 lupin-target-7.04-test3.deb


i get this when i run that command...

---

### Post by ago on 2007-05-30
we'll look into it

---

### Post by Sushubh on 2007-05-30
umm. ever since i tried installing that file... i can no longer run the update manager! how do i fix that?

---

### Post by ago on 2007-05-30
remove/purge lupin-target.deb then run it again

---

### Post by Sushubh on 2007-05-30
umm. where do i remove it from? i cant find that file using 'search for files' command... :|

---

### Post by ago on 2007-05-30
synaptic

---

### Post by Sushubh on 2007-05-30
> E: The package lupin-target needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

this is what i get when i run synaptics...

---

### Post by Sushubh on 2007-05-30
> sushubh@ubuntu:~$ sudo apt-get remove --purge lupin-target
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package lupin-target needs to be reinstalled, but I can't find an archive for it.
sushubh@ubuntu:~$ sudo aptitude remove lupin-target
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  lupin-target 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 10.2kB will be freed.
Writing extended state information... Done
dpkg: error processing lupin-target (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 lupin-target
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


this is what i get when i try to uninstall it :(

---

### Post by Sushubh on 2007-05-30
redownloaded: [http://cutlersoftware.com/ubuntusetup/devel/minefield/lupin-target.deb](http://cutlersoftware.com/ubuntusetup/devel/minefield/lupin-target.deb)

cant install it.

---

### Post by jxhndxe on 2007-05-30
FWIW, I have the exact same problem as Sushubh, but only after installing ntfs-3g through Automatrix2.  Even though I uninstalled ntfs-3g (through the Automatrix2 uninstall), I still have the same issue.

As instructed, I purged *lupin-target* through Synaptic, downloaded it from [http://cutlersoftware.com/ubuntusetu...7.04-test3.deb](http://cutlersoftware.com/ubuntusetu...7.04-test3.deb), and then installed it again.

I now don't get the same dialog on my screen when I shutdown...rather, I get a blank screen with a flashing underline.

I admit, rather reluctantly, that I'm a desktop linux newbie, and many of the other questions presented in this thread regarding the appearance or disappearance of various files went a little over my head.  I'm certain we're not the only ones struggling with the same problem, so would it be possible for somebody "in the know" to post a single set of instructions for how to debug and correct this?

I may just need to uninstall Wubi and start over again, but skip the ntfs-3g through Automatrix2, which seemed to be the cause of it all.

Thank you for your continued help in this issue.  Wubi is a wonderful product for those of us who love the idea of running Ubuntu, want more than what the Live CD can offer, but can't stomach the blood and guts of partitioning and fear the uncertainty of what may become of our Windows OS. ;)

---

### Post by minoas on 2007-06-07
After some extensive testing I noticed that the moment somone uses the NTFS-Configuration tool from the official Feisty Repository the system no longer shutdowns and gives the error we are talking about here.Managed to reproduce it to 4 machines so far.Disabling the NTFS write makes also the issue disapear.Any idea on how to make those 2 coexist?

---

### Post by Sushubh on 2007-06-07
i have a similar feeling. the first thing i have done on my three wubi install was to get the ntfs writing working and i have not been able to shut down the system properly...

---

### Post by ago on 2007-06-07
Can you try with the latest version (I know it's a bit annoying, but we need feedback since we are getting closer to release candidate) 

[http://cutlersoftware.com/ubuntusetup/minefield.html](http://cutlersoftware.com/ubuntusetup/minefield.html)

---

### Post by minoas on 2007-06-09
Tested with Wubi-7.04-minefield-184.52 since the other releases simply failed to boot at all.Still the problem remains.If we enable NTFS-Configuration and make the drivers Write Enabled we still loose the Shutdown.

---

### Post by ago on 2007-06-09
I opened a bug, that might be some "interference" from NTFS-config. I'll have a look.

---

### Post by minoas on 2007-06-09
Just a temporary solution I managed to get.What I did was install this deb OVER the existing ntfs-config and it seems to have fixed the shutdown issue.

[http://flomertens.free.fr/ntfs-config/download.html](http://flomertens.free.fr/ntfs-config/download.html)

A side effect I noticed was that it messed the loading screen on startup and I'm getting the Ubuntu Usplash at low resolution 640x480 and at around 30% it turns to all text modebut with no error report whatsoever.I also noticed no matter what change I do in my menu.lst or even uninstalling usplash-ubuntu-theme have no effect whatsoever in the boot.Only in the shutodwn menu.What is responsible for the boot logo?

Update.The Deactivating Swap [Failed] poped once again during my tests.So this fix is not 100% accurate but better than no shutdown at all :)
After turning to verbose mode I can confirm that the Deactivating Swap is still here just now the system powers right after it while previously it was stuck in a loop....

---

### Post by minoas on 2007-06-10
New Install with minefield Wubi-7.04-minefield-194.53 .Totally clean system with all the updates and I still have not applied the NTFS-config tool or installed anything extra.The system is shutting down normally but those 2 files are not here

/etc/rc6.d/S20fixsedsigs
/etc/rc0.d/S20fixsedsigs 

/etc/init.d/fixsendsigs Exists...

Is this intended,Did you change the scipts or this is the cause of the issue?Why does it break AFTER we apply the NTFS-Config ;


**UPDATE**

Latest Wubi with normal install.The NTFS config issue remains.Turning to Verbose shutdown I noticed an extra error before the ones posted in the first page.

cant't link lock file /etc/mtab~ read only file system 

I also noticed that if I create manually a mtab~ file before shutting down the system it still gives an I/O error but then shuts down.The file is then deleted on next boot....so prob have to reacreate it manually IF I want the system to close..

One also interesting discovery is for the issue to be reproduced all you have to do is write at the swap.Sessions where I keep my usuage minimal and the swap remains at 0% can shut down without issue.But getting   at 1% and more is triggering the bug...

---

### Post by Bejron on 2007-08-30
I'm having the same problem. 
Checking in and more or less just posting to get a thread subscription going with hopes for a solution to the problem.

---

### Post by Bejron on 2007-09-01
> **minoas said:**
> 
One also interesting discovery is for the issue to be reproduced all you have to do is write at the swap.Sessions where I keep my usuage minimal and the swap remains at 0% can shut down without issue.But getting   at 1% and more is triggering the bug...

A thought about this. I don't really know what the disk structure looks like but what if you disable the NTFS write support on the partition that the swap virtual disk resides on ?

I myself have several different partitions on my system and I'm not in dying need of NTFS write support on the partition where the swap is. 

All I know about activating NTFS write support is via ntfs-config and that doesn't allow to choose which partitions to mount and not.   

Anyone who can help me test this one out or can kill the idea immediately ? It's not a good temporary solution but perhaps a quick temporary "hack" to fix it..

---

### Post by TorontoStorm on 2007-11-12
I know this thread is quite old, but I'm having the same issue with 7.04, I get the exact same error as the original post in this thread, and I suspect NTFS Configuration Tool is the cause. Has this problem been solved?

---

### Post by ago on 2007-11-13
7.10 should be ok with that

---

