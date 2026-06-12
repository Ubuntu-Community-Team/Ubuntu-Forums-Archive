---
title: "rtorrent - Move completed files (after download)?"
date: 2007-09-14
forum: General Help
---

### Post by sisco311 on 2007-09-14
Hi!

It is possible to configure rtorrent to move finished files to other directory? 

Thanks!

---

### Post by elev on 2008-02-24
these two sites helped me answer that same question and more!
[http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks]("http://libtorrent.rakshasa.no/wiki/RTorrentCommonTasks")
[http://www.linuxquestions.org/questions/linux-software-2/rtorrent-move-when-download-completes.-move-again-after-seeding-completes.-598556/]("http://www.linuxquestions.org/questions/linux-software-2/rtorrent-move-when-download-completes.-move-again-after-seeding-completes.-598556/")

---

### Post by tears.of.angels on 2008-03-24
could i maybe get some help here? i've googled like crazy and followed both of these links, but it seems like my command just goes unnoticed in my rtorrent.rc file

here's what i've got:

on_finished = move_complete,"execute=mv,-u,$d.get_base_path=,/home/andrew/torrents/seeding/ ;$d.set_directory=/home/andrew/torrents/seeding/"

should the path be relative? am i screwing up some syntax here? is something a comma that shouldn't be?

some help would be appreciated.

---

### Post by Hisstareia on 2008-06-12
Try taking out the -u argument, so the line looks like this:
> 
on_finished = move_complete,"execute=mv,$d.get_base_path=,$DIRECTORY;d.set_directory=$DIRECTORY"

Replace $DIRECTORY with whatever directory you want to save to when the download's complete

---

