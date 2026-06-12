---
title: "headless bittorrent client recommedations"
date: 2008-03-30
forum: General Help
---

### Post by snoop2048 on 2008-03-30
HI, 

I have torrentflux running on a headless Ubuntu server, and whilst its been fine for the past 6 months, torrentflux lacks some of the functionality that I want. Can anyone recommend a client that meets the following spec?

1) Can be installed, configured & deployed via the command line
2) Can automatically download torrents from RSS streams based on text/regex filters 
3) Can be accessed and managed via HTTP
4) Can move completed torrents to another directory to downloading ones
5) Can set  a global upload cap, as well as per torrent upload cap
6) Runs on minimal resources
7) Protocol encryption would be a bonus,but is not essential.

I know azures happily does all of this via few plugins, and have considered it but I am concerned that the jvm will eat all the memory in the box (512mb). Torrentflux ticks along on minimal resources, and  I would like my new solution to do the same.

Thanks in advance for any input. :)

Simon

---

### Post by 505 on 2008-03-30
Take a look at rtorent, it's great. Although I believe the version in the repros is a bit outdated. You can often find newer version as deb packages in these forums or other sites.

As for your requests:
1. Command line only
2. No, the developer refused to implement this, however you can set a watch directory. All torrent files copied to that directory are started automaticaly. You would need another program to get, select and copy the torrent file. Makes much more sense IMHO.
3. Via a plugin on the web site
4. Via the rules in the config file
5. Yes
6. Very minimal
7. Yes

---

### Post by snoop2048 on 2008-03-30
Thanks for the input. I had come across rtorrent and it was one of the clients I was hoping would be able to do what I required. 

As per #2, i really hadn't considered using another program to pull the torrrents from the net, and the more i think the more it makes sense. Thanks! :) I shall be spending the rest of the day writing a script to parse the xml streams for my torrents. This way I have complete control over the pass and fail criteria for the strings. Why was this feature refused development? I think its one of the best features of torrent clients.

Simon

---

### Post by 505 on 2008-03-30
Apparently because the developer feels a torrent program should download torrent, and not be an RSS reader. It's a bit like the UNIX philosophy: "Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface."

A program dedicated to RSS will always be better than a torrent program that happens to do some RSS.

---

### Post by snoop2048 on 2008-03-30
I suppose that sort of makes sense. Either way the rtorrent site links to a few tools that will do exactly this. 

After some research it seems rtorrent will meet all my requirements, and for there is a wealth of information on the net on how to get it configured.

Thanks again!

---

