---
title: "Icon theme causes aplication crash?"
date: 2006-12-09
forum: General Help
---

### Post by yer on 2006-12-09
I have found through the process of elimination that if i use  any custom icon theme for gnome, Azureus will not open. It starts up, displays the main azureus window for a second, and then crashes. I am wondering if there is a way to launch an aplication in gnome but tell it to ignore the theme, or at least the icon theme. Does anyone know of a way to do that?

thanks

---

### Post by yer on 2006-12-09
I know this sounds crazy, but seriously, if i change the icon theme to the default theme azureus works just fine. but if i use a custom theme it just crashes without any usefull output.

---

### Post by bulldog on 2006-12-09
Maybe you can set Azureus to use it's own theme and not the desktop theme?

I know it can be done with frostwire.

---

### Post by yer on 2006-12-12
> **bulldog said:**
> Maybe you can set Azureus to use it's own theme and not the desktop theme?

I know it can be done with frostwire.

Azureus does not have that option. However I did fix this problem by running Azureus from the script in the installation directory rather than the script /usr/bin/azureus. I just changed the script ( it was full of fun stuff that I didnt understand ) to read:
 ```

#!/bin/sh
cd /opt/azureus
./azureus

```instead of whatever the .deb package left there. That change also made the plugins work.
 This is a good fix although I could not find anyone else that had this issue. maybe we can get this thread put in the tips and tricks or howto section?

thanks for replying

---

### Post by yer on 2006-12-13
a side effect of my fix was that I can no longer drag and drop .torrent files into azareus nor can i click on a torrent in firefox and have it open in azareus. I'm going to try to rewrite the original script to omit icon themes but retain gnome compatability. I will post my sucsess/failure.

---

### Post by coder_ on 2006-12-13
For some reason I had this too but kind of the opposite (And a tad different).

Rythmbox, the icon selector, and GIMP will NOT run with Human themed controls for some reason in Gnome in 64 Bit Dapper.  I found no way to fix it though (But I use Edgy and it works now).

Which reminds me, I need to update my profile to say I run Edgy! :)  And a proud Beryl user too :)

---

### Post by yer on 2006-12-14
Solved. added an entry to /etc/mailcap : 
```
# ----- User Section Begins ----- #
application/x-bittorrent; /opt/azureus/azureus
# -----  User Section Ends  ----- #
```as described in this thread: 
[http://ubuntuforums.org/showthread.php?t=144546](http://ubuntuforums.org/showthread.php?t=144546)

so just to clairify, i run azureus with /opt/azureus/azureus, and bittorrent mimetype is associated with azureus so that i can click on a .torrent in firefox, and it will open correctly in azureus. also, themes work, becuase i am not using the script /usr/bin/azureus. i still do not know why the icon theme broke that script, because i am not familiar with java.
If someone would like a nicely formatted howto, I will glady type one up, just ask.

---

