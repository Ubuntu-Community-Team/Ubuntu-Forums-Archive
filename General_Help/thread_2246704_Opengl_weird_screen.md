---
title: "Opengl weird screen"
date: 2014-10-02
forum: General Help
---

### Post by 700 on 2014-10-02
What's that?
Everything worked OK yesterday. No game today. 
How to fix it?

Conditions:
- System: Ubuntu 14.04 LTS / amd64
- GPU: Radeon HD 6970
- GPU driver: AMD FGLRX-updates (proprietary)
- Game: Team Fortress 2 (on Steam; other games OK)
- everything else OK

[IMG]http://pasteall.org/pic/show.php?id=77999[/IMG]

---

### Post by T.J. on 2014-10-02
Have you tried verifying the game assets, and deleting the game's setting files? From the looks of it, it is flipped on the vertical axis.  I don't see how that could happen without either bad settings in the game itself or the OpenGL driver.

I never use the AMD Catalyst driver anymore - it has too many longstanding cursor bugs that crop up on two screens.  It never seems to get fixed.

---

### Post by 700 on 2014-10-03
> Have you tried verifying the game assets, and deleting the game's setting files?
No, because I don't know where these files are.

---

### Post by T.J. on 2014-10-04
The game assets can be verified using the Steam interface, by selecting the game's properties, and the "Local Files" tab.  There is a verify button.

---

### Post by 700 on 2014-10-08
Validation: "All files successfully validated", but I still have the same problem.
I didn't change recently any settings anywhere.

---

### Post by 700 on 2014-10-24
Still not fixed.
It looks like an AMD drivers problem: 
[http://steamcommunity.com/app/440/discussions/0/616189742710481608/#p8](http://steamcommunity.com/app/440/discussions/0/616189742710481608/#p8)

---

### Post by 700 on 2014-10-30
[SOLVED] 
Last TF2 update fixed this problem.

---

