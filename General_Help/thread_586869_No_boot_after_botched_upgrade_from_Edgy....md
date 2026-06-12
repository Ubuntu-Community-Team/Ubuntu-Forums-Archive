---
title: "No boot after botched upgrade from Edgy..."
date: 2007-10-22
forum: General Help
---

### Post by totaldrk62 on 2007-10-22
Long time lurker here,

I can typically find the answers I need by searching the forums here but it seems to be a lost cause this time. I have been using Ubuntu as my main OS now for about a year. I upgraded from Dapper to Feisty with little to no issues. Well I started the upgrade to Gutsy (from Feisty) yesterday (using the upgrade manager) and I had a power outage mid update. Now when I boot up I get past the Ubuntu loading bar and everything goes black. The monitor shuts itself off, I get no HD activity, and I can't seem to reboot or get a console. The only thing I can do is perform a hard shut off. I can get into a recovery console, but I'm not sure what to try from there. I did a "sudo apt-get update" and it failed updating any packages telling me I need to do a "dpkg --configure -a" which I did to no avail. Anybody have any ideas where I should go from here? I do have a Gutsy CD I could use. Could I just start the CD up and try updating from there or will I lose all my data? Any help is greatly appreciated.

---

### Post by Seisen on 2007-10-22
Are you currently using Edgy, because if you are you need to upgrade to Feisty then Gutsy.

---

### Post by totaldrk62 on 2007-10-22
I'm sorry, I was confused. I was running 7.04 and went to upgrade to 7.10. So I went from Feisty to Gutsy. Well I tried to anyway.

---

### Post by totaldrk62 on 2007-10-22
Ok so I got it running somewhat. It looks like it was my video driver holding it up. I reconfigured my xorg and am now able to get a Gnome session. The video is choppy, moving folders stutters. I was running Compiz Fusion fine before with no issues. I have an ATI 9600 and was using the open source drivers. I am really lost as where to go from here.

---

