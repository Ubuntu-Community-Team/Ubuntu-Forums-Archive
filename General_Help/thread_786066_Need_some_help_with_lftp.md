---
title: "Need some help with lftp"
date: 2008-05-07
forum: General Help
---

### Post by Voorhees1979 on 2008-05-07
Hi There

I am having some problems getting lftp to download Directories. Single files is fine. When i try to get any full Directory ie:

get Amiga.Utils.A (Which is a directory)

i will get:

get: Access failed: 550 Amiga.Utils.A: not a plain file

Have tried many other ftp sites but I just cant get it to download a full folder only single files.

One other thing if anyone can help. lftp is setup as default to download stuff to my home folder, is there away to change this so it downloads to a different drive?

Many Many thanks for any help

Ta

---

### Post by Voorhees1979 on 2008-05-07
Ok I seem to have found the command it would be

mirror "directory name"

So one other question, what if I wanted to queue up more then one directory?

Thanks

---

### Post by Monicker on 2008-05-07
This should help:

[http://tutorials.papamike.ca/pub/lftp.html#queues]("http://tutorials.papamike.ca/pub/lftp.html#queues")

---

### Post by Voorhees1979 on 2008-05-07
That link is fantastic. Just what I needed.

Many Thanks

---

### Post by Voorhees1979 on 2008-05-08
Ok I do have one last question regarding this. I understand you can:

get -O /media/Disk/Downloads "file"
will download the "file" to my downloads, but

Queue stop
Queue mirror "directory1"
Queue mirror "Directory2"
queue start

will just send to my home folder :(

Mirror is a great cmd but with the mirror command you cant say where you want the directorys to go. Or am I missing something?

There must be away to use the mirror command and specify where you want the downloads to go.

Great cmd based ftp though, very impressed with it. Beats the gui's I have tried.

Many Thanks

EDIT

Ok its as simple as cd to the dir you want before downlaoding the file. Sorry I wasted a Thread.

Thanks

---

