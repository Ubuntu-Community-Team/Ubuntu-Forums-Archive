---
title: "how do i get a daemon to load on startup?"
date: 2004-11-04
forum: General Help
---

### Post by brschmid on 2004-11-04
i have installed cpufreqd so my laptop runs at full speed while plugged into AC power, and then scales back while on battery. 

but in order to get it to start i need to start it in the root terminal. 

is there a way to get it to start at boot so my Folding at home will operate at full speed??

---

### Post by Magneto on 2004-11-04
make sure you add a link to cpufreqd to the proper runlevel

check /etc/inittab  for the default
```

 more /etc/inittab
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:


```



then make a script like

sudo nano -w /etc/init.d/cpufreq
[Color=Red]
#!/bin/bash

/yourpath/to/cpufreqd start
[/color]

then

sudo chmod +x /etc/init.d/cpufreq


and create a symlink to /etc/init.d/cpufreq in the runlevel folder that corresponds to your default runlevel listed in /etc/inittab- 

sudo ln -s /etc/init.d/cpufreq /etc/rc2.d /etc/rc2.d/cpufreq



when your system starts it will read your inittab and execute every script in your runlevel folder

---

### Post by brschmid on 2004-11-04
[QUOTE=Magneto]make sure you add a link to cpufreqd to the proper runlevel

check /etc/inittab  for the default
```

 more /etc/inittab
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:


```



then make a script like

sudo nano -w /etc/init.d/cpufreq
[Color=Red]
#!/bin/bash

/yourpath/to/cpufreqd start
[/color]

then

sudo chmod +x /etc/init.d/cpufreq


and create a symlink to /etc/init.d/cpufreq in the runlevel folder that corresponds to your default runlevel listed in /etc/inittab- 

sudo ln -s /etc/init.d/cpufreq /etc/rc2.d /etc/rc2.d/cpufreq



