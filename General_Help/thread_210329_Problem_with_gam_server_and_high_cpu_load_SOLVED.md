---
title: "Problem with gam_server and high cpu load SOLVED"
date: 2006-07-06
forum: General Help
---

### Post by konstk on 2006-07-06
Here is a solution that works.

There is a file called "gaminrc" in the "gamin" folder in the "etc" directory which controls how often the gam_server asks the system about changed files.

You have to edit that file as a superuser.

1. Press "Alt" + "F2" to get the "run Application" dialog.

2. In the box type the following (without the quotes) : 
"gksu gedit /etc/gamin/gaminrc"
 (You will have to type in your administrative password when it asks you)

3. You will need to know what filesystems you are using.
For each filesystem type the following in a separate line replacing <filesystem> with the filesystem you are using:

fsset <filesystem> poll 10

4. Save the file

For example, if you are using the ext3 filesystem you would type the following:

fsset ext3 poll 10

What this does is tell gam_server look for changed files every 10 seconds instead of a gazillion times a second like it was doing.

You can try a different interval other than 10 seconds to see what works best for you.

Good luck.

- Konstantin

---

### Post by kebes on 2006-08-16
I was having the same problem: the gamin daemon, gam_server, which is supposed to monitor file system changes, was using an absurd amount of CPU time (60-99% all the time). This caused noticeable slow-down of my modest hardware.

The above solution works perfectly on Kubuntu 6.06 (Dapper Drake). Just add a line like "fsset ext3 poll 20" to "/etc/gamin/gaminrc" and the problem is solved. No functionality is lost (gam_server still runs), but the computer is now back to being fast and smooth.

Thanks so much for posting this solution!

---

### Post by julipanno on 2006-08-25
Great solution... 

ahh.. the smoothness of it.. :-)

---

### Post by Markor on 2007-10-08
This fix does not work for me. 

I set fsset ext3 poll 50
and one line for every other fs. I use.

I use 64-bit Xubuntu 7.04 fiesty and dual-core 2Ghz amd cpu and I have 80% usage on 
every core.  (Every time I start Thunar, gam_server goes crazy):confused:
Gamin version on 7.04 is 0.1.8-1 ubuntu3 And I cant update it beacouse of 
dependencies.

---

### Post by 4ebees on 2007-10-11
Matey,

Solved it like a dream (6.06 box).

Thank you very much :))

---

### Post by Markor on 2007-11-08
Also does NOT solve problem on Xubuntu 7.10 64-bit.

---

### Post by DaveM753 on 2007-11-11
I'm running a few boxes with Ubuntu 7.04 and one with 7.10.  gam_server is a major problem on two of the boxes.  The 7.10 box (a laptop) was seeing gam_server average about 40% CPU at all times.

After several rounds of trying various manual entries in gaminrc, I came across some interesting things:

The laptop mounts two cifs shares on different servers.  I took note that if I umounted the one called  /media/linuxtempfolder, gam_server would settle down immediately (to 0% CPU).  The share to the other server was still mounted.  Each time I would remount /media/linuxtempfolder, gam_server would kick back up to ~40%.

On further investigation, I found that my laptop's trashbin had 5700+ files in it, the vast majority of which were from /media/linuxtempfolder.  I emptied the trash.  gam_server settled back to near 0%.  I took out all of the manual gaminrc entries I had made, rebooted the laptop and gam_server is still running near 0%.

In short, try emptying your trash and see if that helps.

I also noted that using nautilus to view a cifs-mounted folder containing a large number of files will cause gam_server to kick up to about 7%.

---

### Post by doncristobal on 2008-02-03
> fsset <filesystem> poll 10

I had the same same problem, and this seems to have fixed it quite much. With me, Thunar was the program that used to make the gam-server go crazy. Thanks for the instruction. 
I have Xubuntu 7.10.

Edit: Sorry, it does not really solve the problem. One Thunar window is fine now. But as soon as I open a second one, the cpu load keeps bumping up and down between 10 and 90% once a second. A third Thunar window, and cpu is at 100%, harddisk going crazy. Even closing the 3 windows does not help now... cpu and harddisk are still 100% busy. Interesting detail: top says that most (~75%) of the cpu load is of the kind "wa", according to the man page: "Amount of time the CPU has been waiting for I/O to complete."
After some minutes the horror ends, but relaunching more than one Thunar window blocks the computer again. 
:-(
"killall thunar" / "killall Thunar" makes cpu and hd shut up immediately, whereas closing Thunar the normal way (alt-f4 e.g.) does not help. (Don't ask me why Thunar is once thunar and once Thunar...)

---

### Post by linux phreak on 2008-02-27
The problem with thunar is driving me crazy.Is there any solution?I switched to xubuntu feeling that it was quick.But it is not.

---

### Post by malloq on 2008-02-29
Are you using NFS? On my 64-bit Ubuntu 7.10 I started having problems after having configured use of NFS shares. I've tried to unmount them all now to see if the system becomes more stable. I've seen excessive CPU load, and gam_server crashes.

From the "News" on [http://www.gnome.org/~veillard/gamin/news.html](http://www.gnome.org/~veillard/gamin/news.html) :

> Bug fixes: enable polling when using inotify this fixes support for NFS partitions (Alexander Larsson), do not run idle handler if not needed reduce wakeups (Alexander Larsson), handling of failure of inotify initialization (Robert Clark), force poll support if compiled without inotify and dnotify (Ray Strode)

Seems there might be some trouble with NFS shares on the 0.1.8-version in Ubuntu. Would it be possible to try the hardy-package (which i version 0.1.9)?

---

### Post by sengines on 2008-06-20
> **malloq said:**
> Are you using NFS? On my 64-bit Ubuntu 7.10 I started having problems after having configured use of NFS shares. I've tried to unmount them all now to see if the system becomes more stable. I've seen excessive CPU load, and gam_server crashes.

From the "News" on [http://www.gnome.org/~veillard/gamin/news.html](http://www.gnome.org/~veillard/gamin/news.html) :



Seems there might be some trouble with NFS shares on the 0.1.8-version in Ubuntu. Would it be possible to try the hardy-package (which i version 0.1.9)?

The culprit is xubuntu (thunar), I had to post because I am getting the same errors over and over again killing my productivity and have found no answers although I've tried implementing a few fixes, nothing stuck permanently. 

I am using xubuntu hardy 64 bit and there are multiple instances of thunar started, also it may have to do something with gam_server. It also freezes faster when you are viewing hidden files and open up multiple windows

This has already been reported but there are no similar upstream bug reports [https://bugs.launchpad.net/thunar/+bug/163587](https://bugs.launchpad.net/thunar/+bug/163587) if anyone knows a permanent fix for this please post asap because xubuntu is all I can use without having my computer give those pesky black screens that ubuntu gives me all the type.

[http://bugzilla.xfce.org/show_bug.cgi?id=2502](http://bugzilla.xfce.org/show_bug.cgi?id=2502)

---

### Post by ICU2 on 2008-07-11
This really helped me with thunar being slow accesing ntfs partitions, thank you very very much. using ubuntu(unflavored) or flavoured my style.

---

