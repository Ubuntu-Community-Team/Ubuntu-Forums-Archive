---
title: "After Login Screen Desktop Fails To Load in Ubuntu"
date: 2008-07-02
forum: General Help
---

### Post by tehlastninja on 2008-07-02
Hi there,

I'm a relatively new Ubuntu user, and I have to say I'm impressed with the OS.

I seem to be having a bit of trouble, At the moment when I boot Ubuntu it goes to the login screen, I login and the screen is just blank. I can move the mouse pointer around but nothing happens. 

When it was all working I was halfway through installing some updates before I clicked cancel, although I don't think these updates installed themselves. 

I was thinking I may have removed a package or something but I have no idea which one it could be. I don't mean to be vague here I'm just really not sure as I can't see whats missing at the moment without getting to my desktop :P

Please help.

Thanks People.

---

### Post by narsnarf on 2008-07-02
I am running Ubuntu hardyheron on a newly built comp, and Im having the same problem. Foolishly I used the code below to try to fix a resolution problem i have.

**[SIZE="3"]DO NOT TYPE[/SIZE]**```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
``` **[SIZE="3"]DO NOT TYPE[/SIZE]**

I cannot get my desktop to load up, however I can get to a terminal through Ctl+Atl+F1. Im looking for a way to restore the damage I cause without wipe/reinstall. :)

---

### Post by knutschr on 2008-07-02
Try
```
sudo apt-get install ubuntu-desktop
```

---

### Post by itsdaveperdue on 2008-07-02
or
```

sudo aptitude reinstall ubuntu-desktop

```

I believe hardy also has a repair option if you boot into recovery mode.  Not sure how effective it will be.  You could always reinstall =)

---

