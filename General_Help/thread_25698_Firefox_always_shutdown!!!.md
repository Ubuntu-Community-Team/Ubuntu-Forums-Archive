---
title: "Firefox always shutdown!!!"
date: 2005-04-10
forum: General Help
---

### Post by Gandalf on 2005-04-10
Hello, :D
well i don't know for what reason firefox always crash (just disppear), i was on ubuntu hoary condidate, and for reason of partitioning i formated and installed the final release and on the both release firefox just dispear!!! i tried to run it from the terminal and here's the output:
```

wael@nasreddine:~$ firefox&
[2] 9895
wael@nasreddine:~$ .....A
.....A
.....A
.....A

[2]+  Segmentation fault      firefox
wael@nasreddine:~$

```
anyone has the same problem?????

---

### Post by jdong on 2005-04-10
I've experienced a few rare segfaults with Firefox under Hoary, when playing with the GNOME file selector dialogs, but nothing as serious as you mentioned. since the problem persisted across two installs for you, I suspect it may be hardware related (faulty RAM?). At the bootup screen, please select Memtest, and allow the test to finish (may take a few hours).

---

### Post by Gandalf on 2005-04-10
[QUOTE=jdong]I've experienced a few rare segfaults with Firefox under Hoary, when playing with the GNOME file selector dialogs, but nothing as serious as you mentioned. since the problem persisted across two installs for you, I suspect it may be hardware related (faulty RAM?). At the bootup screen, please select Memtest, and allow the test to finish (may take a few hours).[/QUOTE]
 i'm not sure, it's a brand new laptop, and only firefox is crashing!!!!

---

### Post by souki on 2005-04-11
[QUOTE=Gandalf]i'm not sure, it's a brand new laptop, and only firefox is crashing!!!![/QUOTE]
 I have the same issue,

I'm trying to reproduce it ...

---

### Post by jdong on 2005-04-11
[QUOTE=Gandalf]i'm not sure, it's a brand new laptop, and only firefox is crashing!!!![/QUOTE]

