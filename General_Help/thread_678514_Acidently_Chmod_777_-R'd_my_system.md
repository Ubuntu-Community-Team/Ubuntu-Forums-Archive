---
title: "Acidently Chmod 777 -R'd my system"
date: 2008-01-25
forum: General Help
---

### Post by JeremyTheGeek on 2008-01-25
Ok heres what happened...

Dolphin (KDE) stoped saving my bookmarks. I fixed the problem by following the instructions at 
[http://www.linuxforums.org/forum/ubuntu-help/108515-unable-save-bookmarks-dolphin.html]("http://www.linuxforums.org/forum/ubuntu-help/108515-unable-save-bookmarks-dolphin.html")

I opened up Konsole and typed 
```
cd /home/jeremy/.kde/share/apps/d3lphin/
```
from ther I typed 
```
sudo chmod 777 -R /
```
Being new to the command line i thought that this would change the permissions of all the files in the current direectory. When tons of text started to fly by i knew something was wrong so i shut it down 5-7 seconds in. It didnt complete the job so I typed this into konole and let it go for 8 seconds
[HTML]sudo chmod 755 -R /[/HTML] 
Is there any way to fix this??

FYI: I cant do a complete reinstall

Plz help me
- Germ

---

### Post by dcstar on 2008-01-26
> **JeremyTheGeek said:**
> 
..........
```
sudo chmod 755 -R** /**
``` 
Is there any way to fix this??

FYI: I cant do a complete reinstall

Plz help me
- Germ

Since you have changed the permissions of the WHOLE root filesystem, I seriously doubt it.

Learn your lesson, copy off any data and reinstall the system.

---

### Post by JeremyTheGeek on 2008-01-26
OK thanks but now theres a new problem....

1) How can I back up all of my programs (or just make one giant apt-get line)? Would there be a script for it?

2) Can someone explain to me how to make a seperate partition for the /home directory (or point me to a place that can)?

3) I have a 40 GB HD how much space should I throw to each partition (/var, /usr, /tmp, /home, /boot)? 

4) How can I avoid doing anything stupid on the commandline ever again / prevent this from happining again?

Your help is appriciated

-Germ

---

### Post by taurus on 2008-01-26
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

p.s.  Stop using _sudo_ especially changing ownership and/or permissions if you don't know what you are doing.  That is one sure way to screw up your system fast.

---

### Post by JeremyTheGeek on 2008-01-26
Thanks for the advice tarus I'll be sure to be super carefull when using the sudo command.

now does anyone know the answers to 1,2 and 3?

P.S. Is your first name B'Elanna and do you watch Star Trek Voyager?

---

### Post by taurus on 2008-01-26
1.  Are those personally programs that you installed?  If you installed them through synaptic, Add/Remove, apt-get/aptitude, then just install them again after you reinstall your system.

2.  The link that I've provided shows you how to do that.

3.  You don't really need separate partitions for /var, /usr, /tmp, /boot.  However, there is nothing wrong having them on separate partitions.  It's a good idea to have /home on it own partition though.

> P.S. Is your first name B'Elanna and do you watch Star Trek Voyager?
Have no idea who that character is.  Does that answer your question whether I watch Star Trek Voyager?  ;)

---

### Post by JeremyTheGeek on 2008-01-26
Thank you for all the help Tarus and Dcstar,:KS:KS:KS

Just 2 more questions...

1) How much space should I devote to /home? I have about 5 (8.2 total on HD according to filelight) gigs of data (in my home) and a 5 GB backup partition on a 40 GB HD.

How do you think this sceme would work?

1) ext3 /home 15 GB
2) ext3 / 15 GB
3) swap 512 MB
4) ext3 backup (whatever I have left)

2) is there a way to get kubuntu to only install the base system? By using "sudo apt-get install kubuntu-desktop from the command line it install faster.


Im going to back-up and reinstall today.:):):)
P.S. Sry about asking #2 twice, I cant count:lolflag:

---

### Post by danwood76 on 2008-01-26
I would set aside 10GB for / swap should be twice the size of your RAM the rest allocated to your /home

why do you need a seperate backup partition?

regards,
Danny

---

### Post by JeremyTheGeek on 2008-01-26
Thank you for your help all of you, I've learned a valuable lesson...

[SIZE="7"]DONT MESS WIOTH SUDO!!!![/SIZE]

Im backing up right now and will be installing in 10 min.

Thank you all for helping me through this, Power to the community!!
:guitar::guitar::guitar::guitar::guitar:

P.S. About the partition, you raise a good question. If my HD fails there goes my data, ill thow ll of the space from my backup to my home partition. Ill use my old sansa c140 for backup.

P.P.S. Can a mod lock this??

And last of all

[FONT="Impact"][SIZE="7"]THANK YOU!!!!!![/SIZE][/FONT]

---

### Post by JeremyTheGeek on 2008-01-26
Hi again! 

Just thought id let everyone know that the operation worked!

Thank you all!!

---

### Post by fyo on 2008-01-26
> **JeremyTheGeek said:**
> OK thanks but now theres a new problem....
1) How can I back up all of my programs (or just make one giant apt-get line)? Would there be a script for it?


For future reference, you can get a list of installed packages using:

```
$ dpkg --get-selections
```

This will list your packages and their status (either "install" or "deinstall"). An example would be:

```
$ dpkg --get-selections | grep ffmpeg
ffmpeg                                          install
gstreamer0.10-ffmpeg                            install
gstreamer0.8-ffmpeg                             deinstall
libxine1-ffmpeg                                 install
```

If you're feeling a bit more advanced, you could pipe the output to a file (e.g. "installed-packages.list") and use that file to install (deinstall) from after a reinstallation of Ubuntu:

```
$ dpkg --get-selections > installed-packages.list
$ sudo dpkg --set-selections < installed-packages.list
```

This will only set the selections, as the name implies. You can finish the job by running a package manager of your choice and "applying" the changes. "dselect" is one such command line tool. Synaptic should work just fine as well.

If you've installed packages from various sources, you'll need to install the package "apt-show-versions" to get the required information. For example, say you added the medibuntu repository to get an updated ffmpeg package, that's not something you can tell from the list above. However, with apt-show-versions, you can:

```
$ apt-show-versions | grep ffmpeg
gstreamer0.10-ffmpeg/gutsy uptodate 0.10.2-2ubuntu1
libxine1-ffmpeg/gutsy uptodate 1.1.7-1ubuntu1
ffmpeg/gutsy uptodate 3:0.cvs20070307-5ubuntu4+medibuntu3
```

Best of luck ;-)

---

