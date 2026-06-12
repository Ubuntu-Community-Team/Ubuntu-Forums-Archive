---
title: "Lubuntu 13.04 - CUPS fails to start on bootup"
date: 2013-04-26
forum: General Help
---

### Post by Dennis N on 2013-04-26
Lubuntu 13.04: 

CUPS is not starting at boot-up. I discovered this when attempting to install the printer with this new install. I then started CUPS from the terminal, was able to install the printer, and print. However, on restarting the computer, the service again fails to start. How do I configure this service to always automatically start on bootup?

There is a Desktop Sessions Settings dialog of automatically started applications, but CUPS is not included there.

---

### Post by Synoc on 2013-04-26
open a terminal and give me the output of 
```

head /etc/init/cups.conf

```
I've not SEEN it configured wrong before, but I've never not not seen CUPS start on startup before either

---

### Post by Dennis N on 2013-04-26
Here is the output:

```

dn@Alexa:~$ head /etc/init/cups.conf
# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

start on (filesystem
          and started avahi-daemon
          and (started dbus or runlevel [2345]))
stop on runlevel [016]

```

---

### Post by tgalati4 on 2013-04-26
Look for clues in /var/log/cups.

---

### Post by Dennis N on 2013-04-26
I'm looking at the output I gave, and I am not a coder, but it looks to me like for cupsd to start avahi-daemon must be started first? Am I right or wrong?

---

### Post by tgalati4 on 2013-04-26
avahi simply advertises services--in this case shared printers.  It should not cause cupsd to fail.  CUPS does not have a direct dependecy but "recommends" avahi-daemon, which means it should be able to run without avahi-daemon.

If you are running 13.04, try the following:

```
sudo apt-get update
sudo apt-get upgrade
reboot
```

Then check your printers.

---

### Post by Dennis N on 2013-04-26
> **tgalati4 said:**
> Look for clues in /var/log/cups.

As to the cups log files, here is part of the error log, with output from a session earlier this afternoon:

```
W [26/Apr/2013:13:23:26 -0700] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:23:26 -0700] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:23:26 -0700] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
E [26/Apr/2013:13:38:54 -0700] [cups-driverd] Bad driver information file "/usr/share/cups/drv/cupsfilters.drv"!
W [26/Apr/2013:13:38:59 -0700] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:38:59 -0700] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:38:59 -0700] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:48:04 -0700] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:48:04 -0700] CreateProfile failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files
W [26/Apr/2013:13:48:04 -0700] CreateDevice failed: org.freedesktop.DBus.Error.ServiceUnknown:The name org.freedesktop.ColorManager was not provided by any .service files

```

Not sure these are that relevant to the cups-not-running problem - Lubuntu 12.10 on another computer shows similar errors (except for the bad driver information file line) and it prints normally.

Thanks for pointing out the logs.

---

### Post by Dennis N on 2013-04-26
> **tgalati4 said:**
> avahi simply advertises services--in this case shared printers.  It should not cause cupsd to fail.  CUPS does not have a direct dependecy but "recommends" avahi-daemon, which means it should be able to run without avahi-daemon.

If you are running 13.04, try the following:

```
sudo apt-get update
sudo apt-get upgrade
reboot
```

Then check your printers.

I already tried this earlier. No effect. 

Yes, cupsd does not need avahi-daemon, and can run without it, but from the structure of the code, it appears to me that cupsd will not start unless avahi-daemon has been started first. Am I wrong on that interpretation?

Next, I just found  that avahi-daemon is not installed with Lubuntu 13.04:

```
dn@Alexa:~$ apt-cache policy avahi-daemon
avahi-daemon:
  Installed: (none)
  Candidate: 0.6.31-1ubuntu3
  Version table:
     0.6.31-1ubuntu3 0
        500 http://us.archive.ubuntu.com/ubuntu/ raring/main i386 Packages

```

It's not installed on my Lubuntu 12.10 installation either, and Lubuntu 12.10 prints normally. But on 12.10, the cups.conf does not include any reference to avahi-daemon - here is the cups.conf from Lubuntu 12.10:

```
dn@Roxanne:~$ head /etc/init/cups.conf
# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

start on (filesystem
          and (started dbus or runlevel [2345]))
stop on runlevel [016]

respawn
```

