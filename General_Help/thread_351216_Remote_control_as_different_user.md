---
title: "Remote control as different user"
date: 2007-02-01
forum: General Help
---

### Post by anabelle on 2007-02-01
Hi, I have two PCs at home, both running Kubuntu 6.10 and i want to remote control the other PC.

I've done it with krdc but it only lets me control the active session. How can i have one user logged in and working on one PC and simultaneously Remote control it as a different user from the other PC?

---

### Post by bodhi.zazen on 2007-02-01
ssh into the box.

[How to ssh](https://help.ubuntu.com/community/SSHHowtol)

---

### Post by glabouni on 2007-02-01
xdmcp

[http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP](http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP)

---

### Post by anabelle on 2007-02-01
Ok, i looked at [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto) and i managed to login to my other PC trough the konsole, but i couldn't control the other PC remotly... how can i do this? 


I also looked at [http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP](http://wiki.ltsp.org/twiki/bin/view/Ltsp/XDMCP) and i didn't understand what it had to do with my question...:confused:

---

### Post by bodhi.zazen on 2007-02-01
What is it you want to control?

You can forward X via ssh and get a desktop.

You can do most anything from the command line.

XDMCP also allows a remote log in.

---

### Post by anabelle on 2007-02-25
Ok.. so i did it :D im running Firefoxin my other pc now, but something funny is happening, when i watch some video or listen to music.. the sound comes out from my other PC's speakers, is there a way to tunnel sound also? cause its annoying for the user in the other PC an for me because i can't listen....

How?

---

### Post by bodhi.zazen on 2007-02-25
LOL, I'd like to see a solution to that one as well ,,,

---

