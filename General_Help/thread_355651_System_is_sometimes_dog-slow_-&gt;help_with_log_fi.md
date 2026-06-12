---
title: "System is *sometimes* dog-slow -&gt;help with log files?"
date: 2007-02-07
forum: General Help
---

### Post by richardq on 2007-02-07
My system shows intermittent performance problems. Every 3rd or 4th time I boot up the system runs dog slow. I can tell immediately after I log in whether or not the system is going to run slowly by the amount of time it takes to get to the desktop.

Typical symptoms when it's running slowly:

1. It's relatively slow to get from the GDM login to the actual splashscreen and desktop.
2. It's very slow to fully populate the gnome menu bar along the top with icons and the menus.
3. Apps take an abnormally long time to launch (firefox-20sec, calculator-10sec etc.)
4. File->Open dialog boxes take a long time to populate with files, sometimes 10 or 15 seconds at least.
5. Nautilus windows take a long time to launch and a long time to populate with files. Probably 5 times longer than normal.
6. Some apps seem to work at normal speed once they're open. For example, Firefox works fine once it is launched. Others definitely run more slowly.
7. I'm running Beryl (same behaviour occurs with Metacity) and sometimes apps will 'grey' out like they're chugging away on calculations many times. This occurs in apps like Gimp and Inkscape. This 'greying' out never occurs when the system is running at normal speed.

I'm pretty much a newbie when it comes to system troubleshooting with log files. I'm not sure which ones to look at and what to look for. It seems like something is happening before X is started but I'm not sure. If anyone can point me to any good information on Linux system log files and performance troubleshooting I'd really appreciate it.

My system is a P4-3Ghz with 1GB Ram, Intel On Board Video, running Edgy with Beryl.

---

### Post by dcstar on 2007-02-07
> **richardq said:**
> My system shows intermittent performance problems. Every 3rd or 4th time I boot up the system runs dog slow. I can tell immediately after I log in whether or not the system is going to run slowly by the amount of time it takes to get to the desktop.

Typical symptoms when it's running slowly:

1. It's relatively slow to get from the GDM login to the actual splashscreen and desktop.
2. It's very slow to fully populate the gnome menu bar along the top with icons and the menus.
3. Apps take an abnormally long time to launch (firefox-20sec, calculator-10sec etc.)
4. File->Open dialog boxes take a long time to populate with files, sometimes 10 or 15 seconds at least.
5. Nautilus windows take a long time to launch and a long time to populate with files. Probably 5 times longer than normal.
6. Some apps seem to work at normal speed once they're open. For example, Firefox works fine once it is launched. Others definitely run more slowly.
7. I'm running Beryl (same behaviour occurs with Metacity) and sometimes apps will 'grey' out like they're chugging away on calculations many times. This occurs in apps like Gimp and Inkscape. This 'greying' out never occurs when the system is running at normal speed.

I'm pretty much a newbie when it comes to system troubleshooting with log files. I'm not sure which ones to look at and what to look for. It seems like something is happening before X is started but I'm not sure. If anyone can point me to any good information on Linux system log files and performance troubleshooting I'd really appreciate it.

My system is a P4-3Ghz with 1GB Ram, Intel On Board Video, running Edgy with Beryl.

Sometimes DNS issues can affect your system, do a forum search for "disable ipv6" and try out some of the solutions.

---

### Post by spone on 2007-04-27
Sorry for digging up this 'old' thread, but to me it seemed a bit pointless creating a new thread for this. 

I just installed Feisty final and it suffers from the same slowness like this. Not just sometimes, but everytime. Already tried to disable ipv6, disabling unused network cards, uninstalling network manager, enabling/disabling beryl, it just is horribly slow as described above.

System config:
AMD3500+, MSI K8N-Neo4-F mainboard, Geforce 7900GS, 1536MB RAM, kernel 2.6.20-15-generic i686.

---

### Post by | MM | on 2007-04-27
I have also found problems with the font cache can dramatically increase the time it takes teh Gnome desktop and applications to load, though not affecting load or actual performance once the program is running.  If you have added fonts or tried to rebuild your cache this could be it.  There was an issues and the resolution was to *touch* each font subfolder to update its date, so that the font cache could be successfully rebuilt.

---

### Post by spone on 2007-04-28
Now you say so, 

When I added some fonts like tahoma and some other truetype fonts and did a manual 'fc-cache -v -f' it told me at about every folder that the font cache update failed or something in that fashion. It worked nevertheless so I didnt care ;) But ill try touching every font subfolder and see if it helps. Thanks!

---

### Post by msfisher on 2007-04-28
I've had the same problem for weeks.  I've posted about it repeatedly and gotten little help.  In one case, none at all.

Like others, I've disabled ipv6, corrected the hosts file, updated the video driver and finally upgraded from Edgy to Feisty.  Nothing helped.

This is an ongoing problem, as a search on the forum brings up numerous threads in all areas.  The problem is characterized as the poster above noted. IN ADDITION, a symptom is slow ping times -- alternating between several hundred and over a thousand milliseconds for each ping JUST TO REACH THE ROUTER.  

I hope someone actually answers you on this, as I'd like to get it fixed so I can give Ubuntu a decent trial.

---

### Post by spone on 2007-04-28
Thanks a whole lot | MM | , touching the font folders and running fc-cache afterwards solved the slowness! 

/happy

@msfisher: Just a guess but maybe disabling that avahi thing helps (its somewhere hidden in network prefs).

---

### Post by Circleback on 2007-04-29
I uninstalled some fonts via synaptic and ran this command and it sill complains that I am missing some fonts. Also, i touch -ed the some of the font folders and it gives me a message that they are out of date. Should I touch  every ttf file as well?

---