I think I need to install avahi-daemon, or else change the code to remove reference to it.

Comment?

---

### Post by Dennis N on 2013-04-26
Well, I edited cups.conf and removed the line referring to avahi-daemon. I was correct - this was stopping cupsd from starting. Tested and confirmed this solution. Printing on Lubuntu 13.04 now works.

**Now, anyone who downloads and installs Lubuntu 13.04 from the same iso is going to be affected by the same problem.**

The iso is at:

[http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso)

and has a misconfigured cups.conf that will prevent the cups-daemon from starting unless fixed.

The corrected cups.conf begins:

```
# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

start on (filesystem
          and (started dbus or runlevel [2345]))
stop on runlevel [016]

respawn

```

Thanks to **Synoc** and **tgalati4** for your input.

---

### Post by ViniNITRO on 2013-04-30
thanks for the tip. Solved this issue for me too. :D

---

### Post by cherryredz on 2013-05-10
Another big thank you Dennis N, your solution worked a treat for me on Lubuntu 13.04.

:):)

---

### Post by tgalati4 on 2013-05-10
Why was *avahi-daemon* removed from Lubuntu?  I don't see any dependencies that preclude running it on Lubuntu?  Was it an issue of too big to fit on a CD?

---

### Post by Dennis N on 2013-05-10
> **tgalati4 said:**
> Why was *avahi-daemon* removed from Lubuntu?  I don't see any dependencies that preclude running it on Lubuntu?  Was it an issue of too big to fit on a CD?

That would be a question for the Lubuntu team to answer. It was not in the previous release (12.10) either, so we can't say it was removed in 13.04. Maybe it has never been in Lubuntu - that seems likely to me.

---

### Post by vasa1 on 2013-05-10
> **Dennis N said:**
> That would be a question for the Lubuntu team to answer. It was not in the previous release (12.10) either, so we can't say it was removed in 13.04. Maybe it has never been in Lubuntu - that seems likely to me.

Spooky!

Just after reading this post, I ran "dpkg --get-selections" and didn't see anything related to "avahi". Then, I did my daily update/dist-upgrade and saw this:
> Status Legend:
(OK):download completed.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  **avahi-daemon** libavahi-core7 libdaemon0 libnss-mdns
The following packages will be upgraded:
  cups cups-client cups-common cups-daemon cups-ppdc libcups2 libcupscgi1
  libcupsimage2 libcupsmime1 libcupsppdc1
10 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/2,179 kB of archives.
After this operation, 823 kB of additional disk space will be used.
Do you want to continue [Y/n]? y

