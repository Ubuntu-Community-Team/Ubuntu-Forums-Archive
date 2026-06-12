---
title: "Konsole: shortcuts to specific schemas?"
date: 2007-02-27
forum: General Help
---

### Post by celsofaf on 2007-02-27
Hello. I always have a Konsole session open and, depending on the application I'm running at the moment, I use a different schema (the Konsole settings for color/transparency/etc). For example, I use one schema when I'm just "bashing", another one when I use vim, and I like to use a different one when doing stuff as root. However, I'm tired of having to change schemas with the mouse, because of the lost time and atention with the act. And no, when I go to Settings -> Configure Shortcuts (my Konsole is not in English, this is just my translation of the menu), there is no option to assign shortcuts to specific schemas, nor there are when I go to Settings -> Configure Konsole.

Is there any workaround for this, or simply this is realy missing from Konsole? Should I just live with changing schemas with the mouse, or is there any dirt trick to do it?

:confused:

---

### Post by tgalati4 on 2007-02-27
Here's a possible work around:

Create several profiles with different properties for each application.  Create desktop icons with descriptive names.  Edit the command line behind the icon with the appropriate "load profile" switch.

This way whenever you click on a desktop icon, the app will load with your desired profile.  Saving you from having to change it with the mouse.  Which I agree is a pain in the a**.  (my filter, not the forum filter which does ***, I know from experience).

Good luck!

---

### Post by celsofaf on 2007-03-03
> **tgalati4 said:**
> Good luck!

Thank you. I don't know if it will realy do. What I mean is, for example... I'm using Konsole to browse around, then I want to edit a text file. Here we go: 'vim textfile'. Then, I'd like to be able to use a shortcut to change my schema (for _example_, pressing ctrl+1) to a more appropriate one. After I edit my file and quit vim, I'd like to come back to the other schema: ctrl+2. As efficient and simple as that.

That's why I love Konsole over other terminal emulators: it's very, very customizable.

This is it: to add shortcuts to Konsole schemas. It's currently not possible to do it (as far as I'm concerned), unless I go to the source code and fix it myself. But I'm currently unable to do that. :( I guess I'm going to send a message to their maillist. ;)

---

### Post by tgalati4 on 2007-03-03
I like Konsole as well, but I generally use Gnome-based systems for stability.  The Gnome terminal, called terminal, can store different "profiles" where you can store fonts, keymaps, transparency setting, window titles, all sorts of stuff.

You can then assign quickkeys to all of these different terminals depending on what you want to do.  It's not quite as convenient as what you describe, because it requires either a mouse click to activate a desktop icon with your custom profile, or opening a new terminal every time you want to do something different.

You might be able to use voice activation to change schema but that would take some work.

Good luck!

---

