---
title: "How to set default asf player in Firefox?"
date: 2005-04-20
forum: General Help
---

### Post by maddude on 2005-04-20
Dear all

After installing the Realplayer Installer .bin from Real, I realised that I can no longer have streaming asf files in Firefox, anyone have any idea on how can I change it back to totem (which was working)?

Thanks in advance!

---

### Post by gunnyman on 2005-04-20
First, check to see if the file type is listed under edit/preferences/downloads.
if it is, delete it.
restart firefox.  Click on an asf file.  A file open/download dialog box should come up.
choose open with.  If the progarm you used to use is listed, choose it.  If it's not, browse for it, it is likely located in /usr/bin

---

### Post by maddude on 2005-04-21
Hmm..it still isn't working, the website I'm looking at has an embedded asf.

---

### Post by gunnyman on 2005-04-21
try apt-get install mozplugger and apt-get install totem-xine if it's not there already.
If you installed the adobe acrobat plugin for firefox, mozplugger gets removed.
Oh what is the url you are trying to view?

---

### Post by maddude on 2005-04-22
Hi

Thanks for your advice, but it still can't be removed! ARgh. DAMN Realplayer. I'm looking at has an embedded asf. On my other system, it plays fine under Xine!

---

### Post by gunnyman on 2005-04-22
well,
I'm fresh out of ideas now :(

---

### Post by AgenT on 2005-04-23
[QUOTE=maddude]Dear all

After installing the Realplayer Installer .bin from Real, I realised that I can no longer have streaming asf files in Firefox, anyone have any idea on how can I change it back to totem (which was working)?

Thanks in advance![/QUOTE]

Go back to the place you downloaded the bin file (real's website) and look for uninstall instructions. Uninstall the player accordingly. After that, reinstall totem and whatever backend (xine?) totem uses.

---

