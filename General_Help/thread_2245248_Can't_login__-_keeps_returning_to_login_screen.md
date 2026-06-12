---
title: "Can't login  - keeps returning to login screen"
date: 2014-09-22
forum: General Help
---

### Post by h.f.raven on 2014-09-22
I am having an identical issue to [this thread]("http://ubuntuforums.org/showthread.php?t=2245109&p=13126723#post13126723"), and I am also dual-booting Ubuntu 14 with Win 7. I'm worried that it's likely because was too confident in the terminal and created some major damage. I'll describe it as accurately as possible:

- Removed both of the cairo-dock sources from my software sources (using management tool)
- Added Oracle VirtualBox to software sources, downloaded key, downloaded & installed VirtualBox through terminal/apt-get
- Mounted OS (C:\) and moved a 50GB virtual box from Windows 7 to my /home/ folder.

When I was moving the ~50GB file, my system slowed to a crawl. I couldn't even get a terminal running, and when one did, it had more than 10 seconds of latency between commands. I attempted to recover from the lag by doing the following:

- xkill on the programs that were running (other than hard drive operation) 
- Accidentally killed the window server and lost most of the control over the desktop
- Used Ctrl - Alt - F1 to run startx. Crashed again and computer almost completely froze. Rebooted. 

When I rebooted, I couldn't log into my profile. Identical problem as OP. I used my "Guest" profile to login just fine, loads the desktop/Unity. I tried another reboot, failed. Used just the command line to log in, was able to get into my user but whenever I attempt to run a command it past logging in, it immediately freezes. During my 1st attempt it told me that some file ".xsomething" was locked or that I didn't have permissions. Repeated endlessly until I did reboot. Anything that can be done for this? How am I supposed to troubleshoot this issue without admin rights unless I use the safety mode at grub?

note: I tried "sudo chown -R yourusername /home/yourusername" but my account froze   --- should I not have taken such a large file from my NTFS partition into my /home/ directory?

---

### Post by Iowan on 2014-09-22
Moved to separate thread.

---

### Post by h.f.raven on 2014-09-22
To get a closer look at the error so I could share it with the forums, I logged into the guest profile without issue. I then used the tty1 terminal to log into my true user account, and it loaded. Here is what happened:

> 
daedalus@majestic12:~$ startx
xauth: /home/daedalus/.Xauthority not writable, changes will be ignored 


Followed by:

> 
waiting for X server to begin accepting connections
..
No protocol specified
..
No protocol specified
..(II)AIGLX: Suspending AIGLX clients for VT switch

No protocol specified
..


Then proceeded by a timeout after about 100 more lines of that.
 
> 
xinit: giving up
xinit: unable to connect to X server: Resource temporarily unavailable

waiting for X server to shut down (EE) Server terminated successfully (0). Closing log file. 

xinit: server error
xauth: timeout in locking authority file /home/daedalus/.Xauthority


I'm not well versed in any of this but it appears to be a permissions issue. Have I wrecked my user profile? Why would any of the aforementioned changes have altered my user permissions? This is probably newbie's error.

---

### Post by steeldriver on 2014-09-23
When logged in at the tty1 terminal, what are the results of

```

ls -ld $HOME

ls -l $HOME/{.ICE,.X}authority

```

---

### Post by h.f.raven on 2014-09-23
Steeldriver: I logged into my user account through the tty1 terminal again. It seemed to load my account much faster this time and gave me the generic Linux no-warranty warning (did not before).

Output of ls -ld $HOME:
```

drwx------- 43 daedalus daedalus 12288 Sep 22 21:23 /home/daedalus/

```

Output of ls -l $HOME/{.ICE,.X}authority
```

-rw------- 1 daedalus daedalus 17042 Sep 21 22:43 /home/daedalus/.ICEauthority
-rw------- 1 root         root   263 Sep 21 22:43 /home/daedalus/.Xauthority

```

Does that help at all?

---

### Post by Bashing-om on 2014-09-23
h.f.raven; Hello :

yeah, helps. as :
> 
-rw------- 1 root         root   263 Sep 21 22:43 /home/daedalus/.Xauthority

Means "you" do not have access to your /home.
Change the ownership back to "you":
```

sudo chown daedalus:daedalus .Xauthority

```
log out and back in, now I expect that you have access.

[INDENT][INDENT]just my bit to try and help
[/INDENT][/INDENT]

---

### Post by h.f.raven on 2014-09-24
Bashing-om:
Once I changed the ownership on .Xauthority, I was able to start it up again. I couldn't quite get it running normally from inside tty1, but I rebooted the computer and everything worked fine at the normal Ubuntu login screen. Still not sure how I messed it up in the first place (too much sudo?) but it's okay now. Thank you so much everyone for your help. This is a great community. RESOLVED!

---

### Post by CantankRus on 2014-09-24
Make sure to use gksudo for gui applications...
eg **gksudo gedit**
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Bashing-om on 2014-09-24
h.f.raven; Great !

Pleased to be of some small help.

As to the why see CantankRus' ^^ .

As this mater is now concluded you must be the one to mark it solved; top of post -> thread tools.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

