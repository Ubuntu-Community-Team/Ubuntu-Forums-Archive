---
title: "How to change blue firefox globe icon?"
date: 2007-02-27
forum: General Help
---

### Post by ahaurw01 on 2007-02-27
Hi there,
A while back I finally changed the launcher icon on my desktop from that simple blue globe to the traditional orange fox hugging the world. What I haven't been able to change, though, is the small blue globe icon that is in the very top left of the window (click and get minimize, maximize, etc.. menu) and the same icon in the window list on my panel. Does anybody know how to change these two icons? Thanks for your help.
Aaron

---

### Post by Quillz on 2007-02-27
Yes, it's an easy fix. Open up a Terminal session and type this:
```

wget -O mozilla-**firefox**.png [http://img105.echo.cx/img105/1515/](http://img105.echo.cx/img105/1515/)**firefox**rgb2oa.png
sudo dpkg-divert --divert /usr/lib/**firefox**/chrome/icons/default/default.xpm.old --rename /usr/lib/**firefox**/chrome/icons/default/default.xpm
sudo dpkg-divert --divert /usr/lib/**firefox**/icons/default.xpm.old --rename /usr/lib/**firefox**/icons/default.xpm
sudo dpkg-divert --divert /usr/share/pixmaps/mozilla-**firefox**.xpm.old --rename /usr/share/pixmaps/mozilla-**firefox**.xpm
sudo dpkg-divert --divert /usr/share/pixmaps/mozilla-**firefox**.png.old --rename /usr/share/pixmaps/mozilla-**firefox**.png
sudo dpkg-divert --divert /usr/share/pixmaps/**firefox**.png.old --rename /usr/share/pixmaps/**firefox**.png
sudo cp mozilla-**firefox**.png /usr/share/pixmaps/**firefox**.png
sudo cp mozilla-**firefox**.png /usr/share/pixmaps/mozilla-**firefox**.png
sudo cp mozilla-**firefox**.png /usr/share/pixmaps/mozilla-**firefox**.xpm
sudo cp mozilla-**firefox**.png /usr/lib/**firefox**/icons/default.xpm
sudo cp mozilla-**firefox**.png /usr/lib/**firefox**/chrome/icons/default/default.xpm
```
killall gnome-panel

---

### Post by ahaurw01 on 2007-02-27
Thank you so much for the help, Quillz. I couldn't for the life of me figure out where on my computer that blue icon was housed. 

Aaron

---

