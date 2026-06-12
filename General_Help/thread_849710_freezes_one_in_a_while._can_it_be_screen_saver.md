---
title: "freezes one in a while. can it be screen saver?"
date: 2008-07-04
forum: General Help
---

### Post by Pacopag on 2008-07-04
I've been running Ubuntu 8 for a couple of weeks or so, and it has been working perfectly.  But in the last couple of days, it's been freezing up once in a while (but it's pretty seldom).  The only thing I can think of is that this started happening at almost the same time that I switched screen saver over to the "field lines" one.  I suspected this because it only freezes when the screen saver is activated.  Is this even possible?  Of course I'm going to change back to my old screen saver, but I wanted to ask.

Also, what is BAD about shutting down with the power button rather than shutting down properly?

Something to note is that my CPU often runs between 45 and 50 degrees celcius.  Could that be a problem.

---

### Post by karasuman on 2008-07-04
This has happened to me with Field Lines and Solar Winds.  I assumed that it must be the screen saver causing the problem.  :)

---

### Post by Pacopag on 2008-07-04
k good.  

Shouldn't I be getting emails when people reply to my threads??

---

### Post by unutbu on 2008-07-04
Pacopag, click on the "User CP" link in the upper left portion of your browser page. Then in the left panel, click on Edit Options. Scroll down to Messaging and Notification, Default Thread Subscription Mode, and change the drop down menu to Instant Email notification. 

It can be bad to power off the machine abruptly. To make the machine more responsive, sometimes when the machine is supposed to write information to the hard drive it instead says, "Nah, I'll wait until I get a bit more stuff to write, then I'll write it all at once." If you shut down the power abruptly, the machine never gets a chance to write the stuff that it was supposed to, and the result is a corrupt filesystem and some lost data. 
Occassionally the problem can be much more severe, causing the machine to be unbootable. This can be fixed, but it takes some know-how.

To avoid these dangers, try to shut down properly. If your machine freezes and you can't click the buttons to shutdown, there is a trick: Press
```

Alt+SysRq+r  ( The LEFT Alt key ) ( SysRq is on the same button as print screen )
Alt+SysRq+e
Alt+SysRq+i
Alt+SysRq+s
Alt+SysRq+u
Alt+SysRq+o
```

Wait a few seconds between keystrokes.

The r stands for put keyboard in raw mode
The e for terminate all processes
The i for kill all processes
The s for sync the disk
The u for remount all filesystems read only
The b for reboot the system
The o for shutdown the system 

These are low-level commands sent to the kernel. As long as the kernel isn't frozen, your machine will respond to these keypresses.

---

### Post by Pacopag on 2008-07-04
cool.  Those key sequences will come in handy.  Thanks.

---

### Post by mickcalcara on 2008-07-07
I have had similar problems with applications ( either Thunderbird or Firefox ) freezing up when returning  to the desktop after a screen saver ( glshideshow and skyrocket ) is running. So far it has just been applications that do not respond and not Gnome.  This happens about half the time.  Not sure

---

### Post by unutbu on 2008-07-07
mickcalcara, if it is just an app that is freezing rather than your whole machine, then often you can recover from the situation without having to reboot.

Go to System>Administration>System Monitor, click on the Processes tab, find 'firefox' or 'thunderbird' and right-click on it. Select kill process. 

If that doesn't work, then the following command-line method should work:

Open a terminal and type

```
ps axuw | grep firefox
```
(substitute the name of the frozen app for firefox).

You will see some output like this:
```
% ps axuw | grep firefox
atom    6089  0.0  0.1   3848  1356 ?        S    10:11   0:00 /bin/sh /usr/bin/firefox
atom    6101  0.0  0.1   3892  1384 ?        S    10:11   0:00 /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/firefox/firefox-bi
atom    6106  3.2 14.2 278460 147116 ?       Sl   10:11  12:10 /usr/lib/firefox/firefox-bin
atom    6978  0.0  0.0   2976   760 pts/0    R+   16:27   0:00 grep firefox
```

The first column lists the owner of the process. In the example above, the owner is atom. The numbers in the second column are Process ID (PID) numbers.

To kill a process type

```
kill PID
```
Sometimes this is too gentle and a frozen app will ignore this signal. In such situations you can type
```

kill -9 PID
```
This I believe sends the kill signal directly to the kernel, bypassing the frozen app entirely. No process that you own can survive the wrath of kill -9.

If root owns a process, then only root can kill it. In this case, use

```
sudo kill -9 PID
```
May the PID rest in peace.

---

