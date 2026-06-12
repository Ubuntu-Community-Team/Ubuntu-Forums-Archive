---
title: "making my desktop really cool like beryl"
date: 2008-04-22
forum: General Help
---

### Post by dean5778 on 2008-04-22
I've just installed ubuntu 8.04 and wondering how do I play about with the themes and desktop to make it look really funky and 3d like. Just like the videos you see on youtube. Where should I begin looking and reading to get that information. 

Thanks

---

### Post by Martje_001 on 2008-04-22
If you're not afraid to break your system, read [this]("http://www.xs4all.nl/~mgj1/compiz_git.htm") (see below).

If you don't want to do this, install compizconfig-settings-manager with synaptic (or apt-get install compizconfig-settings-manager).

Good luck!
[COLOR="DarkOrange"]
Edit: New theme on ubuntuforums seems to break the link colors :evil:, '[this]("http://www.xs4all.nl/~mgj1/compiz_git.htm")' is a link![/COLOR]

---

### Post by jimbo99 on 2008-04-22
It is tough to just enter the Linux world with the expectation that your desktop will thrive in the 3d compiz/beryl world.  Even in a Windows world you have to spend time learning it, getting to know the ins and outs, getting past the pesky things that annoy you.  All software is this way.  Every software package is this way from  your camera software, to your office suite, to your desktop, to your games.  All software.

With that in mind, Compiz is on by default.  Beryl has essentially been merged with Compiz.  That happened some time ago.

Under your preferences menu (at the top of the screen) is a selection for appearance.  The last tab on the right is visual effects.  If  you do not have the 3d desktop by default then there may be other issues because normally the 3d desktop is on by default.  Try one of the options in the visual effects and see if you can get the maximum effects working.

Yes the compiz settings manager is nice and I use it all the time--but, you should not go turning things on and off willy nilly as you will loose track of what you did that affected which area.  There are so many settings it is easy to get lost.

---

### Post by dean5778 on 2008-04-22
well I have found the visual effects panel and did click it. When I hold a window and move it around it does that funny wobble. That's cool. 

I've not yet been able to understand how to use the 'cube' desktop look. Don't what what buttons to press on that one. 

What i'm kind of looking for is similar to how os x leopard is. Especially when you minimize things or add a widget and you get that ripple effect across your desktop. I've even saw some windows burn into flames when you close them.

Yes i am new to this operating system. I've used windows since 95 so am comfortable with it's interface and how to fix stuff. This operating system is defenitaly out of my comfort zone. However i'm not afraid to learn something now. I'm not about to start clicking everything that's thrown at me. I dont want to break anything. 

Just been really searching then net and trying to find sites which guide you through everything on how to make your computer desktop very pleasing to the eye and works fine.

---

### Post by bijeeshvs on 2008-04-22
install Emerald also (install compiz) go to system>preferences>advanced desktop settings , and play with the settings , u can change the themes from
system>preferences>emerald theme manager , if you like a dock install "avant window navigator" checkout my screen shot . if you want the clock and the calender and other things go to synaptic and install "screenlets" for all these things to work you must install compiz 
it get sometimes tricky but don't worry everyone in the community will help you to the very best but don't forget to post how its all going 

good luck!!!!!!!!!!!!!!!!

---

### Post by Martje_001 on 2008-04-22
> **dean5778 said:**
> I've even saw some windows burn into flames when you close them.
You have to enable 'Animations' for this, and change the defaults settings (in compiz-settings-manager).

---

### Post by bijeeshvs on 2008-04-22
for the fire effect you have to use the animation plugin,
checkout the screen shots, for the cubes to work u have to use the "desktop cube " rotate cue " "cube caps " plugins. In the actions tab of each plugin you can see and set the key combinations for each plugin , i mean each effect

---

### Post by russo.mic on 2008-04-22
> **jimbo99 said:**
> It is tough to just enter the Linux world with the expectation that your desktop will thrive in the 3d compiz/beryl world.  Even in a Windows world you have to spend time learning it, getting to know the ins and outs, getting past the pesky things that annoy you.  All software is this way.  Every software package is this way from  your camera software, to your office suite, to your desktop, to your games.  All software.

With that in mind, Compiz is on by default.  Beryl has essentially been merged with Compiz.  That happened some time ago.

Under your preferences menu (at the top of the screen) is a selection for appearance.  The last tab on the right is visual effects.  If  you do not have the 3d desktop by default then there may be other issues because normally the 3d desktop is on by default.  Try one of the options in the visual effects and see if you can get the maximum effects working.

Yes the compiz settings manager is nice and I use it all the time--but, you should not go turning things on and off willy nilly as you will loose track of what you did that affected which area.  There are so many settings it is easy to get lost.

You know, it's pretty easy to save a profile, screw around, then reload that profile in CCSM.  Save a profile guys, and play around willy nilly as you'd like!

Russo

---

### Post by scradock on 2008-04-24
I have a detail question, related to the overall thread: where is emerald turned ON/OFF as decorationsmanager for compiz? 

In the decorations plugin config screen I can choose emerald as the manager to use _if there isn't a window manager already running_. By typing emerald --replace in a terminal I can switch to emerald instead of metacity; but where oh where do I tell the system to START compiz with emerald instead of metacity?

I had this working fine, then I noticed that it became random whether compiz started up with emerald or metacity, and emerald got less and less frequent; now it never seems to start up.

I've looked in lots of obvious places, and hundreds of unobvious places - is there some simple config file to fix this, or a setting somewhere I haven't thought of?

---

### Post by Lithium17 on 2008-04-24
> **scradock said:**
> I have a detail question, related to the overall thread: where is emerald turned ON/OFF as decorationsmanager for compiz? 

In the decorations plugin config screen I can choose emerald as the manager to use _if there isn't a window manager already running_. By typing emerald --replace in a terminal I can switch to emerald instead of metacity; but where oh where do I tell the system to START compiz with emerald instead of metacity?

I had this working fine, then I noticed that it became random whether compiz started up with emerald or metacity, and emerald got less and less frequent; now it never seems to start up.

I've looked in lots of obvious places, and hundreds of unobvious places - is there some simple config file to fix this, or a setting somewhere I haven't thought of?

Go into System > Preferences > Session

And in the list of startup programs click "Add" on the right hand side.

Type in the name of the Program (anything you want, just describe it, "Compiz + Emerald" is mine).

Then in the "Command" box below that, type in:

```
compiz --replace -c emerald
```

That will start both CF and Emerald every time you log in.

---

### Post by steveneddy on 2008-04-24
Compiz is a default windows manager.

Beryl has been dead for a while now.

Please use Compiz.

---

### Post by scradock on 2008-04-24
Thanks, Lithium17 - compiz starts automatically anyway, so there is probably a script somewhere making that call already. I just want to find it to make sure it has the emerald call in it as well.........

What does the -c do? between --replace and emerald?

---

### Post by steveneddy on 2008-04-24
You mean cool like this?

---

### Post by Fireblend on 2008-04-24
> **bijeeshvs said:**
> for the fire effect you have to use the animation plugin,
checkout the screen shots, for the cubes to work u have to use the "desktop cube " rotate cue " "cube caps " plugins. In the actions tab of each plugin you can see and set the key combinations for each plugin , i mean each effect

Can I ask what theme you're using there? Those are some nice looking colors.

---

