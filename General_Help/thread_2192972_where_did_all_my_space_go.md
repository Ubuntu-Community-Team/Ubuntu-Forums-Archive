---
title: "where did all my space go?"
date: 2013-12-10
forum: General Help
---

### Post by sjoerdmeijer33 on 2013-12-10
hello, im here with a problem thats about the harddrive space in my laptop.
all i do on here is download things, and do things for school
im out of place on the hard drive. but there is only about 8 gigs of files in the downloads folder. 
and documents dont take that much place.
so my question is, where did it go and how do i find it?
my harddrive is 200 gigs btw.
its also not in the trash

---

### Post by Impavidus on 2013-12-10
Have a look at this post: [http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
Which partition gets full? You may have more than one. Which directory consumes all your disk space?

---

### Post by sjoerdmeijer33 on 2013-12-10
i only have one, and i can't find what folder does. it almost seems like none.

---

### Post by codenine75a on 2013-12-10
use squashfs, tarballs or whatever.  Buy an external drive to store your data or store stuff online.  Use google drive.
[drive.google.com]("https://drive.google.com") They offer a free 15GB of space.  Hey use Ubuntu one.  You get 5GB there.

---

### Post by sjoerdmeijer33 on 2013-12-10
thats not what i want, i just want the problem fixed, there is nothing on my hard drive that could take so much space

---

### Post by drmrgd on 2013-12-10
A couple quick things to check:

1. What is the data usage on your file system.  From terminal:

```

df -Th

```

That will show you which partition is taking up all of the space.  It's not impossible, but a bit unusual to only have a system set up with 1 partition.  That will help narrow things down a bit.

2. I like to run this command to show me the top 10 largest files in any directory:

```

du -hsx * | sort -rh | head -10

```

Once you've narrowed down the partitions that has the most data on it, you can try running this from that partition (and any subdirectories) to get an idea of what are the largest files.  Probably /home, /var, and /etc would be the first places I would check.  You may need to prepend that with 'sudo' if you want to run it from system directories as you'll get a permission denied error.  That's usually not a problem as most times you can ignore those files anyway.

That should give you output similar to (this is on my system running from /:
```

74G     home
6.9G    usr
1.6G    var
1.5G    opt
396M    lib
60M     boot
17M     etc
8.9M    bin
8.7M    sbin
1.5M    root

```

That should help you get started.

---

### Post by r-senior on 2013-12-10
How many kernels are in the boot directory?

```
ls -l /boot/vm*
```

---

### Post by sjoerdmeijer33 on 2013-12-10
-rw------- 1 root root 5368560 mei  1  2013 /boot/vmlinuz-3.8.0-19-generic
-rw------- 1 root root 5373488 aug 22 23:26 /boot/vmlinuz-3.8.0-30-generic
-rw------- 1 root root 5372944 sep 10 22:28 /boot/vmlinuz-3.8.0-31-generic
-rw------- 1 root root 5375088 okt  2 00:08 /boot/vmlinuz-3.8.0-32-generic
-rw------- 1 root root 5375056 okt 23 19:58 /boot/vmlinuz-3.8.0-33-generic
-rw------- 1 root root 5375472 nov 12 19:34 /boot/vmlinuz-3.8.0-34-generic
thats what i get when i do [COLOR=#000000][FONT=Ubuntu Mono]ls -l /boot/vm*[/FONT][/COLOR]

---

### Post by sjoerdmeijer33 on 2013-12-10
iv'e tried but [COLOR=#000000][FONT=Ubuntu Mono] sort -rh | head -10. don't seem to work or take really long, could you tell me what one is the case?[/FONT][/COLOR]

---

### Post by drmrgd on 2013-12-10
> **sjoerdmeijer33 said:**
> iv'e tried but [COLOR=#000000][FONT=Ubuntu Mono] sort -rh | head -10. don't seem to work or take really long, could you tell me what one is the case?[/FONT][/COLOR]

Depending on where you run it from, it could possibly take a minute or so.  

Also, double check that you've typed the command in correctly.  What you posted wasn't quite what I put above, and it could be that you're missing the 'du -hsx *' part of the command (in which case the system is just sitting there waiting for input to the next command, sort).  It's best if possible to just copy and paste this into the terminal to be sure you got the syntax correct.

---

### Post by sjoerdmeijer33 on 2013-12-10
> **drmrgd said:**
> Depending on where you run it from, it could possibly take a minute or so.  

Also, double check that you've typed the command in correctly.  What you posted wasn't quite what I put above, and it could be that you're missing the 'du -hsx *' part of the command (in which case the system is just sitting there waiting for input to the next command, sort).  It's best if possible to just copy and paste this into the terminal to be sure you got the syntax correct.

i would but it seems that you can't put in [COLOR=#000000][FONT=Ubuntu Mono]|.
im new to all this so im probably just stupid.[/FONT][/COLOR]

---

### Post by drmrgd on 2013-12-10
> **sjoerdmeijer33 said:**
> i would but it seems that you can't put in [COLOR=#000000][FONT=Ubuntu Mono]|.
im new to all this so im probably just stupid.[/FONT][/COLOR]

No problem!  Depending on your keyboard layout, the pipe character '|' should be right above your enter key.  Worst case scenario, if you can't find or use a pipe character for some reason, the important bit is the 'du -hsx *' as it is what gets the files sizes.  The rest is for sorting (the next bit), and filtering to the top 10 (the last bit).

**Edit**: by the way, what was the result of df -Th?  Can you post the output using the code tags?

---

### Post by oldos2er on 2013-12-10
> **sjoerdmeijer33 said:**
> i would but it seems that you can't put in [COLOR=#000000][FONT=Ubuntu Mono]|.[/FONT][/COLOR]

Copy and paste is the easiest way to input commands from code boxes.

---

### Post by sjoerdmeijer33 on 2013-12-11
here is the outcome of  df -Th:  
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4      146G  138G  639M 100% /
none           tmpfs     4,0K     0  4,0K   0% /sys/fs/cgroup
udev           devtmpfs  487M  4,0K  487M   1% /dev
tmpfs          tmpfs      99M  852K   99M   1% /run
none           tmpfs     5,0M     0  5,0M   0% /run/lock
none           tmpfs     495M  256K  495M   1% /run/shm
none           tmpfs     100M   24K  100M   1% /run/user

---

### Post by sjoerdmeijer33 on 2013-12-11
this is the outcome from du -hsx * | sort -rh | head -10
8,9G	Downloads
1,3G	Desktop
385M	Documenten
2,4M	Pictures
1,7M	D02632D9-1555-4399-B73D-EE45D2EFDAAE.jpg
1,6M	C7F81858-B4A3-49BE-AD33-D18ACEAC8C70.jpg
1,6M	2D84197F-A9BB-4491-9943-0CF33EADCF14.jpg
1,3M	Bureaublad
648K	380711BE-7CEA-4392-87E3-819E23C076B3.jpg

---

### Post by r-senior on 2013-12-11
Well, it doesn't seem to be old kernels, because you only have five old kernels in addition to the one you are running. There is some space to be freed there but probably only 1.5G. Your home directory appears to be < 12G (unless you have thousands and thousands of small files in your home directory).

Let's try:

```
cd /
```

then 

```
sudo du -hsx * 2> /dev/null
```

That goes right to the top of your filesystem and finds the space used in each top-level directory. It's similar to what disk usage analyzer does if you run it on '/', but should be quicker because it only looks at the very top level. It needs sudo because you don't own these directories.

To give you some reference point, here is mine:

```
$ du -hsx * 2> /dev/null
9.5M	bin
61M	boot
4.0K	cdrom
4.0K	dev
86M	etc
43G	home
0	initrd.img
463M	lib
4.0K	lib64
0	libnss3.so
16K	lost+found
4.0K	media
4.0K	mnt
4.0K	net
0	proc
4.0K	root
1.2M	run
12M	sbin
4.0K	srv
0	sys
108K	tmp
5.7G	usr
1.3G	var
0	vmlinuz
```

---

### Post by sjoerdmeijer33 on 2013-12-11
this what i get 
sudo du -hsx * 2> /dev/null
[sudo] password for sjoerd: 
8,9M	bin
148M	boot
4,0K	cdrom
4,0K	dev
81M	etc
15G	home
0	initrd.img
0	initrd.img.old
775M	lib
16K	lost+found
8,0K	media
4,0K	mnt
151M	opt
0	proc
56K	root
852K	run
11M	sbin
4,0K	selinux
4,0K	srv
0	sys
616M	tmp
3,9G	usr
118G	var
0	vmlinuz
0	vmlinuz.old

---

### Post by r-senior on 2013-12-11
OK, so it's /var that's the problem. Just repeat the process above, until you find where the bulk of that 118G is used So you'd start with /var and work your way down:

```
cd /var
```

```
sudo du -hsx *
```

N.B. You don't need to redirect errors to /dev/null now. That was just to avoid errors showing up from '/'.

---

### Post by sjoerdmeijer33 on 2013-12-11
okay this is what shows up then.
4,9M	backups
249M	cache
3,8M	crash
213M	lib
4,0K	local
0	lock
118G	log
4,0K	mail
4,0K	metrics
4,0K	opt
0	run
60K	spool
12M	tmp
so how do i get into log?

---

### Post by drmrgd on 2013-12-11
There you go!  Looks like you've got some out of control log files, which suggests that something may not be working quite right and sending a lot of information to a log file.  118GB for a log file(s) is definitely not normal!  If you go into /var/log/ and run the disk usage command, you should now see which log file has grown this large.

---

### Post by sjoerdmeijer33 on 2013-12-11
okay this is what shows up then.
4,9M    backups
249M    cache
3,8M    crash
213M    lib
4,0K    local
0    lock
118G    log
4,0K    mail
4,0K    metrics
4,0K    opt
0    run
60K    spool
12M    tmp
so how do i get into log?

---

### Post by drmrgd on 2013-12-11
> **sjoerdmeijer33 said:**
> okay this is what shows up then.
4,9M    backups
249M    cache
3,8M    crash
213M    lib
4,0K    local
0    lock
118G    log
4,0K    mail
4,0K    metrics
4,0K    opt
0    run
60K    spool
12M    tmp
so how do i get into log?

It looks like you ran that command from /var, and not /var/log.  Try this:

```

sudo du -hsx /var/log/* | sort -rh | head -10

```

---

### Post by sjoerdmeijer33 on 2013-12-11
well ive found what it is .118G	uvcdynctrl-udev.log now how do i delete this?

---

### Post by r-senior on 2013-12-11
Looks like this bug:

[https://bugs.launchpad.net/ubuntu/+source/libwebcam/+bug/811604](https://bugs.launchpad.net/ubuntu/+source/libwebcam/+bug/811604)

---

### Post by sjoerdmeijer33 on 2013-12-11
how do i fix it?

---

### Post by r-senior on 2013-12-11
Based on that bug report:

```
sudo killall -9 uvcdynctrl
```
```
sudo rm /var/log/uvcdynctrl-udev.log
```

But it might come back.

I guess the longer term solution is to figure out whether you need this uvcdynctrl package, which seems to be related to libwebcam0, which seems to be something to do with developing software for web cams. Does any of that make any sense? Are you using a webcam, developing software for a webcam? Do you recall having to do anything to get a webcam working?

---

### Post by sjoerdmeijer33 on 2013-12-11
nope, but my webcam still does not work.

---

### Post by r-senior on 2013-12-11
Did you manage to free up the disk space?

With regard to the webcam, you are probably better starting another thread with webcam in the title so that people who know about webcams will read it.

---

### Post by sjoerdmeijer33 on 2013-12-11
meh, i have no interest in using webcam xD i now have space free again so im happy :)

---

### Post by r-senior on 2013-12-11
You could probably remove that uvcdynctrl package then. Check the dependencies carefully before pressing 'Y'.

```
sudo apt-get remove uvcdynctrl
```

---

### Post by sjoerdmeijer33 on 2013-12-11
i did it, i deleted  it completely :)

---

### Post by r-senior on 2013-12-11
It's probably worth rebooting to make sure it's gone. Then check in /var/log.

---

