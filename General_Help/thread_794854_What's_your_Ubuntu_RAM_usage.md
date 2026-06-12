---
title: "What's your Ubuntu RAM usage?"
date: 2008-05-15
forum: General Help
---

### Post by PRGUY85 on 2008-05-15
Hey:

I have noticed my new Hardy Heron 64bit install is using quite a bit of RAM compared to past versions of Ubuntu.  Right now, with Banshee beta, Transmission, Firefox and Pidgin open, it is using about 646 MB RAM...for me that is an amount I get out of Windows XP.

Is this happening to everybody? Is it something that can be fixed?

---

### Post by HunterThomson on 2008-05-15
7.10 64bt with VLC player video, Deluge bittorrent downloading 150KBs for 5 files, and Fire Fox running.

---

### Post by sloggerkhan on 2008-05-15
Don't know. I tend to use about 600 mb with lots of stuff open.

---

### Post by PRGUY85 on 2008-05-15
I don't know maybe I'm RAM tacky....yet on startup its using 300 MB RAM (or less).  After opening several programs, using them and then closing them I'm close to 600mb RAM.  That is double the quantity even if I close all the RAM extensive programs (Firefox, Banshee) as well as others (Transmission)...

Again, I thought Ubuntu used to use less resources.

---

### Post by jocko on 2008-05-15
That's perfectly normal, it's the way linux handles memory.
When you close a program it stays loaded in ram in case it gets needed again, if something else needs ram, unused programs and files gets unloaded to leave room.
That means if you leave your computer turned on for a long time ram will eventually be almost completely full.
I have 1.5 Gb of ram, and top reports that I have only about 43 Mb free.
Still my system runs very smoothly without any problem.
If you have ram it's better to use it than to keep it empty...

---

### Post by igfud on 2008-05-15
Running Firefox with several tabs (including Gmail) I use about 360MB RAM.  Even with several apps open I rarely see the majority of my 1GB used.

---

### Post by agim on 2008-05-15
My ram use is *much* lower. I have disabled a few apps, including compiz, so on startup I use about 180mb of ram. I never, ever get above 500mb, unless i am using google earth.

Even before tweaking, I used only 220mb on startup, and the 500mb rule still applied.

And the ram is relinquished when I close a program.

---

### Post by FakeOutdoorsman on 2008-05-15
```
[frink@hedron ~]$ top
Mem:   2074256k total,   313232k used,  1761024k free,    21532k buffers
```Openbox, pypanel, firefox 2, cplay, tor, apache, mysql, medit.  This was shortly after a reboot, however.

---

### Post by PRGUY85 on 2008-05-15
Still based on the System Resources Activities (Viewing ALL Activities), the amount of processes opened and using RAM does not add up to 500-600 MB RAM being Xorg the most using with 60.

---

### Post by Wandering on 2008-05-15
I typically use less than 600K even after running all day, but depending on operations, Ubuntu will use up to 100 percent of my 3GB with the remainder being used as a cache. You usage may be including cache. When I boot, it uses less than 300K and no cache, and it grows from there. It seems to manage the memory well, and I have never run out, and I have never seen the swap file in use. (3GB)  

Judging by the way many programs open much faster the second time, I presume Ubuntu is retaining the memory image of them for some time in just such an instance.

Good luck.

---

### Post by songshu on 2008-05-15
free -m can give you a good indication, 
the first line of **used** show all memory being used, including that what is not actively used at the moment but there "just in case", almost everything is used with hardly any swap so that is very good.
the second line under **used** is what is actually being used by running programs.

```
host:~# free -m
             total       **used**       free     shared    buffers     cached
Mem:          7988       7774        213          0       1822       1795
-/+ buffers/cache:       4155       3832
Swap:          956          2        954
```

don't know any percentages but 64bit also uses more RAM then 32bit, its one of the reasons that it can be slightly faster.

---

### Post by fs3rp4 on 2008-05-15
total       used       free     shared    buffers     cached
Mem:       1164452     610116     554336          0      19404     338528
-/+ buffers/cache:     252184     912268
Swap:            0          0          0

---

