---
title: "Need help with Rtorrent and rssdler"
date: 2008-04-23
forum: General Help
---

### Post by Fredrik_b on 2008-04-23
I´v gott rtorrent and rssdler upp and running but I am missing an importand part. How do I get the files from the torrents to be downloaded to a specific catalog?

[The paper]
link = [http://tvrss.net/feed/eztv/](http://tvrss.net/feed/eztv/)
maxSize = 40000
minSize = 0
directory = /media/testa/tv/the_paper
regextrue = (medium)
regexfalse = (hr|720|1080|ntsc|x264|sct)
nosave = False

In this example the .torrent gets downloaded to "/media/testa/tv/the_paper" but this in not what I want. I want the data to be downloaded here.

How shall a correct setup look?

---

### Post by markharding557 on 2008-05-05
can't you just change the download location.
i find deludge is very good

---

### Post by mushroomblue on 2008-10-02
> **Fredrik_b said:**
> I´v gott rtorrent and rssdler upp and running but I am missing an importand part. How do I get the files from the torrents to be downloaded to a specific catalog?

[The paper]
link = [http://tvrss.net/feed/eztv/](http://tvrss.net/feed/eztv/)
maxSize = 40000
minSize = 0
directory = /media/testa/tv/the_paper
regextrue = (medium)
regexfalse = (hr|720|1080|ntsc|x264|sct)
nosave = False

In this example the .torrent gets downloaded to "/media/testa/tv/the_paper" but this in not what I want. I want the data to be downloaded here.

How shall a correct setup look?


you need to change the directory above to where you want the torrents saved. all rssdler does is download to that directory. if you have torrents there, the app is doing it's job properly.

now you have to set up rtorrent to monitor that directory, and automatically download new torrents from it. use [this link]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks") to figure out what you need to do. configure the directories to watch, download to, and move files once finished (which makes life easier).

---