Please run the memtest (it's in the bootup menu); bad RAM is pretty common. It took me three returns at CompUSA to get a good stick of 512 for my laptop.

---

### Post by trenths on 2005-04-11
I was having that problem in Fedora and still am in Windows XP with Firefox but haven't had it happen in Ubuntu yet. I have run memtest and my ram checks out okay. I have also experienced the same phenomenon with IE in Windows XP but happens much less often than with Firefox. Nonbrowser apps have been completely stable, however. I have my machine overclocked so it may be a timing problem with some apps but not others.

---

### Post by IceAxe18 on 2005-04-11
I'm haveing problems with my Firefox shuting down to.  I did do the memtest & I passed the test.

---

### Post by kadissie on 2005-04-12
[QUOTE=IceAxe18]I'm haveing problems with my Firefox shuting down to.  I did do the memtest & I passed the test.[/QUOTE]
 I will be running memtest later, but this is just to chime in with my own experience.

I'm running a desktop (Pentium 4, 256MB RAM) and Firefox seems flakey.  Not necessarily the same as described above - that's why I'm scouring the forum now :-)  Essentially Firefox crashes when browsing certain sites, which seem to be sites which use Javascript.  Disabling javascript almost, but not quite, solves the problem.  Not enough systematics yet to diagnose.

Sadly, these crashes mostly happen when my girlfriend's surfing the web - so she's rather unimpressed with Ubuntu at the moment, having had it inflicted on her three weeks ago!

R

---

### Post by kadissie on 2005-04-12
I will be running memtest later, but this is just to chime in with my own experience.

I'm running a desktop (Pentium 4, 256MB RAM) and Firefox seems flakey.  Not necessarily the same as described above - that's why I'm scouring the forum now :-)  Essentially Firefox crashes when browsing certain sites, which seem to be sites which use Javascript.  Disabling javascript almost, but not quite, solves the problem.  Not enough systematics yet to diagnose.

Sadly, these crashes mostly happen when my girlfriend's surfing the web - so she's rather unimpressed with Ubuntu at the moment, having had it inflicted on her three weeks ago!

R

---

### Post by Gandalf on 2005-04-15
i did the memtest (the one integrated with ubuntu, my bios don't have memtest option) 8 hours for the test and is the result is fine no errors found, and now i'm on the third fresh install with the same problem :'(

---

### Post by nigerag on 2005-04-15
I would start with checking Firefox plugins, especially - JRE. Try to remove them one by one and see if that makes any difference. That happened to me few time after I installed wrong java plugin  and adblock extension. Reinstalling proper plugin fixed the problem.

---

### Post by Gandalf on 2005-04-19
[QUOTE=nigerag]I would start with checking Firefox plugins, especially - JRE. Try to remove them one by one and see if that makes any difference. That happened to me few time after I installed wrong java plugin  and adblock extension. Reinstalling proper plugin fixed the problem.[/QUOTE]
 i only have a theme installed, not even one plugin, that's what makes it weird

---

### Post by weblars on 2005-04-19
I also experienced shutdowns of Firefox only on certain sites. I figured our that in my case the libflash-mozilla package caused the crashes. Removing the package and using flashplayer-mozilla worked for me.

---

### Post by Gandalf on 2005-04-19
[QUOTE=weblars]I also experienced shutdowns of Firefox only on certain sites. I figured our that in my case the libflash-mozilla package caused the crashes. Removing the package and using flashplayer-mozilla worked for me.[/QUOTE]
 well i actulally re-tested it and indeed it only crashes on sites with flash player items, but i have flashplayer-mozilla installed and not libflash-mozilla !!!

---

### Post by jdong on 2005-04-19
Aha, a cause!


File a bugreport with Ubuntu, and see where you can get. Developer attention is important with these bugs.

---

### Post by Gandalf on 2005-04-19
Thank you man you just solved all my problems, i have tried it with 20 tabs with different flash sites that was crashing my mozilla and not even one single crash
what i did:
```

sudo apt-get remove flashplayer-mozilla
sudo apt-get install libflash-mozplugin

```

Again thank you thank you man

@jdong  where can i do that????

---

### Post by jdong on 2005-04-19
[https://bugzilla.ubuntu.com](https://bugzilla.ubuntu.com)

---

### Post by Gandalf on 2005-04-19
[QUOTE=jdong][https://bugzilla.ubuntu.com](https://bugzilla.ubuntu.com)[/QUOTE]
 ok bug poste [here](https://bugzilla.ubuntu.com/show_bug.cgi?id=9938)

---

### Post by Gandalf on 2005-04-20
i also noticed something, :'( after
```

sudo apt-get remove flashplayer-mozilla
sudo apt-get install libflash-mozplugin

```
swf clips are so weird they  are all mixed!!!!!! :'( so i have t choose between crashing or swf playing!!!!

---

### Post by artio on 2005-04-25
Same here, have had firefox (and mozilla) crash on sites that play flash animations (e.g. [www.corriere.it)](www.corriere.it)). Searched the web, tried removing the ~/.mozilla directory, the /usr/lib/mozilla/plugins and components directories, removing firefox and mozilla completely and compiling from source, removing all plugins, all to no avail.

I just followed the remove flashplayer-mozilla and install libflash-mozplugin advice - the browsers no longer crash but the weather forecast animations at [www.corriere.it](www.corriere.it) still don't work properly.

PS: They all worked fine until a week ago, when I installed a few packages to try out desktop compositing and the enlightenment windows manager. Have since removed those packages again, but the browser kept crashing (not sure they're related, though).

---

### Post by Gandalf on 2005-04-25
[QUOTE=artio]Same here, have had firefox (and mozilla) crash on sites that play flash animations (e.g. [www.corriere.it)](www.corriere.it)). Searched the web, tried removing the ~/.mozilla directory, the /usr/lib/mozilla/plugins and components directories, removing firefox and mozilla completely and compiling from source, removing all plugins, all to no avail.

I just followed the remove flashplayer-mozilla and install libflash-mozplugin advice - the browsers no longer crash but the weather forecast animations at [www.corriere.it](www.corriere.it) still don't work properly.

PS: They all worked fine until a week ago, when I installed a few packages to try out desktop compositing and the enlightenment windows manager. Have since removed those packages again, but the browser kept crashing (not sure they're related, though).[/QUOTE]
 someone suggested on the BUG REPORT to do this, i'm actually rying it so far so good, but i will see,

Open /etc/mozilla-firefox/mozilla-firefoxrc
replace "auto" with "none"

he said it's a sound problem

---

### Post by artio on 2005-04-26
Thanks for the pointer. I tried it but firefox and mozilla (and epiphany!) still crash. Reproducing the problem when running any of these browers from the command line gives me the following error: 

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 117 error_code 8 request_code 147 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I've searched for this, too, but haven't found anything that has solved the problem. I don't enough to follow the "note to programmers."

---

