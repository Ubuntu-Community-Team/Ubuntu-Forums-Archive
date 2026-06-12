---
title: "Updating Flash In Chromium"
date: 2014-08-09
forum: General Help
---

### Post by daniell59 on 2014-08-09
I can no longer view videos in Chromium. When I attempt to do so, it says that I need to update the Flash. I would appreciate it if someone would explain to me how it is done. Ubuntu 12.04 64

Thank you

---

### Post by fizikz on 2014-08-09
Try following the instructions (by saiarcot895) to install the pepper flash plugin [here]("http://askubuntu.com/questions/449103/chromium-34-cant-detect-flash-plugin").

---

### Post by daniell59 on 2014-08-10
I would appreciate it if someone could help me expedite the following. I shamefully admit that I should know more.

Note that you need to configure Chromium to use Pepper Flash. To do this, open /etc/chromium-browser/default and add the following line to the end of the file on a new line:

. /usr/lib/pepflashplugin-installer/pepflashplayer.sh

---

### Post by fizikz on 2014-08-10
In a terminal type (or copy/paste):

```
gksudo gedit /etc/chromium-browser/default
```

and then copy the following on a new line:

```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```

then save and close gedit. 

See if that helps.

---

### Post by daniell59 on 2014-08-10
> **fizikz said:**
> In a terminal type (or copy/paste):

```
gksudo gedit /etc/chromium-browser/default
```

and then copy the following on a new line:

```
. /usr/lib/pepflashplugin-installer/pepflashplayer.sh
```

then save and close gedit. 

See if that helps.

It works! Thanks, I really appreciate it.
One more thing if you don't mind. Please explain to me what I did.

---

### Post by fizikz on 2014-08-10
You're welcome! Glad it's working.

I'm not sure but I believe that line tells chromium where to find the pepper flash plugin.

---

