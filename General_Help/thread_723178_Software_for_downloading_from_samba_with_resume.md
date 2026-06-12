---
title: "Software for downloading from samba with resume"
date: 2008-03-13
forum: General Help
---

### Post by cyrus_the_virus on 2008-03-13
Hi,

I need to be able to download large files via samba. The samba network is over a VPN connection which unfortunately isn't very reliable. The connection drops every now and then for some reason.

Therefore it would be nice to have some software which is able to download via samba and supports resume. In windows I used to use a program called ReGet which I tried to run under wine but didn't really work.

Any suggestions? 

Thanks,
Marty

---

### Post by Cadmus on 2008-03-13
Hmm, have you tried using [rsync]("http://www.samba.org/rsync/")? It's a bit of a pain to get it to do exactly what you want but I've had some success using it over samba and a vpn.

---

### Post by cyrus_the_virus on 2008-03-13
Thanks for your reply

I have heard of sync but haven't actually used it for this purpose. Can it directly work with samba or should I mount a samba share and then use rsync for copying?

Marty

---

### Post by Cadmus on 2008-03-13
I'm pretty sure you have to mount it, though I'm willing to be proved wrong.

---

### Post by Cadmus on 2008-03-13
Just done a bit of checking with cygwin to my Feisty box at home.

Speeds are as fast as doing it direct from rsync (using the username and password of the samaba owner) but I had to cd into the samba directory first, I seem to remember rsync doesn't recognise unc paths (//myserver/data/)

---

### Post by cyrus_the_virus on 2008-03-13
Thanks. I've got it working pretty well. This is what I've done:

- First I mount the network drive with:
*mount.cifs //network/drive /mount_path/bla *
The first path is the networkdrive, the second the where to mount it locally

- I then start rsync with this command
*rsync  -av --progress --partial /mount_path/bla /path/for/downloaded/files*
*Progress* shows a progress percenage during download, *partial* makes resume possible, the first path is the path where to copy from (in my case the mounted samba drive) and second path the destination for the downloaded files.
Marty

---

### Post by Cadmus on 2008-03-13
Glad to hear it's working, if you need it to resume unattended look into writing a script that runs rsync, then checks the exit code of the program to make sure nothing went wrong during the progress and keeps trying, it'd probably look like this (assumes you have the samba share mounted already)

```
#!/bin/bash

#First, run the rsync by itself
rsync -av --progress --partial /mount_path/bla /path/for/downloaded/files

#now enter a loop if it didn't finish properly
until [ $? = 0 ]
do
  rsync -av --progress --partial /mount_path/bla /path/for/downloaded/files
done
exit
```

---

### Post by cyrus_the_virus on 2008-03-13
Thanks :D That nice, I will definitely use that.

Marty.

---

### Post by Cadmus on 2008-03-13
I wrote that in 3 mins, and I've had a bit of ale now so I'm not sure if it's totally right, but it's nearly there.

Anyone know if there's a while-like construct for bash that guarantees the loop body will execute at least once? My solution looks inelegant to me.

---

