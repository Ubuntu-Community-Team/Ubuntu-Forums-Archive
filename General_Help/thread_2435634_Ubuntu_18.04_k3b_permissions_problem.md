---
title: "Ubuntu 18.04 k3b permissions problem"
date: 2020-01-23
forum: General Help
---

### Post by lou6 on 2020-01-23
Can someone please tell the correct permissions for cdrdao, wodim and growisofs?  I'm not able to successfully burn an .iso to dvd (but I can sure burn coasters).  My current settings for cdrdao and wodim are 4711 and for growisofs 0755 and I am a member of the cdrom group.  Thank you.

The disks appear to have been written when viewing the underside but are identified by Ubuntu as blank.

EDIT:  I tried burning the same .iso using Xfburn and was successful.  I guess I should just give up on k3b but it has been my Swiss Army Knife for all things related to cd/dvd for so many years that I hate to give it up...

---

### Post by bunny9000 on 2020-01-23
Honestly I've never ever messed with permissions or even thought to do it for k3b. Just install and run and always works fine. I recently burned an linux ISO to a CD on stock install.

Sorry, can't help, just curious why you'd need to mess with the permissions.

---

### Post by lou6 on 2020-01-23
Because k3b is not working correctly, there have been some reports of permission problems in 18.04 and there are very few user-modifiable things in k3b.

---

### Post by SeijiSensei on 2020-01-24
deleted

---

### Post by lou6 on 2020-01-24
I found today that this is a confirmed problem (Bug #978621 at Launchpad) originally reported in 2012 that has never been addressed.  I'll leave this question open for a while to see if anyone can help but will mark it "solved" if no help appears,,,

---

### Post by lou6 on 2020-01-26
Solved my own problem (always better than asking for help).  Uninstalled K3b completely (including hidden files), reinstalled from Software Center.  All is well.  Marking as solved.

---

### Post by speartip on 2020-01-27
This is a problem with k3b & Brasero but not xfburn. The way to resolve the permissions problem is:
```
[COLOR=#000000][FONT=Carlito][SIZE=3] cd /usr/bin[/SIZE][/FONT][/COLOR]  
```
```
[COLOR=#000000][FONT=Carlito][SIZE=3] sudo chmod -v 4711 cdrdao && sudo chmod -v 4711 wodim && sudo chmod -v 0755 growisofs[/SIZE][/FONT][/COLOR]  
```

---

