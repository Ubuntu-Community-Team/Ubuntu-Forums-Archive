---
title: "chmod shell script: running from XFCE locks up PC"
date: 2008-03-03
forum: General Help
---

### Post by thaddicus on 2008-03-03
Greetings,

I'm currently running Ubuntu Server (7.10) w/ XFCE4.  I created a shell script for a frequently-used set of commands and ran chmod against it to make it executable.  Here's my problem... everytime I double-click the script from the desktop it locks up the PC.  Not quite sure why this happens.

I know in Gnome theres an option in properties to make the shell script executable; which basically eliminates the need for chmod.  But I'm new to XFCE so I don't know if the procedure is different.  Any insight would be appreciated.  Thanks.

---

### Post by bodhi.zazen on 2008-03-03
Could be any number of problems, I suggest you run the script in a terminal and see if there are any errors.

---

### Post by thaddicus on 2008-03-19
Thanks for the direction.  I ran sh in the console and it appears that I had an issue with one of my conf files.  I've since adjusted and it works now.

---