### Post by eriqjaffe on 2008-05-15
[IMG]http://img367.imageshack.us/img367/685/20080511160503scrotko3.png[/IMG]

---

### Post by PRGUY85 on 2008-05-15
Wow eriq, how you get it that low.

---

### Post by jimv on 2008-05-15
> **Wandering said:**
> I typically use less than 600K even after running all day, but depending on operations, Ubuntu will use up to 100 percent of my 3GB with the remainder being used as a cache. You usage may be including cache. When I boot, it uses less than 300K and no cache, and it grows from there. It seems to manage the memory well, and I have never run out, and I have never seen the swap file in use. (3GB)  

Judging by the way many programs open much faster the second time, I presume Ubuntu is retaining the memory image of them for some time in just such an instance.

Good luck.

300 KB, eh?

---

### Post by jimv on 2008-05-15
> **PRGUY85 said:**
> Wow eriq, how you get it that low.

He's not using Gnome or KDE.  There was time when computers had great GUIs and didn't need hundreds or thousands of megabytes of RAM to run.

---

### Post by Thirtysixway on 2008-05-15
With firefox, pidgin, compiz, and awn open I'm using about 318 MB of my 512 MB i have installed.



On my Ubuntu server [apache, mysql, proftpd, openssh, fail2ban, noip, and some other stuff] I get
Real memory: 501.93 MB total, 154.88 MB used
Virtual memory: 1.43 GB total, 224 kB used

---

### Post by jimv on 2008-05-15
Lets see, I've got Firefox with a bunch of tabs open, Thunderbird open, a terminal open, and a bunch of applets open on my panel...and music playing.  I'm using 430mb/1900mb on my laptop.

My apache/mysql/openssh/gnump3d/samba/dns server is using 130mb/375mb

---

### Post by PRGUY85 on 2008-05-15
Then what am I doing wrong to get 500mb with nothing open.

Also,Thirtysixway...what's that theme you are using?

---

### Post by housam on 2008-05-15
it is normal to have that size of ram usage as mine

---

### Post by eriqjaffe on 2008-05-15
> **jimv said:**
> There was time when computers had great GUIs and didn't need hundreds or thousands of megabytes of RAM to run.There still is, apparently.  ;)

I'm running Openbox on top of a command-line install.  This old (still has the "Designed for Windows 98" sticker on it) system started out with Feisty and has gone through two upgrade cycles and still runs like a champ.

---

### Post by TenPlus1 on 2008-05-15
Booting straight into my Ubuntu desktop my memory sits at 83mb used and can go as high as 290mb when I run my music, movies, opera etc.  (I have 768mb total)...

---

### Post by PRGUY85 on 2008-05-15
Again what am I doing wrong then?

Sure I got the 64bit kernel but 100mb RAM to 400mb RAM is a big difference.

---

### Post by songshu on 2008-05-15
> **PRGUY85 said:**
> Again what am I doing wrong then?

Sure I got the 64bit kernel but 100mb RAM to 400mb RAM is a big difference.

whats does your ```
free -m
``` say?

---

### Post by Fenris_rising on 2008-05-15
heres mine. dont know if its good bad or indifferent. firefox is open. deluge is running. system monitor and cpu temp.

fenris@lair:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        996         13          0        232        438
-/+ buffers/cache:        325        685
Swap:         2957         36       2920
fenris@lair:~$

---

### Post by PRGUY85 on 2008-05-15
OK here is mine with Banshee Beta and Firefox running:

             total       used       free     shared    buffers     cached
Mem:          2013        832       1181          0         18        396
-/+ buffers/cache:        416       1597
Swap:          996          0        996

---

### Post by songshu on 2008-05-15
> **Fenris_rising said:**
> heres mine. dont know if its good bad or indifferent. firefox is open. deluge is running. system monitor and cpu temp.

fenris@lair:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1010        996         13          0        232        438
-/+ buffers/cache:        325        685
Swap:         2957         36       2920
fenris@lair:~$

looks pretty good,

you have 1000MB total
all of it is being used in cache . with just 36MB swap
325 is for the programs that you are running
leaves you with 675MB that can be used any minute you would need it.

