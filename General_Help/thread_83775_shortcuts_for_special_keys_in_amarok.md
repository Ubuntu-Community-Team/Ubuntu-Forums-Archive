---
title: "shortcuts for special keys in amarok"
date: 2005-10-29
forum: General Help
---

### Post by matva on 2005-10-29
I have a i8600 laptop, and it has some special multimedia keys. They work with ubuntu (system->pref->keyboard shortcuts) but not with amarok :( How do i get them working with amarok. They're vol up/down, pause, play, ->, <- 
They come up as 0xae (and another) for volume and XF86audioup etc for the rest. 

thanks !

---

### Post by matva on 2005-11-01
anyone?

---

### Post by souled on 2005-11-01
Did you customize shorcuts to use the keys? Go to Settings --> Global/Shortcuts. Or do you mean amaroK isn't recognizing the buttons?

---

### Post by krye on 2005-11-01
You should be able to customize those keys on the gnome preferences for the keyboard, just use the combinations that work for amaroK with each key:
Windows Key + Z = previous
Windows Key + X = play
Windows Key + C = pause
Windows Key + V = stop
Windows Key + B = next

About the volume... that should be working, or not?

---

### Post by matva on 2005-11-02
i meant amaroK isn't recognizing the buttons.

---

### Post by ltmon on 2005-11-02
Can you go into the Amarok menus and select "Keyboard Shortcuts..."?  It's there somewhere.

Do the predefined shortcuts there work?

If so, you should be able to just change them to "XF86AudioNext" or whatever.

The only thing I can think of to stop this is that you may need some part of the KDE daemon process (kded) running to intercept your shortcuts whilst the Amarok window is not in focus.  I'm not sure how to fix that whilst still using gnome.

L.

---

### Post by perseo1614 on 2007-08-15
This script will allow the use of keyboard multimedia keys in Gnome 2.18 and above (eg. ubuntu feisty) to control playback. This includes most multimedia buttons found on many laptops. Support for this was broken due to changes in the handling of keyboard shortcuts by gnome 2.18.

Good:)

_**[http://kde-apps.org/content/show.php?content=60910](http://kde-apps.org/content/show.php?content=60910)**_

---

### Post by mgmiller on 2007-09-26
This can be enabled from within Amarok itself. 
Click on Tools > Script Manager
Click on "Get More Scripts" and wait for it to populate
Go to the "Latest" tab and scroll down to Gnome Multmedia Keys.
High lite it and click install.
Then, in the script manager click to open the general list.
Click Gnome Multimedia keys to select it
Click Run on the right side.
You don't have to configure it.
You don't have to restart Amarok.
This worked instantly for my keyboard short cut keys that work with Gnome apps.  :guitar:

The more I use Amarok, the more I like it.

---

### Post by blastfm on 2007-10-19
> **mgmiller said:**
> This can be enabled from within Amarok itself. 
Click on Tools > Script Manager
Click on "Get More Scripts" and wait for it to populate
Go to the "Latest" tab and scroll down to Gnome Multmedia Keys.
High lite it and click install.
Then, in the script manager click to open the general list.
Click Gnome Multimedia keys to select it
Click Run on the right side.
You don't have to configure it.
You don't have to restart Amarok.
This worked instantly for my keyboard short cut keys that work with Gnome apps.  :guitar:

The more I use Amarok, the more I like it.

This worked perfectly. Thanks man :guitar:

---

### Post by doriard on 2007-10-20
I'm trying to create global volume control key bindings in Kubuntu Gutsy but there is no action listed to associate the key presses with.  I want the up/down volume control to work with all applications and games, not just Amarok.  

Currently play/pause, next/previous, and stop keys are recognized, but the volume control knob isn't.  The mute key is recognized and shows "mute on" or "mute off" when I press it, but the sound doesn't change.  I previously had my <-- and --> multimedia keys bound to volume up/down in Fiesty but now they are gone (had to do a complete reinstall to get Gutsy to work).

Does anyone know how to create a volume control action for volume up/down when one doesn't exist?  There are no multimedia actions showing now, just window and desktop type actions.

---

