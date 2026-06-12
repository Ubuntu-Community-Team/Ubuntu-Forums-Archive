---
title: "creating useful launchers"
date: 2007-04-28
forum: General Help
---

### Post by dhaus111 on 2007-04-28
Hey all,

I'm trying to figure out how to make scripts or launchers do my bidding.
basically I'd like to have an icon i can click on to run commands or more specifically lists of commands.  most of these would require sudo privileges.  One of the things I'd like to do is have a button "turn on" another X server which would use ssh and the -X switch to login to an X server on another computer on my LAN.

currently what I have to do to accomplish this is:

switch to tty2 and:
```
X :1
``` 
now this renders this tty stuck running 2nd x server

switch to tty1 and:
```
xterm -display :1
```
this opens up a terminal in the x server for me to execute the next command

```
ssh -X myuser@192.168.1.5
```
and then:
```
gnome-session
```

This sets up a fully functional remote gnome session on my 2nd xserver, which is pretty nice.  There are probably better ways to do this, but this is what I figured out, any improvements would be appreciated.

now for the purpose of this post, I'd like to know how to automate this into a single click of a script or launcher of sorts.  Is this possible? how would I configure my local gnome session to prompt me for passwords the way everything else does (with the pretty little password dialog).

thanks for reading, and hopefully...posting

---

