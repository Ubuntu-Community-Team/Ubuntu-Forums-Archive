---
title: "Thunderbird Border missing under compiz"
date: 2008-06-24
forum: General Help
---

### Post by sphoid on 2008-06-24
I'm hoping this is the right forum to post this in. Just upgraded to hardy over the weekend and having issues with thunderbird/compiz

After searching I found this thread:
[http://ubuntuforums.org/showthread.php?t=740444&highlight=thunderbird+border](http://ubuntuforums.org/showthread.php?t=740444&highlight=thunderbird+border)
and this page:
[http://forum.compiz-fusion.org/showthread.php?p=59083](http://forum.compiz-fusion.org/showthread.php?p=59083)

These posts describe my problem exactly. Basically when compiz is enabled, when I open thunderbird it maximizes on the left screen (I have 2 monitors) and the window border is missing. Apparently thunderbird is not under the control of the window manager at all, so no minimizing, moving, etc.

This did not happen in gutsy. Anyone run into this? Solution? Bug report even? Running on NVIDIA 8600 GT on vaio fz190 (Hardy Heron Ubuntu). I can confirm one other person in my office is experiencing the same problem with a similar hardware configuration.

---

### Post by eesperan on 2008-06-24
I can confirm this bug.  It's also occurred in Firefox a couple times, and can be solved by hitting F11 (to full-screen the window) and then again to return to normal size - at this point, the window borders are visible.

Thunderbird has no such full screen mode, so this workaround is not usable in that case.  I have been able to "fix" the issue temporarily by creating a new thunderbird profile (by moving the .mozilla-thunderbird directory and letting TB create a new one), but it comes back after a few uses.

Also, window placement is usually dictated by the layout of windows already present on the screen.  When this bug is manifesting itself, TB *always* loads on the left screen (in this scenario, I have a Vaio VGN-FZ290 hooked up to a Dell 2001WFP over HDMI, which sits to the right of the laptop; making the laptop's display the "left" one).  This is also true for reply windows, etc - the simply overlay each other on the left screen.

No window-manager based hotkeys for de-maximize or move window seem to have any effect on the TB windows.

Finally, there seem to be several halting glitches at times when using TB while the bug is manifested - including full window manager lockups for a few seconds.

---

### Post by kecsap on 2008-07-04
I have the same problem on Lenovo Thinkpad X61s with fresh Hardy installation and I noticed the following:

- The laptop default resolution is 1024x768, but I have an external monitor, thus I'm forcing to switch 1280x1024, if the notebook on docking station.
- If the screen resolution is the default 1024x768, then the Thunderbird does not have window decorations.
- If the screen resolution is the 1280x1024, then the Thunderbird has window decorations.

Funny workaround.... :D

---

### Post by SvenRieke on 2008-09-01
Finally, I found a fix of this problem:
[LIST]
[*]Close Thunderbird
[*]Edit by hand the file **~/.mozilla-thunderbird/xyz1234.default/localstore.rdf** in your default profile directory.
[*]Search the entry
[HTML]        <RDF:Description RDF:about="chrome://messenger/content/messenger.xul#messengerWindow"
                         width="800"
                         height="600"
                         sizemode="normal"
                         screenX="5"
                         screenY="5" />[/HTML]
[*]Change the *width*, *height* and *screenXY* entries to the ones you see here
[*]Restart Thunderbird and it should have its borders again.
[/LIST]

---

### Post by theonlyandy on 2008-09-17
@SvenRieke
Thanks a lot, that worked for me =)

---

### Post by Derek_ on 2009-04-01
That fix works for me until I close and re-open Thunderbird.

I have a dual monitor setup, side by side, such that one desktop spans both screens, but the right-hand screen is larger than the left-hand screen.  I usually use Thunderbird in the right-hand screen.  If the Thunderbird window width is equal or greater than the left-hand screen width when I close, it will fullscreen-maximize in the left-hand screen when I re-open it.  Then when I close it, the screenX and screenY values are set 0, and the width and height are set to that of my left-hand monitor size.  If I change that width value to something less than the left-hand screen width before re-opening Thunderbird, the window comes up normally.

It seems to be intended to protect against having an over-sized window, but it's using the wrong monitor size to make that determination.

Does anyone know a way to either disable that maximizing behavior or to keep Thunderbird from saving the window geometry to localstore.rdf when it closes or to make it use the larger monitor size?

I tried using the Custom Geometry extension ([https://addons.mozilla.org/en-US/thunderbird/addon/4073](https://addons.mozilla.org/en-US/thunderbird/addon/4073)), but it doesn't get around the problem.  Thunderbird maximizes, and then the extension can't adjust the window.

This is with Thunderbird 2.0.0.21 (20090318) on Ubuntu 8.04 with Compiz.

---

### Post by soyouth on 2011-06-01
Thanks a LOT ! That was annoying !

If you are in my case where the problem was the composing window you have to look for the following entry 
"chrome://messenger/content/messengercompose/messengercompose.xul#msgcomposeWindow"

then set sizemode="normal"  and resize as you wish

Thanks and have a good one,

A.

---

