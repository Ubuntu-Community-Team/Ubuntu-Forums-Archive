---
title: "Need some help with deciding between Server or Desktop"
date: 2008-01-13
forum: General Help
---

### Post by thorlin on 2008-01-13
I'm looking to take an existing PC that I've got (P4 2.8 GHz, 1 GB RAM) and turn it into the home "server".  All my machines in the house, save this one, are Apples.  I want this "server" to be network store for files, pictures, music, etc.  I'll then want to setup this "server" to run backups of these crucial files to something like Amazon S3 or other online file backup, (I'll probably do this, maybe, or I may just buy a Drobo or other external drive solution).  I've used Ubuntu desktop in the past and been pleased.  I'm fairly technical, but I'm still a big novice when it comes to Linux.  Also, my wife is completely non-technical, so I've got to make this as easy as possible for her to store her files (almost all the photos, iMovie files, etc... for our family).  I'm looking to the experts on this forum to help me understand what I should install, Desktop or Server, and what the best configuration would be.

I thank you all in advance for your time in helping with this.

---

### Post by .nedberg on 2008-01-13
I did something similar a while ago.

I went with server, and installed kubuntu-desktop on it after install (I like KDE more than GNOME). I would recoment using XFCE though...

Just mount a folder from the server on your wifes computer (I use NFS for this, Samba is an other option). I don't use mac, but I am certain you will figure that part out.

Remote backup/sync? I am planning on placing a box at my parents with rsync on it...

---

### Post by twright on 2008-01-13
this should tell you everything you need to know:
[http://www.knightwise.com/content/view/300/9/](http://www.knightwise.com/content/view/300/9/)
[http://www.knightwise.com/podcasts/KC002.mp3](http://www.knightwise.com/podcasts/KC002.mp3)

---

### Post by Craigus on 2008-01-13
Have a look at FreeNAS.

Being BSD based, samba transfers are slow, but you will be using NFS with your apples, so this is not a problem. Very easy to use.

[http://www.freenas.org/]("http://www.freenas.org/")

---

