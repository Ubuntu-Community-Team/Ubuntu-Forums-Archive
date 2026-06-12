---
title: "2 questions regarding rTorrent on Ubuntu Dapper LTS"
date: 2007-11-17
forum: General Help
---

### Post by stokedfish on 2007-11-17
Hello hello!    ;)

2 questions:

1) My seedbox is an Ubuntu Dapper 6.06 LTS server. Right now I'm using rtorrent/0.7.4/0.11.4, which works like a charme. Very happy with it. But I see there's a newer version. So I'm wondering...would it make sense to upgrade? I've read that some of the config stuff has changed and that I could run into problems. Also, there's prolly no *.deb for Ubuntu Dapper and I'd have to compile it myself...ugh. Maybe it's better to keep on using this version. Any advice?

2. So far I've created my torrents with Ktorrent and then seeded them with Rtorrent, which is kind of a weird setup. My Rtorrent is on 24/7 and my preferred client. Any way to create a torrent with it and go Rtorrent-only for releasing torrents?

Any help is appreciated!    :)

---

### Post by stokedfish on 2007-11-18
Anyone?   :(

---

### Post by mali2297 on 2007-11-18
> **stokedfish said:**
> 
1) My seedbox is an Ubuntu Dapper 6.06 LTS server. Right now I'm using rtorrent/0.7.4/0.11.4, which works like a charme. Very happy with it. But I see there's a newer version. So I'm wondering...would it make sense to upgrade? I've read that some of the config stuff has changed and that I could run into problems. Also, there's prolly no *.deb for Ubuntu Dapper and I'd have to compile it myself...ugh. Maybe it's better to keep on using this version. Any advice?

I think you have answered your own question. I have nothing to add.

> 
2. So far I've created my torrents with Ktorrent and then seeded them with Rtorrent, which is kind of a weird setup. My Rtorrent is on 24/7 and my preferred client. Any way to create a torrent with it and go Rtorrent-only for releasing torrents?

No, it isn't possible within rTorrent. But you could look for simple stand-alone applications. Here is one I found:
[http://www.createtorrent.com/](http://www.createtorrent.com/)

Just to check, I tried installing it. It was fairly easy. All you need to do before compiling is
```

sudo apt-get install build-essential checkinstall libssl-dev

```
Then follow the instructions..
> 
1. tar xzf createtorrent-version.tar.gz
2. cd createtorrent-version
3. ./configure
4. make

But finish off with
```

sudo checkinstall

```
instead off *make install*.

---

### Post by ellgor on 2007-11-19
Hi,

I'm a Dapper user myself and have tried various progs like ktorrent, azureus and others and have finally found one that is so easy to use and doesn't consume lots of memory in the process, it also creates torrents, the prog being Transmission. It is available from the Gnome site and the latest version is 0.93 should you give it a try, by the way the gui is pretty basic but its the job it does that counts.Hint, give this a shot but keep rtorrent on hold till you find a solution.

Regards, Ellgor.

---

