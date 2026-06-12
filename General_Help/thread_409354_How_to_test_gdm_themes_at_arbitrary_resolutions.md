---
title: "How to test gdm themes at arbitrary resolutions?"
date: 2007-04-14
forum: General Help
---

### Post by newtonfn on 2007-04-14
I want to test some gdm themes at differents screen resolutions.
Reading the forum i found gdmthemetester and gdmflexiserver

Both works, but gdmthemetester hangs after the username and i can never see the password textbox.

On the other side, I could not figure out how to force a screen dimension with gdmflexiserver.

gdmflexiserver running with xnest seems to choose a resolution according my actual resolution, and running without xnest just use my own resolution. All i want is a xnest window with an arbitrary resolution/dimension.

---

### Post by parker13 on 2008-03-25
One way of doing this is to use the Xnest utility, which gives you an X session in a window on your current desktop:

Change your GDM settings to use the "themed" style for remote connections:

System->Administration->Login Window
Hit the "Remote" tab and change the "Style" to "Same as local".

Then, install Xnest:

```
sudo apt-get install xnest
```

You can now run Xnest to show the GDM screen at a specified resolution, eg:

```
Xnest :1 -query localhost -geometry 1024x768
```

or

```
Xnest :1 -query localhost -geometry 800x600
```

...etc.

Garry.

---

