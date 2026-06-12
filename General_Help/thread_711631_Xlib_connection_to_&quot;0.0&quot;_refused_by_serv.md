---
title: "Xlib: connection to &quot;:0.0&quot; refused by server"
date: 2008-02-29
forum: General Help
---

### Post by slim99 on 2008-02-29
I am trying to install an application on a virtual machine (ubuntu 7.10 running in VMware on Windows XP) and getting errors trying to run a script called wrf_tools which is supposed to open a GUI:

root@baersys:/home/admin/DRJACK/WRF/wrfsi# cat /tmp/wrf_tools.log 
Xlib: connection to ":0.0" refused by server 
Xlib: No protocol specified
couldn't connect to display ":0.0" at /usr/lib/perl5/Tk/MainWindow.pm line 55.  
MainWindow->new(-bg,#d9d9d9) at /home/admin/DRJACK/WRF/wrfsi/gui/guiTk/ui_system_tools.pl line 177

Several people report similar problems in Debian, eg: [http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg119740.html](http://www.mail-archive.com/debian-bugs-rc@lists.debian.org/msg119740.html) and state that this is due to bad X11 environment with Perl Tk installed.  This is entirely possible as I am not at all familiar with the X Windows environment as usually work from the command line.  In fact I installed ubuntu 7.10 and then installed KDE later but it certainly seems that the X environment is OK as KDE runs fine. 

But tried to run this command suggested in similar threads and got no result:

root@baersys:/# xlsclients | wc -l
xlsclients:  unable to open display ""
0

and also tried :

root@baersys:/home/admin/DRJACK/WRF/wrfsi# xhost -
xhost:  unable to open display ""

 Any suggestions folks? Thanks in advance..........  Bernie.

---

### Post by SpaceTeddy on 2008-03-01
since you are running on an ubuntu, i think you need to run the command xhost command as the user that started the x-server. i.e. as the one you are logged in as, not as root...

also, to allow connectons to an xserver, i think you need to run 
> xhost +
to allow anyone to connect to it... not sure here, really.

Hope it helps :)

---

### Post by slim99 on 2008-03-01
Hi SpaceTeddy, that was it.
Once I ran the script as non-root user, it opened up straight away.
Haven't tried the 'xhost +' comand yet, but will do.
Thanks,  Bernie.

---

### Post by astrotech226 on 2008-03-01
You don't want to run "xhost +" is you don't have to.  It allows absolutely anyone to your display.

If what you are doing is local, try this instead.  It allows any non-network connection to the display:
```

xhost local:root
```

---

### Post by slim99 on 2008-03-01
thanks astrotech226, that works nicely.

---

### Post by SpaceTeddy on 2008-03-02
> **astrotech226 said:**
> You don't want to run "xhost +" is you don't have to.  It allows absolutely anyone to your display.


ups, you're right astrotech... my bad, sorry for not thinking of that. :)

---

