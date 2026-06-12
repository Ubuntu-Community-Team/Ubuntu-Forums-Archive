---
title: "Games and appearance"
date: 2008-05-02
forum: General Help
---

### Post by visionthing on 2008-05-02
Since installing 8.04 if I turn on Visual Effects (even just from None to Normal) my games (Urban terror 3D shooter) have issues. It will try to load to full screen then it looks like the computer fights to try and window it between the top and bottom Ubuntu Desktop Panels. The after flickering between full screen and windows it will evenually lock the mouse then the whole computer. Setting Appearance back to None allows me to run the game normally.

Any ideas? Running an Nvida card with the restricted driver.

Thanks!

---

### Post by encompass on 2008-05-02
I also get these same issues... even in none 3d games like battle for wesnoth.  If I have full screen and effects on it jumps back and for.
So... do you want to report that bug?  I am a little to busy to worry about it.

---

### Post by Zorael on 2008-05-02
Do you have Legacy Fullscreen Support enabled in the Workarounds plugin, in ccsm (compizconfig-settings-manager)?

---

### Post by visionthing on 2008-05-02
Yep. Had to install Compiz to see the settings even. Did that and the workaround is enabled.

The problem does remain

---

### Post by alsamman on 2008-05-02
This is normal when you play games. It is advised to disable Compiz before you play games because it can interfere and cause some problems.

---

### Post by linuxlizard on 2008-05-02
> This is normal when you play games

LOLOLOL

It shouldn't be normal.

I had beryl with the cube working on edgy eft and feisty fawn, and compiz on gutsy and never had this problem until hardy. The only app I used to have to shut it off for was virtualbox full screen mode. Now I have to shut it off for almost everything that goes fullscreen.

If the compiz devs have decided this new incompatibility should be the norm, I hope enough complaints will cause them to reconsider.

---

### Post by alsamman on 2008-05-02
> **linuxlizard said:**
> LOLOLOL

It shouldn't be normal.

I had beryl with the cube working on edgy eft and feisty fawn, and compiz on gutsy and never had this problem until hardy. The only app I used to have to shut it off for was virtualbox full screen mode. Now I have to shut it off for almost everything that goes fullscreen.

If the compiz devs have decided this new incompatibility should be the norm, I hope enough complaints will cause them to reconsider.

What the hell? Whenever I played Counter-Strike in Feisty Days I would always have to switch to Metacity because if I didn't, the graphics would be messed up and the mouse wouldn't work properly.

---

### Post by encompass on 2008-05-02
Actually, guys, when a window goes to full screen it stops rendering.  That's the way it is supposed to be.  And yeah, it never did this to me before, and now it does.  And you know, it may not be compiz it could be something else.  Try stoping all running programs inside of the gnome login... for example... try stopping tracker and any applets you may have running.  If you game works then... we just might have found our issue.

---

### Post by visionthing on 2008-05-03
Nothing else is running. I tested and I get this behavior on a fresh install of 8.04, before anything else is added or loaded.

On 7.10 runs just fine

This should probably go under a different thread but I also notice that in a game (running with Visual effects set to none so the game will actually start) there is fractional mouse latency in games. Like by nano seconds. But is a precision shooter its noticeable. Keyboard same thing. For instance pressing w to running. I will have it pressed consistently and in the game I will suddenly stop ( without taking my finger off the run button ) and I will have to release the button and press it again to start running again. 

Again, same machine on 7.10 I do not have this issue.

---

### Post by elustran on 2008-05-08
I'm having a fullscreen problem too, but not with every program.  mplayer works fine in fullscreen (thank god because this is supposed to be a media PC), and so does zsnes (other main purpose of this computer...), but Planet Penguin Racer and Ur-Quan Masters fail to fullscreen, have a title bar and flicker.  It's a half-baked theory, but I think the stuff that works isn't having problems because it takes over the opengl drivers...

I'm content with my functionality, but I'd like everything to work smoothly.

I'd love to hear from someone who found a full workaround.

---

### Post by HunterCyprus on 2008-05-08
I'm still fairly new to Ubuntu, so I'm no expert.  

I have noticed this issue works in strange ways.  When I run Tux Racer in Gnome, I get a black flicker horizontally across the middle of the screen, changing quality and resolution does not change this.

I also run Dominions 3 in Gnome and I get the same flicker, until I change the games resolution (while in-game) to match the resolution of my desktop.

I have only tested Tux Racer in KDE, but it does not have any graphics issues there.

I am using Compiz in Gnome, and I have a number of desktop visualizations set up in KDE (not sure if this runs through Compiz as well).

I have a PCI Express - ATI Radeon X850 with the restricted ATI drivers set up.

---