when your system starts it will read your inittab and execute every script in your runlevel folder[/QUOTE]
 shouldve added i am a noob :(

---

### Post by Magneto on 2004-11-04
does that mean you could follow what i was saying?
If so sorry I wasnt clear enuf

you need to create a link to the program that you run for your cpu in a certain folder- that way every time you turn your computer on it will automatically run
same concept as the windows Startup folder in start menu-->Programs

your laptop will start in runlevel2- so you need a link in the folder /etc/rc2.d that points to your cpu program

---

### Post by wallijonn on 2004-11-04
By default Ubuntu uses run level 2. init.d is the directory which holds all the daemon start files. (d=daemon; therefore cpufreqd = cpufreq daemon, just like inetd = internet daemon. (don't confuse with in[Color=red]**i**[/COLOR]t[COLOR=RED]**.**[/COLOR]d which is the system _init_ialisation daemon)).

sudo gedit /etc/init.d/cpufreq.sh
#!/bin/bash
<path to>cpufreqd start
exit gedit

<path to> = where did SPM install it? does SPM install cpufreq to /usr/bin?

**Do Computer -> Search for files -> cpufreqd -> look in folder ->  / -> Available Options -> Date Modified More than -> Find**

so the above lines would be (if it installs to /usr/bin)

sudo gedit /etc/init.d/cpufreq.sh
#!/bin/bash
/usr/bin/cpufreqd start

{exit gedit & save the file}

open a root terminal {you should already be at a root terminal if you are doing the above, so at the root prompt, "#", copy / paste (two lines below)/ hit the carriage return key

sudo chmod +x /etc/init.d/cpufreq
sudo ln -s /etc/init.d/cpufreq /etc/rc2.d /etc/rc2.d/cpufreq

{reboot the PC}

the "ln" in the above command creates a **l**i**n**k. The small "s" says to create a 'soft symbolic' link. 

Magneto, am I mistaken by saying _sudo gedit /etc/init.d/cpufreq.sh_ where .sh is a shell script? or should it be left out altogether?

And shouldn't the command be _sudo ln -s /etc/init.d/cpufreq /etc/rc2.d/cpufreq_?


.

---

### Post by brschmid on 2004-11-04
[QUOTE=wallijonn]By default Ubuntu uses run level 2. init.d is the directory which holds all the daemon start files. (d=daemon; therefore cpufreqd = cpufreq daemon, just like inetd = internet daemon. don't confuse with in**i**t**.**d which is the system initialisation daemon)).

sudo gedit /etc/init.d/cpufreq.sh
#!/bin/bash
<path to>cpufreqd start
exit gedit

<path to> = where did SPM install it? does SPM install cpufreq to /usr/bin?

Do Computer -> Search for files -> cpufreqd -> look in folder ->  / -> Available Options -> Date Modified More than -> Find

so the above lines would be (if it installs to /usr/bin)

sudo gedit /etc/init.d/cpufreq.sh
#!/bin/bash
/usr/bin/cpufreqd start

{exit gedit & save the file}

open a root terminal {you should already be at a root terminal if you are doing the above, so at the root prompt, "#", copy / paste (two lines below)/ hit the carriage return key

sudo chmod +x /etc/init.d/cpufreq
sudo ln -s /etc/init.d/cpufreq /etc/rc2.d /etc/rc2.d/cpufreq

the "ln" in the above command creates a **l**i**n**k. The small "s" says to create a 'soft symbolic' link. 

Magneto, am I mistaken by saying _sudo gedit /etc/init.d/cpufreq.sh_ where .sh is a shell script? or should it be left out altogether?


.[/QUOTE]
 i thought you meant to just follow, but i wasn't sure, i will try this now.

---

### Post by Magneto on 2004-11-04
nope - i sudo gedit all the time cause it keeps those links to the last files you opened and you can have multiple files open 

Extensions are fine in gedit  u can open or create a file with any extension

---

### Post by wallijonn on 2004-11-04
I was just reading up on NANO and I found that the "-w" is a 'wrap around' commnd. People who use PICO will probably be right at home using NANO.

As a noob I am more likely to use GEDIT since that is what's on the GUI taskbar.

---

### Post by Magneto on 2004-11-04
im a VI person but using gentoo got me into using nano -w
now i use it more in linux- but vi is always the original

---

### Post by brschmid on 2004-11-05
[QUOTE=Magneto]im a VI person but using gentoo got me into using nano -w
now i use it more in linux- but vi is always the original[/QUOTE]
 ok, i tried the method above twice and it didn't work either time. 

from a search i found that it was installed to /usr/sbin/
and it was setup in all the rc*.d folders but it says all the links are broken. 

how can i fix it?

---

### Post by Magneto on 2004-11-05
if the links are broken then they are pointing to the wrong place
open a terminal
1. cd /etc/rc2.d    (since this is the runlevel u will using most of the time)
2. ls -al
3. what does the link for cpufreq point to?
4. sudo rm cpufreqd  (or whatever that cpufreq link is named)
5. sudo ln -s /usr/sbin/cpufreqd /etc/rc2.d/cpufreqd       (you know the real name of your cpufreq script so replace that cpufreqd with the right name if im incorrect)
6. ls -al   the link shouldnt be broken anymore right?

it should work now

---

### Post by brschmid on 2004-11-05
[QUOTE=Magneto]if the links are broken then they are pointing to the wrong place
open a terminal
1. cd /etc/rc2.d    (since this is the runlevel u will using most of the time)
2. ls -al
3. what does the link for cpufreq point to?
4. sudo rm cpufreqd  (or whatever that cpufreq link is named)
5. sudo ln -s /usr/sbin/cpufreqd /etc/rc2.d/cpufreqd       (you know the real name of your cpufreq script so replace that cpufreqd with the right name if im incorrect)
6. ls -al   the link shouldnt be broken anymore right?

it should work now[/QUOTE]
 ok, that didn't work either :(

EDIT: i went and fixed all the links, rc0.d -> rc6.d and it still doesn't work :(

---

### Post by brschmid on 2004-11-05
[QUOTE=brschmid]ok, that didn't work either :(

the S20cpufreqd link is pointing to /etc/init.d/cpufreqd

and i went thru and typed what you said to type and it is still pointing to that location and it still doesn't start up on boot either.[/QUOTE]
 ok, i got that link fixed, should i fix the rest of them, since it still doesn't begin at startup?

---

### Post by Magneto on 2004-11-05
add a S to the startup script name in rc2.d

change the link to 

/etc/rc2.d/Scpufreqd

the S in the name tells init to Start that process

sorry about that

---

### Post by brschmid on 2004-11-06
it is currently named S20cpufreqd

some the folders had K scripts and some had S. (i mean that is all they had, either K or S, not both)

should i delete all the K's?

---

### Post by Magneto on 2004-11-06
[QUOTE=brschmid]it is currently named S20cpufreqd

some the folders had K scripts and some had S. (i mean that is all they had, either K or S, not both)

should i delete all the K's?[/QUOTE]

NO

scripts in that folder are meant to be Started or Killed- dont modify anything but that sole link you are trying to get working

1. so its named /etc/rc2.d/S20cpufreqd?
2. you can run cpufreqd and it loads?
3.you can ./S20cpufreqd and it runs?
4. at startup cpufreqd still doesn't load?

---

### Post by brschmid on 2004-11-06
[QUOTE=Magneto]NO

scripts in that folder are meant to be Started or Killed- dont modify anything but that sole link you are trying to get working

1. so its named /etc/rc2.d/S20cpufreqd?
2. you can run cpufreqd and it loads?
3.you can ./S20cpufreqd and it runs?
4. at startup cpufreqd still doesn't load?[/QUOTE]
 1. yes
2. yes
3. yes from /etc/rc2.d
4. correct

---

### Post by fissy on 2004-11-06
I was interested in how to turn off postfix, i don't know why it comes on by default in ubuntu...
anyway, looking at this thread, managing services is a nightmare!

would it be possible to port gentoo's rc-update and rc-status tools?

---

### Post by Magneto on 2004-11-07
i had to take a look at how debian's/ubuntu's inittab-runlevels work in order to write some scripts for my laptop- xf86 config script and a network switching script 
In gentoo it was easy with adding softlevel to a grub menu.lst option
In slackware its easy too and pretty similar to debian with the exception of the S and K filename flags and the ordering numbers which makes debian better than slackware in this regard but far more constrained than gentoo - gentoo's ability to add any number of init states labeled however you want without having to edit inittab is better IMO

im gonna make a thread in howto of how i use inittab and rc scripts

postfix comes on by default because the mail system is used to log errors and send notifications 
apt-get is setup for this by default but strangely enough sudo isnt

But you can do everything you want with debian's inittab system through proper use of rc scripts and grub.

---

### Post by brschmid on 2004-11-07
[QUOTE=Magneto]i had to take a look at how debian's/ubuntu's inittab-runlevels work in order to write some scripts for my laptop- xf86 config script and a network switching script 
In gentoo it was easy with adding softlevel to a grub menu.lst option
In slackware its easy too and pretty similar to debian with the exception of the S and K filename flags and the ordering numbers which makes debian better than slackware in this regard but far more constrained than gentoo - gentoo's ability to add any number of init states labeled however you want without having to edit inittab is better IMO

im gonna make a thread in howto of how i use inittab and rc scripts

postfix comes on by default because the mail system is used to log errors and send notifications 
apt-get is setup for this by default but strangely enough sudo isnt

But you can do everything you want with debian's inittab system through proper use of rc scripts and grub.[/QUOTE]
 thanks, can you put the link in this thread?

---

### Post by humberto on 2004-11-07
[QUOTE=fissy]I was interested in how to turn off postfix, i don't know why it comes on by default in ubuntu...
anyway, looking at this thread, managing services is a nightmare!

would it be possible to port gentoo's rc-update and rc-status tools?[/QUOTE]

Debian (and ubuntu) have update-rc.d, it isn't quite as nice as redhat's chkconfig, but it works.

man update-rc.d

---

### Post by Magneto on 2004-11-07
[QUOTE=brschmid]thanks, can you put the link in this thread?[/QUOTE]

Just finished it
[http://www.ubuntuforums.org/showthread.php?t=3550](http://www.ubuntuforums.org/showthread.php?t=3550)
it just described placing a script in /etc/init.d making it executable and creating a link in /etc/rc2.d and /etc/rc3.d to start them - but i just changed it to use update-rc.d which only does what we've done already
and when/if you try update-rc.d cpufreqd defaults - it wont change much because you already have the link in /etc/rc.2d

I seriously dont know what is going on with your system






Humberto-- yeah update-rc.d is similar to rc-update in gentoo but i like gentoo's system better

the link that was recommended /etc/rc2.d/S20cpufreqd  is the same thing that update-rc.d cpufreqd 20 start 2 . stop 20 1 6 .  would do without the kill scripts - but the kill scripts arent necessary for it to work 
any idea where  this could be going wrong for brschmid?
I changed my howto in that other thread since update-rc.d is the preferred method of setting up init scripts - I couldnt remember that update-rc.d command I had used it when I first installed my system and changed the kernel and needed to dump those module loaders

---

### Post by p!=f on 2004-11-07
What's wrong with cpufreqd? I can see it already contains startup scripts. At least here on **Hoary** (version 1.2.2).

I don't think it will work. You don't have any stop or restart section in that script anyway, so using update-rc.d and linking to K will be useless.

It would be more efficient to use startup template which can be found at /etc/init.d/skeleton and after the editation use update-rc.d or perhaps even better create /etc/rc.boot directory and place your custom scripts inside.
Here's the script I use to get 800 cpi from my mouse and it starts automagically on boot.
```

 * 15:09:45 * pef @ agonicus *
[~] > ls -l /etc/rc.boot/
celkem 1
-rwxr-xr-x  1 root root 66 2004-10-08 17:12 logitech_applet

 * 15:09:50 * pef @ agonicus *
[~] > cat /etc/rc.boot/logitech_applet
#!/bin/sh
echo "Tunning Logitech mouse..."
logitech_applet -s 800

```
Don't forget to add the executable permission onto your scripts or it won't start.


What suprises me is that the startup scripts didn't came along the package.

---

### Post by brschmid on 2004-11-07
cpufreqd was not included in the base system, but i was able to get it thru SPM. all i want is my laptop to function at full speed while plugged into AC, and scaled back when on battery. 

it won't start automatically by itself :(

---

### Post by brschmid on 2004-11-07
i made some progress, i created a link in the /etc/rcS.d directory. 

this is what happens:

Nov  7 12:00:24 localhost powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens 
Nov  7 12:00:24 localhost powernowd: Found 1 cpu: 
Nov  7 12:00:24 localhost powernowd:   cpu0: 600Mhz - 1400Mhz 

then a little later, it tries to start cpufreqd 

Nov  7 12:03:53 localhost powernowd: PowerNow Daemon Exiting. 
Nov  7 12:04:47 localhost cpufreqd: find_cpufreq_interface(): no cpufreq interface found. 
Nov  7 12:04:47 localhost cpufreqd: Unable to find a cpufreq interface, please ensure to have cpufreq enabled in the running kernel. Exiting. 

then a minute later powernowd started again
Nov  7 12:04:58 localhost powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens 
Nov  7 12:04:58 localhost powernowd: Found 1 cpu: 
Nov  7 12:04:58 localhost powernowd:   cpu0: 600Mhz - 1400Mhz 

but boot doesn't take that long, so i am unsure of why, but i know the error message for cpufreqd starts when the system is booting. 


i am confused why though, because i can run it when i get into linux. does cpufreq (which is required by Powernowd as well start when the GUI starts???)

t

---

### Post by Magneto on 2004-11-07
[QUOTE=brschmid]i made some progress, i created a link in the /etc/rcS.d directory. 

this is what happens:

Nov  7 12:00:24 localhost powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens 
Nov  7 12:00:24 localhost powernowd: Found 1 cpu: 
Nov  7 12:00:24 localhost powernowd:   cpu0: 600Mhz - 1400Mhz 

then a little later, it tries to start cpufreqd 

Nov  7 12:03:53 localhost powernowd: PowerNow Daemon Exiting. 
Nov  7 12:04:47 localhost cpufreqd: find_cpufreq_interface(): no cpufreq interface found. 
Nov  7 12:04:47 localhost cpufreqd: Unable to find a cpufreq interface, please ensure to have cpufreq enabled in the running kernel. Exiting. 

then a minute later powernowd started again
Nov  7 12:04:58 localhost powernowd: PowerNow Daemon v0.90, (c) 2003-2004 John Clemens 
Nov  7 12:04:58 localhost powernowd: Found 1 cpu: 
Nov  7 12:04:58 localhost powernowd:   cpu0: 600Mhz - 1400Mhz 

but boot doesn't take that long, so i am unsure of why, but i know the error message for cpufreqd starts when the system is booting. 


i am confused why though, because i can run it when i get into linux. does cpufreq (which is required by Powernowd as well start when the GUI starts???)

t[/QUOTE]


those scripts have numbers at the beginning like S20someprocess  S23anotherprocess 
init looks at those numbers for the order in which to execute those scripts
basically its not loading because the cpufreq module that your kernel uses to interact with cpufreqd has yet to be loaded
when you load it from the commandline all your modules have already been loaded

do this
```

sudo update-rc.d cpufreqd start 99 2 3 4 5 . stop 99 0 1 6 .
```
dont forget both periods

this will create a link with the S99 flag instead of S20 - you can remove that S20cpufreqd link

this will cause the process to be started in the last group, well after your cpufreq module has been loaded

---

### Post by brschmid on 2004-11-08
[QUOTE=Magneto]those scripts have numbers at the beginning like S20someprocess  S23anotherprocess 
init looks at those numbers for the order in which to execute those scripts
basically its not loading because the cpufreq module that your kernel uses to interact with cpufreqd has yet to be loaded
when you load it from the commandline all your modules have already been loaded

do this
```

sudo update-rc.d cpufreqd start 99 2 3 4 5 . stop 99 0 1 6 .
```
dont forget both periods

this will create a link with the S99 flag instead of S20 - you can remove that S20cpufreqd link

this will cause the process to be started in the last group, well after your cpufreq module has been loaded[/QUOTE]
 i tried it at 80, and that didn't work, but i will try this.

---

### Post by brschmid on 2004-11-08
uh oh, we have problems. 

>  # update-rc.d cpufreqd start 99 2 3 4 5 . stop 99 0 1 6 .
update-rc.d: warning: /etc/rc0.d/K20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc1.d/K20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc2.d/S20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc2.d/K20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc3.d/S20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc4.d/S20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc5.d/S20cpufreqd is not a link to ../init.d/cpufreqd
update-rc.d: warning: /etc/rc6.d/K20cpufreqd is not a link to ../init.d/cpufreqd
 System startup links for /etc/init.d/cpufreqd already exist.


---

### Post by brschmid on 2004-11-08
ignore the previous 2 messages, sorta.

I changed all the links to S99, and this time i worked :) thanks i also changed all the links from /usr/sbin/cpufreqd   to /etc/init.d/cpufreqd   and now it works, but when i try what you said to do, i still get the error message, even though 'ls -al' shows each S99cpufreqd linked to /etc/init.d/cpufreqd

all that matters is it now works, and I am happy, 

thanks a lot magneto.

---

### Post by Magneto on 2004-11-08
glad u got it sorted out! nah thats not a bad error -  update-rc.d will do that every time if a link for the process you're trying to add is already present
update-rc.d process -f remove          will get rid of stuff from those rc*.d directories too but it will leave the script in /etc/init.d which is cool for adding it back later

---

