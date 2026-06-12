---
title: "Perpetual/Non-stopped Disc Writing (&quot;bmcapure&quot;)"
date: 2022-10-28
forum: General Help
---

### Post by n2te on 2022-10-28
I have an issue on my 20.04 machine where a process keeps writing to the disc every 1 second. Anywhere from 1 to 2Kb of data. If I remove my network cable, the repetitive writing stops. After investigating I have determined that the culprit is some mystery process called "**bmcapture**".  However I can't figure out how to eliminate it  from launching at startup. The process is called "bmcapture" but there doesn't seem to be much info about it on the internet. (Only some  mentions in an OSX forum.)  

(1.) There is an executable file in **/usr/bin/**:
-rwxr-xr-x  1 40887 Jul 27  2014 **bmcapture***

(2.) i**otop** finds it and lists the PID & owner as root:
**TID:742**, Priority be/4, **User:root**, DiskRead:0, DiskWrite:24K/s, **Command: bmcapture**

(3.) **pidof bmcapture** also lists the PID:
742

(4.) **systemctl** shows no such service running:
~$ sudo systemctl list-unit-files --type=service
(5.) **dpkg** -l |grep bmcapture finds no such named installed package
(6.) **snap list** finds no such named installed package

(7.)  In **/etc/init.d** there are two executable files that I own called  bitmeter and bitmeterweb. But I have no indication if they're related to  the "bmcapture" process. (I figured the letters "bm" might mean something.)

(8.) **sudo killall bmcapture fixes the problem. **I'd rather just eliminate the source from my machine rather than execute that command when launching the machine.

[COLOR=#ff0000]**So WHO launches this thing?**[/COLOR] As I haven't identified any removal or uninstall option should I  merely delete the '/usr/bin/bmcapture' executable file and then reboot  and hope for the best? Most intriguing.Suggestions?

---

### Post by #&amp;thj^% on 2022-10-28
I'm only guessing here because I've not seen this since 2016, but what dose this return:
```
dpkg -L bitmeteros
```
>  But I have no indication if they're related to the "bmcapture" process.
The above would confirm or not.
If your not using that program, you could just remove it:
```
sudo apt purge bitmeteros
```
EDIT Now I remember what it was.....bandwidth monitoring tool with CLI and web interfaces 
So yes you will see activity on your disk.

---

### Post by Holger_Gehrke on 2022-10-28
Have you tried 'dpkg-query -S /usr/bin/bmcapture' ? That should tell what package - if any - the file belongs to. On the other hand, packages.ubuntu.com doesn't have any hits if I search for the filename 'bmcapture', so unless you installed things from PPAs or downloaded the .deb file directly it's probably not from a package.

Holger

---

### Post by n2te on 2022-10-28
[COLOR=#0000ff]***[1fallen] ***[/COLOR]-  THAT WAS IT! You're my hero. I can't tell you how much time I spent  poking around trying to figure out where that mystery process originated.  

The cmd you suggested **'dpkg -L bitmeteros'** returned a list of results a *mile long*!  '**sudo apt purge bitmeteros**'  did the trick. I removed the app and the annoying endless disk pounding has  finally gone away. The life expectancy of my HDD has just increased another hundred years.

Thank you for your assistance. Much appreciated. 

[* * PROBLEM SOLVED ** ]

---

