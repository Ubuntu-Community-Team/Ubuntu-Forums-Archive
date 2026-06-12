---
title: "[SOLVED] Text based torrent client availible through apt-get"
date: 2007-12-01
forum: General Help
---

### Post by TidusBlade on 2007-12-01
Does anybody know any torrent client that can run in the terminal, and is available through apt-get?
I would really appreciate it if anyone could tell me anything :) 
It would also help if it is in the Dapper apt-get list.

---

### Post by llamakc on 2007-12-01
The regular 'bittorrent' package has a curses-based client, and also a headless one.

---

### Post by TidusBlade on 2007-12-01
That sounds good enough, any idea what command I gotta use to get it?

---

### Post by bingoUV on 2007-12-01
You can try rtorrent too.

---

### Post by TidusBlade on 2007-12-01
Yeah I was trying it, but it dosen't compile, and I wasent in the mood to start fixing things xD So I came here to ask :)

---

### Post by llamakc on 2007-12-01
sudo apt-get install bittorrent

---

### Post by TidusBlade on 2007-12-01
Oh, thought the curses one had a different install, thanks anyways :D

---

### Post by llamakc on 2007-12-01
...And you'll run it with:

```

btdownloadcurses NAMEOF.torrent

```

---

### Post by TidusBlade on 2007-12-01
Oh, thanks alot for that command! I was puzzled since it had no man bittorrent.

---

### Post by llamakc on 2007-12-01
In the absence of a man page, you can check for the documentation in

/usr/share/doc/NAMEOFPACKAGE

or in this case

/usr/share/doc/bittorrent

which has this as its contents:

```

ken@llamakc 10:14:38:/usr/share/doc/bittorrent$ ls
bittorrent_logo.png  documentation.html  FAQ.html           press.html
changelog.Debian.gz  donate.html         guide.html         protocol.html
copyright            download.html       index.html         README.Debian
credits.txt          examples            introduction.html  README.txt.gz

```

---

### Post by mellowd on 2007-12-01
rtorrent is by far the best once you get rtorrent.rc edited. It uses almost 0 resources on my server.


```
apt-get install rtorrent
```

---

### Post by CatKiller on 2007-12-01
Actually, even better is ```
screen btdownloadcurses NAMEOF.torrent
``` if you have more than one computer - say, with some kind of server machine - since then you can connect remotely to the server, start a torrent, detach from the server and turn the client off with the torrent still downloading. Then, at some point later you can re-attach to the running download and check it/stop it. Very cool.

---

### Post by TidusBlade on 2007-12-01
I am currently using bittorrent, but I tried rtorrent again, but cannot find the rtorrent.rc file anywhere, so if you can tell me I would love it :)
And thanks llamakc, ill be sure to check those man pages :D
@Catkiller: Ill try it with the screen on my next download ;)

---

### Post by CatKiller on 2007-12-01
> **TidusBlade said:**
> Yeah I was trying it, but it dosen't compile, 

Actually, it's in the Universe repository.

---

### Post by alphane on 2007-12-01
+1 for rTorrent.

rtorrentrc needs to be created, default examples can be found here: [http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest")

stick it in your home folder

---

### Post by llamakc on 2007-12-01
> **CatKiller said:**
> Actually, even better is ```
screen btdownloadcurses NAMEOF.torrent
``` if you have more than one computer - say, with some kind of server machine - since then you can connect remotely to the server, start a torrent, detach from the server and turn the client off with the torrent still downloading. Then, at some point later you can re-attach to the running download and check it/stop it. Very cool.

screen works great for those situations, but you can also do this (which negates the need for screen):

```

nohup btdownloadheadless nameof.torrent &

```

And a "nohup.out" file is created. You can `tail -f` that to check on the process. This way you can logout and log back in, checking on the status of the torrent with

```

tail -f nohup.out

```

PS: One would need to be in the directory with nohup.out or provide the full path.

---

### Post by TidusBlade on 2007-12-01
> **alphane said:**
> +1 for rTorrent.

rtorrentrc needs to be created, default examples can be found here: [http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest]("http://libtorrent.rakshasa.no/browser/trunk/rtorrent/doc/rtorrent.rc?rev=latest")

stick it in your home folder
Thanks for pointing that out :) Hopefully, I can start downloading from private trackers now!

---

### Post by mellowd on 2007-12-01
[QUOTE=CatKiller] if you have more than one computer - say, with some kind of server machine - since then you can connect remotely to the server, start a torrent, detach from the server and turn the client off with the torrent still downloading. Then, at some point later you can re-attach to the running download and check it/stop it. Very cool[/QUOTE]

I do this with rtorrent as well.

```
screen rtorrent

ctrl+a d
```

Then when I get home

```
screen -x
```

You can use screen to do this with any terminal application - [http://mellowd.co.uk/test2/index.php?m=12&y=07&entry=entry071201-063218](http://mellowd.co.uk/test2/index.php?m=12&y=07&entry=entry071201-063218)

---

### Post by CatKiller on 2007-12-01
> **mellowd said:**
> You can use screen to do this with any terminal application

Indeed. screen is one of my favourite things.

Which possibly makes me rather sad.

---

### Post by mellowd on 2007-12-01
> **CatKiller said:**
> Indeed. screen is one of my favourite things.

Which possibly makes me rather sad.

hehe, it really is a useful app. especially since I'm always doing things at home here or at work on my server.

I suppose that makes me even more sad

---

