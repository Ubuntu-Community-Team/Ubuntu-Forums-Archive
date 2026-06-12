---
title: "Screensaver"
date: 2007-10-28
forum: General Help
---

### Post by LostAngel on 2007-10-28
Hello, I just bought a new Inspiron 1520, and installed ubuntu 7.10.  When I run compiz, my screensaver acts like it tries to come on, then goes back off...I tried the following and it didnt fix it...does anyone have another fix?


-------------------------

Ok, not sure if this fix is a good one or not, but it seems to be working for me.

First I decided to remove all the screensaver stuff that was on my comp. I figured they weren't working so I didn't need them just sitting around.

I went to Synaptic Package Manager and removed gnome-screensaver, as well as all of the xscreensaver packages I had installed.

After searching the net it seemed that gnome-screensaver just doesn't work very well, so I decided to not even try to use that. Seems it causes more trouble than its worth. not sure though, someone may prove me wrong later

I went back to synaptic and searched for xscreensaver.
I clicked all the packages, because I wanted all the extra stuff.
(not sure what all they have in those extra packages besides other screensavers, but figured it couldn't really hurt)

So hit apply to install them, easy enough.

Then I opened a terminal and typed "xscreensaver &"
(if that doesn't work try "xscreensaver-demo")

It popped up a nice little settings window for xscreensaver. I chose my settings, set my screensaver to come on in 1 minute, went downstairs to put a plate away, and came back to a lovely screensaver. !!hooray!!

This next part is optional.
As atlas1 pointed out, when you install the xscreensaver, it should automatically add an entry to your Applications menu under Other.
I wanted to keep mine where the original screensaver settings were though.
Then I went to SYSTEM>>PREFERENCES>>MAIN MENU
Click "+New Item" when you are in the SYSTEM>>PREFERENCES section of the menu editor.

A small dialog box will pop up, it may be behind the window if you can't see it.

Type: Application (i originally chose app+terminal, but just app works also)
Name: XScreensaver Settings (or whatever you want to call it is fine!)
Command: xscreensaver-demo
Comment: XScreensaver Settings GUI

I think you should be set after that.
Try it out and let me know. The advanced tab has some power management features, but I disabled them as I was unsure how they might clash with the other gnome Power Management feature in the System>>Preferences menu.

Sorry so long, lemme know if this works, thanks

---

