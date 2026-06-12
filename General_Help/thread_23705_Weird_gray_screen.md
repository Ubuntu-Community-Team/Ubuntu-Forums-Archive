---
title: "Weird gray screen"
date: 2005-04-03
forum: General Help
---

### Post by teumima on 2005-04-03
Every so often my screen goes gray with weird patterns in different shades f gray. I can't exit X by typing Ctrl + Alt + backspa. Can't do anything, it freezes. I have to turn off my PC and only then it fixes it.

I use the ati drivers. I have a radeon 9200.

Assistance appreciated.

a.t.

---

### Post by Alfonso VI on 2005-04-03
I've had pretty much the same experience (using radeon9250). Which became more and more frequent until it was all that ever happened.

I *think* it's got something to do with an Xorg / Radeon-ATI mismatch. EDIT: How's that for stating the obvious?!
The only advice I can give is to go back to Warty...

This same problem has prevented me from upgrading back up to Hoary, which saddens me some... :(

---

### Post by cgreene on 2005-04-03
Are you using [compositing](http://www.ubuntuforums.org/showthread.php?t=20769) ?

I had this happen with that enabled.

---

### Post by teumima on 2005-04-04
[QUOTE=cgreene]Are you using [compositing](http://www.ubuntuforums.org/showthread.php?t=20769) ?

I had this happen with that enabled.[/QUOTE]
 i had it, then got rid of it, since ati drivers dont work with composite enabled.

---

### Post by Alfonso VI on 2005-04-04
I'm not sure if I had it on or not...

I'm putting off any upgrade back to Hoary until I'm sure it won't happen again (which does suck to some extent).

I wasn't sure if it was a problem with GNOME in Hoary, but since it works fine with Warty - I'm guessing it is Xorg.

---

