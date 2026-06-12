---
title: "close rtorrent, but keep rtorrent running"
date: 2007-10-20
forum: General Help
---

### Post by pcit on 2007-10-20
Hello everyone,

I wander if I can close the rtorrent (ctrl+q) while there are some torrents still downloading.
Then, come back later to check my download status.

Right now, if I quit the rtorrent, it seems like kill the rtorrent process, so next time when I start the rtorrent, there is nothing left (not even the torrent file).

Thanks for the help~~

---

### Post by airtonix on 2007-11-09
open a terminal.

run : > screen

then youll be at a command prompt again. start up rtorrent like normally do

then just close the terminal window


to reconnect run 
> screen -l 

should list currently running  screen sessions.

> screen -r [screen-session-id]

will get you running in that session again, which will have rtorrent as your last open window.

you can create new windows in screen session by pressing ctrl-a, then c...for create.

this will put you at a blank command prompt. 

to get to other windows in current session, type ctrl-a n....for next...or ctrl-a [1-9] to access a window directly

---

### Post by JasonRivers on 2008-05-01
or run "screenie" which gives you a menu like this:

```

 SCREENIE - terminal screen-session handler
 written by Marc O. Gloor <mgloor@fhzh.ch>

 1) 12797.irssi
 2) 12936.rtorrent

 a) add job
 q) quit

 Use 'a' to add jobs or '1'-'2' to choose a currently running (screen)
 session. Once you're inside the (screen) session press 'CTRL-a d'
 to return to the session selection menu.

 select: 


```

then you just hit 1 for irssi (IRC client) or 2 for rtorrent.

Hold CTRL and hit "a" followed by "d" to desconnect from the screen and get back to the menu. :)

very useful this one.

J

---

