---
title: "Reinstalling over an existing installation"
date: 2007-03-04
forum: General Help
---

### Post by Cloudy on 2007-03-04
So, I've come to the fact that my Ubuntu partition is growing increasingly bloated, I'm constantly having trouble with window managers and desktop environments, problems with my repositories, dependencies.. 

So I was wondering, is it possible to do a clean install over my existing Ubuntu partition? I have a 15 gb partition for Ubuntu on hd0,2 right now. If I pop in the Edgy Eft CD, can I reinstall over the partition in question?

The reason I ask is that I'm weary of uninstalling and reinstalling since I've got GRUB on the MBR (big mistake) and if I uninstall Ubuntu, would it be correct to assume I couldn't boot into XP and have to mess with teh MBR?

---

### Post by rsambuca on 2007-03-04
You will be safe.  You don't really have to uninstall anything though.  Just re-install in that same partition as if nothing was there prior.  Grub will be written to the MBR again as normal.

---

### Post by Cloudy on 2007-03-04
> **rsambuca said:**
> You will be safe.  You don't really have to uninstall anything though.  Just re-install in that same partition as if nothing was there prior.  Grub will be written to the MBR again as normal.

So just pop the CD in and reinstall to hd0,2? :)

---

### Post by Cloudy on 2007-03-04
Just being safe.. :

[http://img.photobucket.com/albums/v82/CloudStrife888/Screenshot-3.png](http://img.photobucket.com/albums/v82/CloudStrife888/Screenshot-3.png)

I'd choose the sda3 partition, right - seeing as that's where I currently have Ubuntu installed?

---

### Post by rsambuca on 2007-03-04
That is the one.  You should be good to go.

---

