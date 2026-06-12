---
title: "Firefox + Flash - Only Few Sites Work"
date: 2008-05-30
forum: General Help
---

### Post by wagb278 on 2008-05-30
I have a problem with most sites that serve up video - only few work.  Those that don't only show the rotating "Loading" animation.

I am using:
  Ubuntu 8.04 64-Bit
  
  Firefox: Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9b5) Gecko/2008050509 Firefox/3.0b5
 
  Synaptic Package Manager shows the following loaded (I searched for "flash"):
      flashplugin-nonfree (installed version= 9.0.124.0ubuntu2)
      libswfdec-0.6-90 (installed version= 0.6.4-2)
      swfdec-mozilla (installed version= 0.6.0-2ubuntu1)

No "gnash" items are installed/enabled.

Can someone tell me if I need additional or different versions of these items?

Is there somewhere else I need to check; e.g.; Firefox applications?

Thanks!

---

### Post by abhiroopb on 2008-05-30
Can you give an example of a site that doesn't work? Then I can see if it works for me...

---

### Post by wagb278 on 2008-05-31
These are some sites that do not work for me:

[http://vids.myspace.com/](http://vids.myspace.com/)

[http://new.music.yahoo.com/videos/](http://new.music.yahoo.com/videos/)

[http://www.mtv.com/](http://www.mtv.com/)


This one does work - videos play

[http://video.google.com/](http://video.google.com/)
[http://www.theonion.com](http://www.theonion.com)
[http://www.nasa.gov/multimedia/videogallery](http://www.nasa.gov/multimedia/videogallery)

screencasts for Ubuntu work, both flash, and another low-res format

It appears that that "swfdec 0.6.0" is the "tool" that activates when Flash files are activated.  I thought I was using the shockwave Flash player.  Maybe that has something to do with my problem. 

Hope this helps

---

### Post by abhiroopb on 2008-05-31
The issue may be flash. Do the following in a terminal:

```

sudo apt-get update
sudo apt-get remove flashplugin-nonfree --purge
sudo apt-get install flashplugin-nonfree

```

---

### Post by wagb278 on 2008-05-31
> **abhiroopb said:**
> The issue may be flash. Do the following in a terminal:

```

sudo apt-get update
sudo apt-get remove flashplugin-nonfree --purge
sudo apt-get install flashplugin-nonfree

```

Thanks for the reply - I did as you suggested with no change in results.  Any other ideas?

---

### Post by isaacjoe on 2008-06-28
Maybe it has something to do with your using swfdec, the open source flash plugin, instead of the standard adobe one.

---

### Post by iaculallad on 2008-06-28
Had you tried using GNASH as your plugin instead of Adobe's flash to open those websites?

GNASH is available in the repo:

```
sudo apt-get install gnash
```

---

