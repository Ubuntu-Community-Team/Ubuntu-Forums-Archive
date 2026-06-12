---
title: "Plex install on ubuntu server 12.04 command line"
date: 2014-01-29
forum: General Help
---

### Post by mark103 on 2014-01-29
Hi all, im a noob linux user so i just have a few questions to ask about installing plex on my Ubuntu 12.04 server 

I have been searching online for tutorials to do this and found one or two, now normally I don't really post unless I have to as I prefer to solve problems myself and do a lot of research but i'm stuck badly on this.

I tried to install plex but the .deb packages I was finding online wouldn't work for me and im still confused on how u get them of the plex site and put in the command line to download anyway 
I found this link [http://www.makeuseof.com/pages/plex-a-manual-your-media-with-style#chapter-2](http://www.makeuseof.com/pages/plex-a-manual-your-media-with-style#chapter-2) 
with instructions to show me and I had to edit this file ```
sudo nano /etc/apt/sources.list
``` 
and add this link deb [http://www.plexapp.com/repo](http://www.plexapp.com/repo) lucid main and then save it and do 
sudo apt-get update and it would update 

but the problem is it looks for files but won't install them and this is where I am really lost and need a help out of anybody if possible I would really appreciate it 

Thanks

---

### Post by mark103 on 2014-01-29
i got it working

---

### Post by Dods on 2014-05-12
Hi mark103,

And how have you done it!

I have found a nice link. For others who's looking for more How to's.
It's [http://www.geeklee.co.uk/headless-plex-media-server-on-hp-microserver/](http://www.geeklee.co.uk/headless-plex-media-server-on-hp-microserver/)

---

