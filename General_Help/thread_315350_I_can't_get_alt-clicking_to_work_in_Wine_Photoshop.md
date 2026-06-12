---
title: "I can't get alt-clicking to work in Wine Photoshop with Gnome"
date: 2006-12-09
forum: General Help
---

### Post by SolidAndShade on 2006-12-09
In order to use the clone stamp tool in Photoshop, I first must alt-click on part of an image to sample it. By default, alt-clicking is used to move windows. I brought up the System >> Preferences >> Windows window and changed it so that control-clicking moves windows, but alt-clicking still doesn't work in Photoshop. So now I'm forced to log into XFCE if I want Photoshop to work right. Does anyone know how to resolve this? Thanks.

---

### Post by thevinn on 2007-02-21
I'm having the same problem, when I use the zoom tool I cannot ALT+left click to zoom out. It is extremely frustrating.

Crossover Office FAQ sheds a bit of light on the subject

from [http://www.codeweavers.com/support/docs/crossover-pro/troubleshooting#PHOTOSHOP-ALT-CLICK](http://www.codeweavers.com/support/docs/crossover-pro/troubleshooting#PHOTOSHOP-ALT-CLICK)

> 
7.1.5.2.3. Why doesn't Alt-Click work with Photoshop?

Some window managers use the Alt-Click combination to move windows. This means that the button click never reaches Photoshop.

To get the Alt-Click in Photoshop you need to disable this key binding in your window manager. Each window manager may be different, however here are a few examples to help you find how you may be able to do this:

On Mandrake 8.1 you can control this behavior by opening the KDE Control Center and going to Look'N'Feel -> Window Behavior. Once there, scroll to the 'Inner window, titlebar and frame' section at the bottom. There you can either change the 'Modifier Key' field or set 'Modifier Key + Left Button' to 'Nothing'. Here the fields were set to 'Alt' and 'Move' respectively so that Alt+Left Click anywhere inside a window would move the window. After setting 'Modifier Key + Left Button' to 'Nothing' Alt+Left Click should have no special effect, and Photoshop should work correctly.

On Gentoo, KDE 3.1 vanilla the way to turn it off is: Control Center Desktop->Window Behaviour and the Actions tab, then under the section "Inner Window, Title Bar, Frame" set the "Modifier Key + Left Button" to nothing.

On RedHat 9, Metacity: Main Menu->Preferences->Windows. Switch radio button off of ALT to either CTRL or Super (Windows Logo) under "To move a window, press-and-hold this key then grab the window:" 

Any idea what the fix is for GNOME?

---

### Post by proalan on 2007-03-01
Big DOH! moment when i figured it out

simply go to ```
System -> Preferences -> Windows
```

and assign the super key (aka windows key) for the move windows option

> One step closer to becoming completely ubuntu

---

### Post by [Alsharifi] on 2007-09-11
it dosnt work after u change the windows movement setting.



I was messing around with it and i tryed SUPER+ALT+CLICK....Bam!

hope this helps

---

### Post by b20963a2 on 2007-09-15
Ah, exactly what I was looking for. I finally might get my girlfriend to stop rebooting to her old XP install just to use photoshop. Actually tried installing it both via wine and virtualbox, but both solutions have the same problem...

I'll ask her to give it a try and report back.
==> WIN+ALT+Click does the trick!

---

### Post by proalan on 2007-09-16
Just to note beryl/compiz have their own 'move windows' mapped keys which will take precedence over the settings at 
```
system->preferences->windows
```

---

