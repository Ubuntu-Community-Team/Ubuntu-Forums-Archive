---
title: "rtorrent"
date: 2007-09-04
forum: General Help
---

### Post by ewloe on 2007-09-04
I am having major problems with torrent clients, AZ won't start just closes after the splash screen, ktorrent and deluge and also bit tornado and bit torrent are banned from the tracker I am using. 

I have downloaded and installed  rtorrent using synaptic package manager but cant get it to run its not in the applications drop down menu, I have browsed to it when trying to open a torrent file but still it wont start. I tried sudo rtorrent in terminal and something seemed to happen but did not know how to work it, I tried dragging the file in but that did not work either.

I am in danger of losing my account with the tracker if i don't sort this soon.

thanks in advance

ps deluge is working fine for other trackers but not the one I need to use urgently

---

### Post by SOULRiDER on 2007-09-04
rTorrent is a console app.

Open a console and type
```
rtorrent
```

Once its opened press backspace and tyoe the path to the torrent file. It will be automatically started and hashed. To stop press ctrl + D and to remove it ctrl + D twice. To start/resume ctrl + s

For more info you should do
```
man rtorrent
```

---

### Post by bjarneh on 2007-09-04
it has an ncurses frontend, no drag and drop there, try out  'vim'  or some other ncurses program and you'll soon see how much more fun stuff where in the old day :-)

---

### Post by yabbadabbadont on 2007-09-04
You don't need to run it with sudo.  You just need to configure it and then run it in a terminal window.  The simplest way to start, is to copy /usr/share/doc/rtorrent/examples/rtorrent.rc to ~/.rtorrent.rc and then edit it to fit your needs.  It is well commented and the complete user guide can be found here:
[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)

Edit: Too slow, but no one else posted the link to the user guide, so I get brownie points...  :D

---

### Post by ewloe on 2007-09-05
thanks for all the replies but i managed to get utorrent to work under wine so for now I will stick with a program I know how to use, but i know I have this info as back up should I decide to use rtorrent in the future.:)

---

### Post by olavjunior on 2007-09-07
Earlier I used utorrent, but now I've taken the time to learn rtorrent, and it's just great! Uses no resources at all even with hundreds of torrents and a lot of activity :) I'm very satisfied!:popcorn:

---

