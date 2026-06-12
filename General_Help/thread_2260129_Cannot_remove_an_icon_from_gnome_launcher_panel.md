---
title: "Cannot remove an icon from gnome launcher panel"
date: 2015-01-09
forum: General Help
---

### Post by jf-moniquelevi on 2015-01-09
Hi, and Happy New Year !

I am frustrated !!!

I have been using Ubuntu since Dapper Drake and watched it become better and better.
However, lately, simple things are getting more and more complicated.

Running 14.04 with Gnome (not a Unity fan).  By some mistake, I have 3 "calculator" icons in the top laucher;  I want to remove 2 of them.
I just spent 40 minutes on Google with no success.
The right click brings a Launch/Properties menu.  Alt + right click and alt + win+ right click does the same.  Dragging it in the trash does not work !!!

There must be a real simple thing to do that I cannot figure !

Help would be greatly appreciated !

---

### Post by kerry_s on 2015-01-09
theres no remove from favorites?
have you tried logging out & back in?

---

### Post by jf-moniquelevi on 2015-01-11
> **kerry_s said:**
> 

theres no remove from favorites?
have you thttp://extratorrent.cc/ried loging out & back in?


Thanks !   
I don't understand "*remove from favorites*".  Where would that be ?
Yes, I have logged in and out, rebooted, etc.  However, since I didn't do anything to remove the icons, they are still there
"http://extratorrent.cc" does not seem to exist ???

---

### Post by buzzingrobot on 2015-01-11
A right-click on an icon in the Dash should display the "Remove from Favorites" option.

---

### Post by jf-moniquelevi on 2015-01-11
> **buzzingrobot said:**
> A right-click on an icon in the Dash should display the "Remove from Favorites" option.

Right-click on an Icon brings only 2 choices: "Launch" and "Properties".

As mentionned in the OP, I am using "Gnome", not "Unity".

---

### Post by buzzingrobot on 2015-01-11
> **jf-moniquelevi said:**
> Right-click on an Icon brings only 2 choices: "Launch" and "Properties".

As mentionned in the OP, I am using "Gnome", not "Unity".

Right.  That's what you should see in Gnome. When I right click on icon in the Dash on Gnome, I see neither "Launch" or "Properties".

Icons displayed in the *top* panel in straight Gnome Shell are usually there because the app that produces them is one of the startup applications, and an extension like appindicators or topicon that relocates icons from the message area at the bottom of the screen is in use. Any chance you have more than one calculator entry in your startup list? (Tweak Tool will list them.)

You can't launch apps from the top panel in straight Gnome Shell.  f you are actually launching applications from the top panel in Gnome, however, you must be using the Gnome Classic interface which consists of a collection of extensions, or have installed an extension that provides that capability. (Which I don't use.) Tweak Tool is the only GUI interface available to deal with extensions.

---

### Post by jf-moniquelevi on 2015-01-11
Thanks for the reply !
Using "Gnome Flashback metacity"  BTW same with compiz.
Only 3 items in "Tweak tools" Startup, see screen shot:

[IMG]https://dl.dropboxusercontent.com/u/33224031/Screenshot%20from%202015-01-11.jpg[/IMG]

The "top bar" item in Tweak tool, just list the calendar and clock.
I tried removing the calculator completely, the icons are still there, even after re-boot; they just do nothing. This is just ridiculous !!!
It is not a life-threatening situation ;-), but now it is bugging the heck out of me !

There must be something simple we are missing ???

---

### Post by deadflowr on 2015-01-11
You've tried right-click, how about alt+rightclick or alt+super+rightclick?

(I'm on flashback -compiz now and it's alt+super + rightclick, but don't know about metacity atm.)

---

### Post by buzzingrobot on 2015-01-11
> **jf-moniquelevi said:**
> 
Using "Gnome Flashback metacity"  BTW same with compiz.


And that means I'm officially clueless.

I wonder, tho, if the panel is caching its contents.

Also, if you are using some kind of 'save session' functionality -- that returns apps and windows to the state at the previous logout -- disable it temporarily and see if changes anything.

---

### Post by kerry_s on 2015-01-11
lol, so many choice's of de/wm's everyones just mixing it up. :)

i think we need to concentrate just on the panel. is there an open spot you can right click & select about panel, so we can see what panel is being used?

ps: when i get my panel that screwed up, i just create a new 1 & delete the 1 with messed up settings. sometimes you can just delete the configuration file to reset it back to stock.

---

### Post by CantankRus on 2015-01-11
You appear to have added numerous launchers and applets to the panel. Nothing to do with startup applications.
You should be able to alt+super+rightclick on each item and remove
or
reset the gnome-panel to default with....
```
dconf reset -f /org/gnome/gnome-panel/
```

---

### Post by jf-moniquelevi on 2015-01-12
> **CantankRus said:**
> You appear to have added numerous launchers and applets to the panel. Nothing to do with startup applications.<br>
You should be able to alt+super+rightclick on each item and remove<br>
or<br>
reset the gnome-panel to default with....<br>
```
dconf reset -f /org/gnome/gnome-panel/
```

THANKS !!!
I tried ```
sudo dconf reset -f /org/gnome/gnome-panel/
``` didn't do anything.
Then I just did; ```
dconf reset -f /org/gnome/gnome-panel/
``` and it worked ! Go figure.

---

### Post by buzzingrobot on 2015-01-12
> **CantankRus said:**
> You appear to have added numerous launchers and applets to the panel. Nothing to do with startup applications.


Yeah, I misread.  Thought the OP was using pure Gnome Shell.

---

### Post by CantankRus on 2015-01-12
**sudo** executes a command as another user
so your not changing **your** user settings.
Don't just arbitrarily add sudo to commands as you my find yourself in trouble.
Anyway glad it's fixed and goodluck.

---

### Post by CantankRus on 2015-01-12
> **buzzingrobot said:**
> Yeah, I misread.  Thought the OP was using pure Gnome Shell.
It's hard to tell sometimes.
Should be a checklist to indicate the release and desktop environment/session being used
before you can post a new thread.:idea::mrgreen:

---

