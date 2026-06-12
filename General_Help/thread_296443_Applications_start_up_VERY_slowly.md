---
title: "Applications start up VERY slowly"
date: 2006-11-09
forum: General Help
---

### Post by NRios on 2006-11-09
Since a few weeks ago, my system has turned DOG slow.

It boots OK up to GDM, but after inputting name and password it takes two minutes to start gnome (it was just a few seconds before).

Once gnome is started, apps take FOREVER to load. As an example, a gnome-terminal takes about 20 seconds to load and, once it is loaded, it takes a further 20 seconds to load another (being loaded in RAM does not seem to help). If I launch another program from the terminal (say, midnight commander) it also takes a long time to start.

It has nothing to do with gnome or gtk or X, because launching, e.g. midnight commander from a text console takes just as long. For the same reason, it must have nothing to do with the font cache, unlike someone suggested. Switching to a previous kernel fixes nothing, and neither does creating a new user (so it does not seem to be my user's config files).

I have run "strace -r" on a few apps, to see where the time is spent, and some of the data is interesting, though I don't know how to proceed. The gnome apps stall on a read call, well into app launching. Midnight commander seems to choke specially on close() calls and gettimeofday().

I have run strace on gnome-terminal (from another gnome-terminal), gaim (from a gnome-terminal) and mc (from a text console). Then I have sorted the results on time, and found the bigger culprits.  I hope some warped but kind mind finds these dumps interesting and sets me on course! Here is what i've found:

**_From text console, "strace -r -o str.txt mc"_**
Total time to startup: 60.56 seconds
Number of calls:1211
Calls lasting more than 1s: 19, adding up to 60.00 seconds.

CALL#   TIME    CALL
-----   ----    --------------------------------------------
1099	29,37	rt_sigaction(SIGINT, {SIG_IGN}, NULL, 8) = 0
1118	10,08	rt_sigaction(SIGINT, {SIG_IGN}, NULL, 8) = 0
327	5,01	close(3)                  = 0
426	5,00	close(3)                  = 0
567	5,00	close(3)                  = 0
509	5,00	close(3)                  = 0
455	5,00	close(3)                  = 0
538	5,00	close(3)                  = 0
323	5,00	gettimeofday({1163091672, 18474}, NULL) = 0
563	2,93	gettimeofday({1163091722, 41521}, NULL) = 0
451	2,92	gettimeofday({1163091692, 31926}, NULL) = 0
534	2,88	gettimeofday({1163091712, 37241}, NULL) = 0
505	2,88	gettimeofday({1163091702, 36352}, NULL) = 0
422	2,87	gettimeofday({1163091682, 31034}, NULL) = 0
418	2,12	ioctl(3, FIONREAD, [40])  = 0
501	2,12	ioctl(3, FIONREAD, [40])  = 0
530	2,11	ioctl(3, FIONREAD, [40])  = 0
447	2,08	ioctl(3, FIONREAD, [40])  = 0
559	2,07	ioctl(3, FIONREAD, [40])  = 0

_**From gnome-terminal "strace -r -o str.txt gnome-terminal"**_
Total time to startup: 20.41 seconds
Number of calls: 1433
# calls taking > 1s: 1, taking up **20 SECONDS**
# calls taking < 1s, > 10ms: 10, taking up 240 ms
The other 1408 calls take up 170 ms altogether.

CALL#   TIME    CALL
-----   ----    --------------------------------------------
1273	20,00	read(10, "%\0\0\000105aa0e8f1000116309234500000"..., 48) = 48
1419	0,09	writev(16, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
1424	0,03	close(15)                 = 0
1420	0,02	close(16)                 = 0
556	0,02	mprotect(0xb7666000, 8192, PROT_READ) = 0
1425	0,02	writev(13, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
1423	0,02	writev(15, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
1421	0,01	writev(14, [{"GIOP\1\2\1\5\0\0\0\0", 12}], 1) = 12
557	0,01	munmap(0xb7f46000, 46735) = 0
1422	0,01	close(14)                 = 0
1428	0,01	close(11)                 = 0

**_From gnome-terminal, "strace -r -o str.txt gaim"_**
Total time to start up: 30.98 seconds
Number of calls: 8652
# calls lasting > 1s: 1, lasting **20 SECONDS**
# calls lasting > 10ms and < 1s: 19, taking up 5.28 seconds
# calls lasting > 1ms and < 10ms: 22, taking up 4.22 seconds
# calls lasting < 1ms: 8400 aprox, taking up 1.5 seconds.

Here are the calls lasting more than 10ms:

CALL#   TIME    CALL
-----   ----    --------------------------------------------
3730	20,00	read(12, "%\0\0\000105aa0e8f1000116309944500000"..., 48) = 48
8278	0,73	gettimeofday({1163099449, 32485}, NULL) = 0
8374	0,51	gettimeofday({1163099451, 148610}, NULL) = 0
8488	0,49	gettimeofday({1163099452, 312680}, NULL) = 0
8302	0,45	ioctl(3, FIONREAD, [64])  = 0
8290	0,40	gettimeofday({1163099449, 432455}, NULL) = 0
1820	0,37	fstat64(12, {st_mode=S_IFREG|0644, st_size=36432, ...}) = 0
8509	0,33	ioctl(3, FIONREAD, [96])  = 0
8340	0,30	gettimeofday({1163099450, 238806}, NULL) = 0
8381	0,24	ioctl(3, FIONREAD, [96])  = 0
1212	0,20	access("/etc/selinux/", F_OK) = -1 ENOENT (No such file or directory)
8349	0,19	ioctl(3, FIONREAD, [64])  = 0
7081	0,19	gettimeofday({1163099446, 595911}, NULL) = 0
7118	0,18	gettimeofday({1163099447, 152688}, NULL) = 0
8464	0,15	ioctl(3, FIONREAD, [64])  = 0
7055	0,14	gettimeofday({1163099446, 407566}, NULL) = 0
7108	0,11	gettimeofday({1163099446, 975837}, NULL) = 0
8365	0,11	gettimeofday({1163099450, 640468}, NULL) = 0
7102	0,11	gettimeofday({1163099446, 862278}, NULL) = 0
365	0,10	open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)

---

### Post by Vitriolic on 2006-11-26
I also have a problem with slow application launch.  It began (I think) when I was fiddling with network settings trying to get my new broadband connection working. Seems there was a problem with D-Link routers not playing nice with Ubuntu's IPV6 support:

[http://www.ubuntuforums.org/archive/index.php/t-78337.html](http://www.ubuntuforums.org/archive/index.php/t-78337.html)

I now have internet access, but there's still a big delay launching applications.  If anyone knows what I've messed up or has a theory, please let me know :)

Otherwise, I'll try strace like NRios did, and report the results back.

---

### Post by Vitriolic on 2006-11-27
strace also reports on my system that one of the calls to read is taking a long time to return (10s or so.) The second, quoted, parameter starts with a %. The other read calls were fast.

Any ideas what this read call is reading? Might it be network related or is it filesystem?

Cheers,
Vit

---

### Post by het.idee on 2006-11-28
I have the same thing. Ever since i got my wireless connection working, everything starts buttslow. The problem seems to fix itself as soon as i get my internetconnection up...

---

### Post by mpop on 2007-01-01
> **Vitriolic said:**
> strace also reports on my system that one of the calls to read is taking a long time to return (10s or so.)

Same thing here.

Half of my applications start (CPU usage at 100% for 1-3s), then just stop and seem to be waiting for something for 20s, then continue and finally launch.

Since Nautilus and Gnome-terminal have this problem too, it makes my gnome desktop barely usable (Gnome takes 1'00-1'30 to start, compared to a few seconds before this problem started).

I've spotted a similar line as well :
```
3730 20,00 read(12, "%\0\0\000105aa0e8f1000116309944500000"..., 48 ) = 48
```
But mine was "just" 10s.

](*,)

---

### Post by laidback on 2007-01-01
A later thread mentions problem with ipv6 and suggest that it should be disabled in Firefox and elsewhere. Apparently a search for ipv6 yields the other threads. I doubt that this solves all your problems but it might erase one or two possibilities.

Laidback

---

### Post by 2CV67 on 2007-01-02
See last post here - it sounds like same problem to me.

[http://www.ubuntuforums.org/showthread.php?t=323151](http://www.ubuntuforums.org/showthread.php?t=323151)

Don't ask me for explanation though...

---

### Post by mpop on 2007-01-02
> **2CV67 said:**
> See last post here - it sounds like same problem to me.

[http://www.ubuntuforums.org/showthread.php?t=323151](http://www.ubuntuforums.org/showthread.php?t=323151)

Don't ask me for explanation though...

THANKS !

I've just tried to start my system with no internet connection at all, and applications now start just as fast/normal as they should, with no 20s delay. Note 1: it's painfully hard to *really* stop an internet connection. I had to unplug my ethernet cable AND reboot. Note 2: right now i've plugged it again, so I have an internet connection, but I haven't witnessed the dreaded delay coming back. I expect it to come back sooner or later, for example next time I reboot.

Now, on fixing this on a long-term basis:

I can't apply your solution, because it seems that *my system has no name/hostname whatsoever*. My /etc/hostname configuration file is empty (it exists, but it simply is empty), and my /etc/hosts configuration file is empty as well (well, not totally empty, but it only contains the "The following lines are desirable for IPv6 capable hosts" comment, with nothing else).

So next thing I need to do, if I am to apply your solution, is to find a way to give a hostname to my machine. Don't know if I can do this just by adding one to /etc/hostname. Any tips on this matter would be greatly appreciated. :)

Well, thanks anyway for pointing that out. Phew, to think that it was a network configuration issue... Aren't those supposed to affect *networking* ? :roll:

---

### Post by mpop on 2007-01-02
Wow, that's strange. I've just rebooted once more, this time with the ethernet cable plugged in, and there seems to be no problem at all. Even with the Internet connection. :confused:
*Edit :* ok, the bug is back, so it really seems to be about the network config. I'll have to fix that tomorrow.

---

### Post by pjbgravely on 2007-01-02
I had the same type of problems. The fix was to make sure nothing is funky in /etc/hostname, and /etc/hosts which I found there was. It happened all of a sudden and fixing those files fixed everything.

/etc/hostname only has one word in it, the name of your computer.

/etc/hosts only needs to have one line in it to work.

127.0.0.1 localhost host_name

Host_name has to be the same name found in /etc/hostname.

Put a # in front of all other lines.


Also in /etc/network/interfaces if these lines are not found you computer can act the same.

# The loopback network interface
auto lo
iface lo inet loopback


Paul

---

### Post by mpop on 2007-01-03
Paul >
Thanks for the tips. I've tried what you did, and it seems to work fine. I'll have to confirm it because recently there were times when everything worked fine for a while, then got messy again. Now it seems I've fixed my networking configuration, so it should be fine.

Here is what I did :
1) /etc/hostname was empty so I edited it to add an hostname (I chose "mpopland").

2) /etc/hosts was empty as well so I wrote one that looks that way:
```
127.0.0.1 localhost mpopland
```
Note: I've read documentation saying that it should be the host/domain name first, then the alias. In my case: "mpopland localhost", but it seems that both work ok.


[quote="Paul"]Also in /etc/network/interfaces if these lines are not found you computer can act the same.

# The loopback network interface
auto lo
iface lo inet loopback[/quote]
I had these lines (except for the comment), so I didn't change anything in my /etc/network/interfaces

I'll write in a few hours/days to say whether the problems are gone for good or not.

*Edit :* everything has worked fine since then. Problem solved.

---

### Post by crapapelada on 2007-03-05
I had the same problem and found a couple of threads here with no solutions yet.
I just found this, tried and looks like it works fine!!!
I had some doubts about this solution because I had always the problem, regardless being connected to the network or not.
Anyway, thank you very much for solving this!

:guitar:

---

### Post by Quasaur on 2007-03-31
my hostname is vistaclm
in my /etc/hosts file...in addition to:

127.0.0.1 localhost

i have the following:

127.0.1.1 vistaclm.subdom.nj.isp.net

shouldn't this be 127.0.0.1??

---

### Post by pjbgravely on 2007-03-31
> **Quasaur said:**
> my hostname is vistaclm
in my /etc/hosts file...in addition to:

127.0.0.1 localhost

That line should be 127.0.0.1 localhost vistaclm


> **Quasaur said:**
> 
i have the following:

127.0.1.1 vistaclm.subdom.nj.isp.net

shouldn't this be 127.0.0.1??

No,127.0.0.1  is  correct, but the line should read :
127.0.1.1 vistaclm.subdom.nj.isp.net vistaclm

Paul

---

