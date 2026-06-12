---
title: "Hardy Compiz scale plugin bindings broken"
date: 2008-04-26
forum: General Help
---

### Post by Vermind on 2008-04-26
Hello,
In the Hardy version of compiz-plugins, the scale plugin bindings do not work as they should. [compiz scale in compiz fusion wiki]("http://wiki.compiz-fusion.org/Plugins/Scale"). In particular, if I bind the scale to a mouse button or a mouse button in a particular corner of the screen, or a keyboard shortcut, I will have to hold the mouse button or the keyboard modifier to keep the scale on. It is not toggle, as it was in the previous version, and as it is supposed to be.
Holding the buttons and using the scale window filter, that is, finding a window by typing parts of the name, is at best very cumbersome.

Right now I workaround this with binding the scale to just the top right corner, without a button. I would prefer not activating scale by accident though. Could someone tell me how to fix the scale plugin, where to post about a broken original compiz plugin, or tell me how to get a fixed version.

Thanks,

---

### Post by Zorael on 2008-04-26
I noticed this as well.

It is possible to compile the plugin from source to get a newer version of it, but this requires developers to have noticed the bug in the first place.

I suggest you search the forums over at [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/), and if no results, post a thread.

---

### Post by rogeriovinhal on 2008-04-26
I've noticed that too.

And even if that is solved, the settings manager doesn't let me put a binding only on the upper right of the screen without pressing mouse button.

That sucks because scale is a plugin that becomes interesting because of its ease of activating. Having to hold a button to select a window is no easy at all. If I have to do that I'll just do Alt+Tab that is a lot quicker.

EDIT:

Just found out that what I wanted is possible! Actually, it is quite obvious.

When editing the bindings you can configure 3 types of them (each one has an icon). Screen, mouse and keyboard.
The mouse forces you to open and then hold one button, the keyboard is just the same, but the screen just needs you to place the mouse in the chosen corner and then choose the window.

But it is really annoying if you want to use the keyboard or mouse binding.

---

### Post by Vermind on 2008-04-26
Hello,
I searched the compiz-fusion forums a few hours ago. No mention of the bug. I am a member of the forum, but for some reason I am unable to post stuff there. Maybe I should create a new account or somesuch.

---

### Post by Jacob111 on 2008-05-13
Another odd issue I've come across with the buttons.  Has anyone noticed how you can't remap the move and resize window to different mouse buttons?  For example, changing move window from <Alt>Button1 to <Alt>Button2 (or 3, or 4, etc.) doesn't change it.  Only Alt+Button1 still works.  You can change the keyboard button or remove it but no matter what mouse button, it always thinks its button1.

If you close and reopen the compiz settings window you will see that it reverts the mouse assignment back to button1.  It's kina annoying.

---

### Post by JGJones on 2008-05-21
Seconded! I have actually reported this as a bug and it's also listed as a bug at Debian I think. I used Scale a LOT in Gutsy - but I absolutely hate using Screen binding as it's too easy to activate by accident all the time (it's one of the primary reason I hate Expose on OSX).

I use Mouse binding only, and I also use the Scale Addition Plugin as well - so if I need to close windows quickly - I have Windows from All desktop binded to mouse as Upper Right Corner with Button 3. I get all windows. I can then close them as needed using middle click. Fantastic and all that.

In hardy I can no longer do it. 

My bug as reported in Launchpad - [https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/201392](https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/201392)

I have also discovered that it's also reported as a bug with Compiz and the link is here (good news...there are patches for it. bad news? I don't know how to compile - would prefer to wait for it to be backported or something)

[http://bugs.freedesktop.org/show_bug.cgi?id=11331](http://bugs.freedesktop.org/show_bug.cgi?id=11331)

---

### Post by Jacob111 on 2008-05-21
Oh now I feel less stupid.  Someone else who doesn't know how to compile.  I'm still a linux noob.

---

### Post by wdaniels on 2008-05-21
> **Vermind said:**
> I will have to hold the mouse button or the keyboard modifier to keep the scale on. It is not toggle, as it was in the previous version, and as it is supposed to be.

This has been bugging me too - I just assumed somebody must have decided it was better working this way rather than it being broken. So, if there's a fix I'd like to know about it also...

---

### Post by van_Zeller on 2008-11-06
Oddly, I used scale a lot in hardy, and recently switched to intrepid. Guess what: scale not working properly. Strange to find mention of this bug here, on a hardy thread...I thought it was an Intrepid problem...

Cheers

---

### Post by Vermind on 2008-11-06
Hello,
that is fairly interesting, since I am now using Ubuntu Intrepid 8.10, and scale works exactly as I want it to. The binding problem has been fixed.

---

### Post by wdaniels on 2008-11-06
> **Vermind said:**
> Hello,
that is fairly interesting, since I am now using Ubuntu Intrepid 8.10, and scale works exactly as I want it to. The binding problem has been fixed.

lol same here - it's back to working properly for me in intrepid also

---

### Post by VincentVX73 on 2008-11-06
You must be lucky because I'm using a fresh install of Intrepid and the scale plugin isn't working right at all.  Like others before me described, it doesn't toggle properly since it scales on press and returns to normal on release of my hotkey.  I've experimented with some different settings and found a few interesting points.  If I have a modifier key involved in my binding it "works" correctly. For example, I tried using the default binding of Shift+Alt+up and the windows scale the moment I hit all three keys.  If I release the "up" key and continue holding the modifiers the windows remain scaled. Next I tried binding my prefered hotkey which is F11 since I'm on a laptop and it is very easy to quickly reach.  With just that single key bound the windows refuse to toggle their scaledness and instead scale while F11 is held and return once it's released. As far as I can tell my compiz and associated plugins are all the latest versions since I opened all the unofficial repos in Software Sources.  Anybody have any ideas how to get scale to toggle properly when using a single key as the initiator?

---

### Post by Vermind on 2008-11-06
Hi,
Sorry, it seems that when using a keyboard shortcut, the initiating key actually has to be held down.
When using a modifier, the modifier has to be held down.
when using the mouse and edge, holding down is not needed.
When using a mouse button and modifier, ALL of them have to be held down.
So, there are lots of problems at the moment, apparently.

But hey, you can use xmacro for now.
install it from the repositories, and set scale to some mouse click in a screen edge. Maybe mouse button 12 or something stupid, so it does not happen when you don't want to. Then create a macro file that makes the mouse go there and click it.
For the top right corner, the file looks like this:
```
MotionNotify 1679 1
ButtonPress 1
ButtonRelease 1
```
Here, change 1679 to your screen width -1, and change 1 in the ButtonPress and ButtonRelease to the desired mouse button. Then save it as right-corner.xmacro, or something else, wherever you want.

then test it with:
```
xmacroplay :0.0 < /where/you/saved/right-corner.xmacro
```
If it works, go to compiz general settings, and commands, and define it as a command. Set F11 as its shortcut.

Hope this works around your problem,

---

### Post by VincentVX73 on 2008-11-06
You sir are a genius, your xmacro idea worked perfectly! I added one line to the end of your code to make the cursor return to the approximate center of the screen after activating the scale plugin.

> MotionNotify 700 333

Having it start at the center instead of the corner makes it easier to quickly pick the window I want, and it doesn't break the way the plugin toggles. Thanks a million for the help!

---

### Post by Vermind on 2008-11-07
Good that it helped :).
To improve upon this, you could find a way to get the current mouse position on the command line.
Then make a shell script that records the current position of the mouse, then runs the corner click macro, then runs a macro that just sets the mouse position back where it was. Then make that execute on the F11 instead of just the one macro.

Might improve usability when the mouse doesn't jump...

---

