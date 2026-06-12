---
title: "&quot;No serving hosts were found&quot;"
date: 2006-09-05
forum: General Help
---

### Post by scuz on 2006-09-05
This just started happening after coming back from a small trip. Computer boots as normal, then right before it would start displaying the login window(has the "thinking" mouse icon) it pops up this winding which says "No serving hosts were found." with a place to add host, help/refresh/cancel/connect buttons.

I'm guessing its a problem with connecting to the X server, I didn't see any error messages though.

Any ideas at all? I can provide more specific computer details if needed.

---

### Post by CUNY on 2006-09-28
I have exactly the same problem! Please could someone help ne I'm a total linux newbie!!!](*,) 

Thank you very much!:???:

---

### Post by Brendanw2 on 2007-06-12
Alas I Too have the same problem, only I inadvertantly made it happen.  Yes it is on the XSERVER and it is associated with log in type. I am trying differant things ...so far nothing helpfull . I have tried the following
Sudo-dpkg-reconfigure xserver.........
dpkg-reconfigure gdm..........

---

### Post by Major Newb on 2007-06-27
I admit it. I went in to Login Screen in the Admin area and set it to "Choose". Now what? :redface:

---

### Post by JDNeeves on 2007-08-17
Hi Guys,

I've just fixed this on my system.
I'm running Debian V4.0 with gnome. 

use ctrl-alt-F1 to get a terminal login, or in some other way.

edit file /etc/gdm/gdm.conf
in the [server-Standard] section 
comment-out the line
chooser=true
put a # at the start of the line to comment it out.
you'll probably have to reboot after this. 

Yes, it's a pain. Took a while to fugure it out. 

Hope this is helpful. Let me know.

All the best, from J.
[www.jdnsystems.co.uk](www.jdnsystems.co.uk)

---

### Post by Pinger05 on 2007-09-05
UPDATE FOR FIESTY

Make this work in Fiesty you need to change something.  Insted of modifying /etc/gdm/gdm.conf you will need to modify:

```
/etc/gdm/gdm.conf-custom
```

As JDNeeves said all you need to do is comment out the 

```
cusom=true
```

and it works.  Thank you JDNeeves for the directions!!:KS

---

### Post by bhavi on 2008-04-08
What to do in gutsy?

---

### Post by mfregeau on 2008-05-31
> **JDNeeves said:**
> Hi Guys,

I've just fixed this on my system.
I'm running Debian V4.0 with gnome. 

use ctrl-alt-F1 to get a terminal login, or in some other way.

edit file /etc/gdm/gdm.conf
in the [server-Standard] section 
comment-out the line
chooser=true
put a # at the start of the line to comment it out.
you'll probably have to reboot after this. 

Yes, it's a pain. Took a while to fugure it out. 

Hope this is helpful. Let me know.

All the best, from J.
[www.jdnsystems.co.uk](www.jdnsystems.co.uk)
there are no "chooser=true" line under my [server-Standard] section, all I got is this:

[server-Standard]
name=Standard server
command=/usr/bin/X -br -audit 0
flexible=true

should I just comment everyting then?

---

### Post by mfregeau on 2008-05-31
nice, thanks! (in english, it will be "chooser" not "cusom").

---

