---
title: "Ubuntu 13.04 Parial Upgrade"
date: 2013-10-29
forum: General Help
---

### Post by Redalien0304 on 2013-10-29
got a Partial Upgrade Option in Ubuntu 13.04 now. Do not know what caused this. but here they are
install 
    popularity-contested
    ubuntu-stamdard
No longer needed
    gambas-gb-gui
Remove
    xscreensaver
Upgrade
gambas3-gb-desktop
gambas3-gb-form
gambas3-gb-form-dialog
gambas3-gb-form-stock
gambas3-gb-settings
gambas3-runtime

do not want mess up my system. do have backup though.
Any help would be Appreciared Thanks

---

### Post by Redalien0304 on 2013-10-29
Bump

---

### Post by newb85 on 2013-10-29
Perhaps you should read this:  [http://ubuntuforums.org/showthread.php?t=1859240](http://ubuntuforums.org/showthread.php?t=1859240)

---

### Post by newb85 on 2013-10-29
Hmm...on second thought, that may not have anything to do with your situation, since 13.04 isn't in testing anymore.

Please give us the output of each of the following:
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

---

### Post by Redalien0304 on 2013-10-29
ok ty read wil wait a day or so

---

### Post by Redalien0304 on 2013-10-29
Ok here is Output of cat /etc/apt/sources.list
[http://pastebin.com/P0W5mKV3](http://pastebin.com/P0W5mKV3)

Output of ls /etc/apt/sources.list.d
[http://pastebin.com/UWEPCNsC](http://pastebin.com/UWEPCNsC)

---

### Post by sammiev on 2013-10-29
Give it a few days and if it has been that already I would take the partial upgrade as this seems to happen time to time. 13.04 is no longer a test version and hasn't been for a long while. Always great to backup your /Home folder first.

You can try a manual update if you wish from the Terminal with this command first.

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by newb85 on 2013-10-30
Before doing the partial upgrade, I would disable your (very extensive list of) ppas and see if the error goes away.  It is most likely caused by one of them.

---

### Post by Redalien0304 on 2013-10-30
Solved by Googling gambas3 decided to Remove Via Synaptic & did sudo apt-get update, upgrade, autoremeove. No more Partial Upgrade. So it was gamabas3. also removed couple of repository from sources.d.list

---

