---
title: "KDM Assistance Needed"
date: 2008-06-04
forum: General Help
---

### Post by Vince4Amy on 2008-06-04
I have to set my MTU on my network device to 1492. On Gnome I would do this by adding ```
ifconfig eth0 mtu 1492
``` to /etc/gdm/PreSession/Default.

How can I add this to by ran on startup on KDE. Obviously there is no /etc/gdm/PreSession/Default so what is the alternative for KDE?

---

### Post by Zorael on 2008-06-04
edit: You can modify your [FONT="Courier New"]/etc/network/interfaces[/FONT] file to set MTU for you automatically.
```
   The static Method
       This  method  may be used to define ethernet interfaces with statically
       allocated IPv4 addresses.

       Options

              address address
                     Address (dotted quad) required

              netmask netmask
                     Netmask (dotted quad) required

              broadcast broadcast_address
                     Broadcast address (dotted quad)

              network network_address
                     Network address (dotted quad) required for 2.0.x kernels

              metric metric
                     Routing metric for default gateway (integer)

              gateway address
                     Default gateway (dotted quad)

              pointopoint address
                     Address of  other  end  point  (dotted  quad).  Note  the
                     spelling of "point-to".

              media type
                     Medium type, driver dependent

              hwaddress class address
                     Hardware  Address. class is one of ether, ax25, ARCnet or
                     netrom. address is dependent on the above choice.

              [B]mtu size
                     MTU size[/B]
```



If you want it run after login, create an executable script and place it in [FONT="Courier New"]~/.kde/Autostart/[/FONT]. That's the default directory, unless you've changed it under System Settings -> About Me -> Paths.

From the man page of startkde:
```
       startkde,  with ksmserver, is a standard X11R6 session manager that can
       manage any X11R6 SM compliant program.

       startkde and ksmserver use the contents of  the  ~/.kde  directory  for
       starting   previously   saved   sessions.   Source   scripts  found  in
       ~/.kde/env/*.sh can be used to define environment variables  that  will
       be available to all KDE programs.

       For  anything  else  (that doesn’t set env vars, or that needs a window
       manager), better use the ~/.kde/Autostart folder.

       At the end of a session, the scripts found in ~/.kde/shutdown  will  be
       executed.
```

If you want it run before login, I'd put it in [FONT="Courier New"]/etc/rc.local[/FONT], *before* the '**exit 0**' line.

---

