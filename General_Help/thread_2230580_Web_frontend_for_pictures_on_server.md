---
title: "Web frontend for pictures on server?"
date: 2014-06-20
forum: General Help
---

### Post by Roasted on 2014-06-20
Hello friends. Long story short, I really like Shotwell... but in this day and age, we store everything on a home server. Everything is pretty well automated and functions nicely, as we utilize Clementine's Subsonic internet plugin to stream music from the server over Subsonic, and music, pictures, and videos are served to the HTPC running Ubuntu 14.04/XBMC via SMB (Samba). Thing is, I feel like I could do a better job with serving up pictures if any system on the LAN wants to view them. Of course, opening the file manager yields a one-click way to auto mount the Samba link to pull up pictures on the server, but I can't help but to think there's a better way to 'serve' them than through the file manager. One thought is to just set up NFS and have it auto link to the pictures directory on the server and let Shotwell do its job, but I have some concerns about ~5 systems auto linking up to Shotwell like that. Maybe it'll work, but perhaps there's a reason I'm hesitant about it.

I got to thinking that with all of the magical softwares on the internets that perhaps something is out there that I'm missing. Maybe there's some sort of application I can install that'll tap into my existing Apache set up on the server where I can say, hey, pictures are in /media/storage/pictures, and boom - I'm presented with a sweet web frontend where I can browse through all of the pictures with a slick web UI. Maybe it doesn't exist, but it can't hurt to ask.

I do have ownCloud running on the server, and ownCloud has a really nice photo gallery. I've considered going that route, but I'm not too sure I can do that while retaining the capability to pull them up over Samba for the HTPC. I certainly don't have the space (nor do I care to even entertain this idea) of having the pictures in two locations, i.e. ownCloud data + its own folder hosted via Samba.

With that said, here I am blind firing. Anybody got any suggestions?

---

### Post by TheFu on 2014-06-20
Seems like you are using the best stuff for many things already.  I'd add Plex for the media and photos, then any DLNA client/renderer can be used to view any of the media and photos.

With Plex, I don't need to use CIFS anymore and my media center is an NFS server to other machines.  I use autofs to make the mounts automatic, but only when needed.

I don't use apache (nginx), but I do host a photo gallery online for family.  I use MyPhotoGallery (modified to add search, GPS, tags, etc). It stores metadata in a different directory structure, but access to the original files works (usually those are just too large to be viewed in a browser).  There are many photo gallery web-apps.  For inside the house, I prefer the Plex + DLNA renderer solution myself.  Love sending the photos to a projector or TV from any Android device (bubbleDLNA is the app).

CIFS and NFS have full file locking facilities. Don't worry about corruption too much.

---

### Post by SeijiSensei on 2014-06-20
You can certainly run a PHP gallery application and Samba together with a single collection of photos.

---

### Post by tgalati4 on 2014-06-20
[http://galleryproject.org/](http://galleryproject.org/)

---

### Post by SeijiSensei on 2014-06-20
> **tgalati4 said:**
> [http://galleryproject.org/](http://galleryproject.org/)

There's a posting dated just today on the front page of the Gallery site that says the project is going "into hibernation" because real life has intervened.

---

### Post by mirak-mirak on 2015-01-03
You might be interested by this [https://github.com/lwoggardner/shotwellfs](https://github.com/lwoggardner/shotwellfs)

It present the library of shotwell as a regular filesystem, ordered and sorted according to events, and I hope labels soon.
I tried it, it works fine and it is promising.

I intend to use it with DLNA with ushare.

---