This may also be of interest: [https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/1133794](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/1133794)
I came across it in the Lubuntu mailing list: [https://lists.ubuntu.com/archives/lubuntu-users/2013-May/004125.html](https://lists.ubuntu.com/archives/lubuntu-users/2013-May/004125.html)

---

### Post by DJBJ on 2013-05-28
Hi,

How did you actually edit the cups.conf file?  I am having the same problem with printing to PDF not working after a restart, but cannot work out or find out how to edit the cups.conf file.

I have copied the file elsewhere and edited it, but cannot do it in the /init folder.  I guess this is to do with permissions?

Thank you

---

### Post by Sachaweb on 2013-05-28
Did you mean cupsd.conf under /etc/cups ? (You wrote cups.conf)

After adding the code below and trying to save I got this message:

"Can't open file to write."

Does it have to do with running Lubuntu 13.04 from a USB stick?

I tried saving under a different name and also closing the printer interface, to no avail.

It is very, very difficult to get something printed with Lubuntu...

> **Dennis N said:**
> Well, I edited cups.conf and removed the line referring to avahi-daemon. I was correct - this was stopping cupsd from starting. Tested and confirmed this solution. Printing on Lubuntu 13.04 now works.

**Now, anyone who downloads and installs Lubuntu 13.04 from the same iso is going to be affected by the same problem.**

The iso is at:

[http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso](http://cdimage.ubuntu.com/lubuntu/releases/13.04/release/lubuntu-13.04-desktop-i386.iso)

and has a misconfigured cups.conf that will prevent the cups-daemon from starting unless fixed.

The corrected cups.conf begins:

```
# cups - CUPS Printing spooler and server

description     "CUPS printing spooler/server"
author          "Michael Sweet <msweet@apple.com>"

start on (filesystem
          and (started dbus or runlevel [2345]))
stop on runlevel [016]

respawn

```

Thanks to **Synoc** and **tgalati4** for your input.

---

### Post by Dennis N on 2013-05-28
> **Sachaweb said:**
> Did you mean cupsd.conf under /etc/cups ? (You wrote cups.conf).

No, you have the wrong file.
[B]
/etc/init/cups.conf[/B] is the file you want.

more: post #18

---

### Post by Dennis N on 2013-05-28
> **Sachaweb said:**
> 
After adding the code below and trying to save I got this message:
"Can't open file to write."
Does it have to do with running Lubuntu 13.04 from a USB stick?
I tried saving under a different name and also closing the printer interface, to no avail.
It is very, very difficult to get something printed with Lubuntu...


As to the rest  (above):

You cannot save a file in that location without using root privileges. Nothing to do with where Lubuntu is installed, usb or hdd.

**The fastest and easiest way to fix the file is to use the terminal:**

These steps should do it. Step 1 gets you into the right directory. Step 2 copies the file to your Desktop for safekeeping. Step 3 starts a terminal text editor and opens the cups.conf file to fix this thing - it will require your password. After these three commands, continue with the steps below them.

```
cd /etc/init
cp cups.conf ~/Desktop
sudo nano cups.conf
```[B]

Now to fix it:[/B]
Move cursor down to line 7, containing: **and started avahi-daemon**
Press **Ctrl+K** to delete line 7.
Press **Ctrl+O** (and confirm with Enter) to save the file.
Press **Ctrl+X** to quit editor.
Close the terminal. You are done.

you can abort the whole thing with Ctrl+X at any point before saving and start over.

Reboot the machine, and the printer setup and printing should work.

---

### Post by mlloyd on 2013-05-28
This seems to have fixed both of my machines with the problem. Thanks.

These are the 2 machines I just put 13.04 on as a new install, rather than an upgrade.

---

### Post by Dennis N on 2013-05-28
> **DJBJ said:**
> Hi,

How did you actually edit the cups.conf file?  I am having the same problem with printing to PDF not working after a restart, but cannot work out or find out how to edit the cups.conf file.

I have copied the file elsewhere and edited it, but cannot do it in the /init folder.  I guess this is to do with permissions?

Thank you

Please see Post #18.

---

### Post by DJBJ on 2013-05-29
All sorted!  Great stuff, thank you very much!

---

### Post by funfrank on 2013-06-14
thanks,this worked for me too.

Here are some extra directions for newbies (been there):

1) go to the command line (i.e. open accessories -> lxterminal)
2) type "sudo leafpad /etc/init/cups.conf"
this tells the machine to open the file cups.conf, which is located at /etc/init, with your default text editor "leafpad"
3) delete the line with the avahi daemon as indicated in the messages on the first page of this thread
4) save
5) reboot
6) print!

---

### Post by cmccullough on 2013-06-27
Strangest thing, I was experiencing this exact problem but had no reference to avahi-daemon anywhere in cups.conf. I added the reference, saved it, then removed it. Now, printing is working fine. :-)

---

### Post by ABMember on 2013-06-27
Thanks so much!  Your solution worked for me too.  I seriously doubt I could have figured that out on my own.

---

### Post by fixerdave on 2013-08-16
> **Dennis N said:**
> I'm looking at the output I gave, and I am not a coder, but it looks to me like for cupsd to start avahi-daemon must be started first? Am I right or wrong?

Thanks for this... figured I'd take the easy way out:
     **sudo apt-get install avahi-daemon**
and printing is now working.  Didn't even take a reboot.

David...

---

### Post by eyTkT7Y on 2013-08-17
> **Dennis N said:**
> Well, I edited cups.conf and removed the line referring to avahi-daemon. I was correct - this was stopping cupsd from starting. Tested and confirmed this solution. Printing on Lubuntu 13.04 now works.


Thanks Dennis! Great work. I had the same problem.

---

### Post by good-brian on 2013-09-19
Hi,

Just installed lubuntu 13.04 on my old Gateway-T-1620.  This was the only issue (listen for knocking on wood sounds .....  now) and thanks to this thread is fixed.  

Just wanted to say thanks and perhaps throw out an endorsement for lubuntu......

Cheers

---

