---
title: "Unable to unlock admin tools"
date: 2008-04-30
forum: General Help
---

### Post by seamuso on 2008-04-30
I just upgraded one of my machines to Hardy (x32) from Gutsy. I'm trying to troubleshoot an issue with mdadm and deeded to be able to stop the mdadm service from starting .. Problem is, I can't unlock the services-admin program to disable services .. nor can I open the "users and groups", "network setting", or "time and date".

The unlock button is greyed out. Everything else seems to be working correctly .. I can run anything that pops up the prompt for a password (synaptic, etc) .. just nothing that needs the unlock button pushed. Any way to fix this?

[http://info.bluefrogcs.com/images/unlock.png](http://info.bluefrogcs.com/images/unlock.png)

---

### Post by seamuso on 2008-04-30
Just a bump .. more an annoyance, but if someone knows what to change to allow access to this, it would be helpful.

BTW, on the mdadm issue I referred to, it's fixed. The hardy upgrade changed my hda and hdd to sdx entries .. it then pushed my hde,hdg,hdi,hdk entries (highpoint pata raid controller up to 8 drives) to hda,hdc,hde,hdg .. my mdadm.conf was referencing the original set so was only able to create an array out of 2 disks .. after I changed the entries in mdadm.conf to match my actual drives, all was well again.

---

### Post by seamuso on 2008-05-02
solved from info provided in this thread ..

[http://ubuntuforums.org/showthread.php?p=4866207](http://ubuntuforums.org/showthread.php?p=4866207)

---

