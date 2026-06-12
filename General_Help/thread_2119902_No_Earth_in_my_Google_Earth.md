---
title: "No Earth in my Google Earth"
date: 2013-02-25
forum: General Help
---

### Post by PocketDog on 2013-02-25
Odd problem I can live with but it's puzzling.
As you can see from the screenshot below I have no terrain in Google Earth. No land, no sea. This happened after installing XFCE and KDE for testing, and subsequently removing them. No idea how this could have borked Google Earth. I've tried purging G.E. and reinstalling.
Currently using Ubuntu 12.04, upgraded from 10.04 and 8.04 before that. G.E. was working on 12.04 Unity before trying other desktop environments. Won't work on any now. 
Any ideas or guesses on what I can try? Safe graphics mode does nothing. 

**[Screenshot](http://img805.imageshack.us/img805/1587/screenshotfrom201302250.png)**

---

### Post by dino99 on 2013-02-25
the new installed DE might have been removed some package(s) or broken some symlink(s)
try purging then reinstall GE

---

### Post by Impavidus on 2013-02-25
This seems to be a recurring problem. Try renaming the ~/.googleearth/ and ~/.settings/Google/ directories.

---

### Post by PocketDog on 2013-02-25
I ran ```
sudo apt-get purge google-earth-stable
``` and then ```
sudo apt-get autoremove
``` Then deleted the ~/.googleearth folder, all of which I've tried before.
I haven't got a ~/.settings folder so I created /.settings/Google and re-installed. 
Running google-earth from the terminal gives no errors, but I still have no terrain. Weird.

---

### Post by PocketDog on 2013-02-25
Just for info: 

The version I was using (7x) hadn't signed into the maps server and I hadn't noticed, and when I tried to sign in I got 'unknown protocol error.'
Going back to 6x via this link  [http://www.ubuntuupdates.org/package/google_earth/stable/main/base/google-earth-stable](http://www.ubuntuupdates.org/package/google_earth/stable/main/base/google-earth-stable) fixed it.

---