---

### Post by songshu on 2008-05-15
> **PRGUY85 said:**
> OK here is mine with Banshee Beta and Firefox running:

             total       used       free     shared    buffers     cached
Mem:          2013        832       1181          0         18        396
-/+ buffers/cache:        416       1597
Swap:          996          0        996

same for you, looks like perfectly well used ram and you have plenty to spare since you are only using 416MB actively out of the 2000MB....

the differences (300 MB - 400 MB) can also depend on things like hardware, for example some graphical cards have there own RAM build in and some snoop it from the rest of the system, same applies to raid controllers and such as well.
DDR2 and DDR3 can make a difference etc.......

with these amounts of RAM you can run much heavier software, but you could make it lighter by choosing a different desktop and applications, also Ubuntu itself is not especially geared for low-end machines, they choose comfort instead and that simply takes some RAM.

---

### Post by NightwishFan on 2008-05-15
Kubuntu Hardy AMD64 running Amarok, Ktorrent, Kopete, Konqueror with about 20 tabs, and gimp.

```
free -m
             total       used       free     shared    buffers     cached
Mem:           877        847         30          0         34        358
-/+ buffers/cache:        454        423
Swap:         2572        112       2460
```

---

### Post by PRGUY85 on 2008-05-19
The new Pidgin (2.4.2) uses 40-50mb RAM :S

---

### Post by PRGUY85 on 2008-05-19
Also, Firefox spikes to 140-150 MB with just one tab and just Adblock enabled.

---

### Post by atomkarinca on 2008-05-19
Mine starts with 108mb and never exceeds 300.

---

### Post by PRGUY85 on 2008-05-19
I believe using the x86 64-bit kernel is making me have double the amount of active RAM usage.  I had always installed the 32-bit version and was used to 300mb RAM total.
Don't know if there's anything there in the 64-bit version that is noticeable enough to warrant double the amount of memory usage.

---

### Post by fjgaude on 2008-05-19
It is standard in Unix and Linux systems for the OS to use up all the available RAM as programs are opened and keep those items in memory for future use, without having to go to the hard drive. I am usually using all my 4GB of RAM and the system is quick, because everything is in cache. That's the way both 32-bit and 64-bit Ubuntu works.

---

### Post by PRGUY85 on 2008-05-20
Another rant on my RAM findings...sorry hehe just trying to make Ubuntu the leanest I can using Gnome.  

Gnome Panel uses 30 MB RAM...I can accept that from some program but from the panel?  Is it because of the Clock Applet?

---

### Post by hellomoto on 2008-05-20
i made a note of the RAM useage on my PC when I did a clean install of hardy...

with nothing loaded apart from the  OS I use: 172.5 MB

:)

---

### Post by PRGUY85 on 2008-05-20
I may be complaining because I was used to the 32-bit Distros and now I finally installed a 64-bit one that uses more RAM.

Its just that was one of the good things about using Ubuntu, have everything running on 300 mb RAM...now it uses 500 with firefox, banshee, etc.

---

### Post by PRGUY85 on 2008-05-20
Is using the 64-bit Kernel really worth it if I have a 64-bit capable CPU?  I know the 64-bit kernel brings compatibility issues with some programs at times.  Is there any noticeable advantage?

---

### Post by chewit on 2008-05-20
Xubuntu, Pidgin, OO.org quick starter, FF3 = 140mb RAM used!

Just the OS loaded = 50mb!

---

### Post by PRGUY85 on 2008-05-20
Nice, XFCE is known for its low resource usage.

---

### Post by misfitpierce on 2008-05-25
Im usually never over 500MB with a ton of stuff open such as Opera, rhythmbox, Screem, Kompozer, Pidgin and some other junk...

---

### Post by Ameneon on 2008-05-25
800mb with Skype, Deluge, Xchat, Rhythmbox, pidgin, firefox, thunderbird, nautilus and a number of small fish running. FF3 is by far the greatest memory hog with about 250-300mb of that.

---

### Post by PRGUY85 on 2008-05-25
Yea I thought FF3 was retooled for less resource usage, but I also read the Linux version has some resource usage problems..

---

