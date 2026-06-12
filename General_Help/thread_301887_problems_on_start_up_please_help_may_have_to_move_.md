---
title: "problems on start up please help may have to move back to windows"
date: 2006-11-17
forum: General Help
---

### Post by cptjaben on 2006-11-17
When I restarted my computer after following this guide, I got the message :

Init: Unable to execute "/bin/sh" for RcS: too many levels of symbolic links
Init: RcS process(1999) terminated with status 1

Init: Unable to execute "/bin/sh" for rc-defeault: too many levels of symbolic links
Init: rc-defeault process(2000) terminated with status 1

Basically I started following method 2 and stopped here at the Create .deb packages because my computer gave me a message saying something about

bash ati-driver-installer-8.30.3.run --buildpkg Ubuntu/edgy having too many symbolic links.

does anyone have any ideas on how one might get around this? orr suggestions on what to do?

---

### Post by greeklegend on 2006-11-17
I don't think this'd be recommended, but what happens if you do...
```

sudo -i
rm /bin/sh
cp /bin/bash /bin/sh

```

---

### Post by cptjaben on 2006-11-18
when i tried 

```
sudo -i
rm /bin/sh
cp /bin/bash /bin/sh
```

it didn't really do anything, i could type stuff as though i was in a terminal but it wasn't excuting anything. It looks like the problem is that this script that wasn't finished is getting run on startup, Is there a way I could somehow delete it using a live cd and broswing for it on my harddrive or something?

---

### Post by deanlinkous on 2006-11-19
could fool around with a liveCD...not sure what all you need to clean up though.

So after you get those messages the computer stops dead or what? Can't get past them?

---

