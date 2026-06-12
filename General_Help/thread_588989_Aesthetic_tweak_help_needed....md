---
title: "Aesthetic tweak help needed..."
date: 2007-10-23
forum: General Help
---

### Post by germclown on 2007-10-23
Hi:) Since Feisty, I've been gradually (successfully) putting together a graphic environment to slowly chip away at the aesthetic high horses of my Mac-loving friends. Gutsy has thrown me a few curveballs, though:

1) the OS load screen looks fine except that it is ever-so-slightly off center: about 100px left and up. My screen's native is 1280x1024 in case it matters.

2) I can't get rid of the beige background after logging in. The process goes roughly like this: nice, single colour screen (same as the "no background" colour in "appearances"); nice, sexy login screen; UGLY BEIGE SCREEN (Blech!); nice, sexy desktop and UI.

3) My collage of an icon set was modded from a gnome standard set. Try as I might, the foot that has replaced the Ubuntu logo on the "applications" menu will not go away. I have erased all traces of it in the icon set and there are no inherits from other sets.

I'm completely stumped on all these points, but my anal retentiveness can't give them a pass. Any ideas:confused:

---

### Post by seventyeights on 2007-10-23
1. Maybe your monitor has an auto-center button?

2. Go into system/preferences/appearence, and click on the background tab. Select the first rectangle (should still be beige) and then go a bit down to the Colors section and click on the other (smaller) beige rectangle. This will bring up a palette.

---

### Post by strabes on 2007-10-24
1) Your bios might have an option to not stretch resolutions that are lower than the native. This is what I do on my widescreen laptop and it centers and shrinks the bootsplash perfectly.

2) Try setting the background color on the "Local" tab of System > Administration > Login Window.

3) The foot is probably a remnant of the GNOME or Tango icon sets, depending on which one the icon theme is based on. I don't know how to change it.

---

### Post by MatthewPlanchard on 2007-10-24
1. i agree with the above posters, also thought I'd mention to check /etc/usplash.conf and make sure those numbers are on call with your monitor

2. again agree with the above posters. also try running gnome-control-center from a terminal and using that to set a splash image with the splash image section. you can also choose to display a control center shortcut in your normal preferences menu!

3. use the synaptic packet manager to download the ubuntu studio icon set . . . it should replace the foot with a really neat blue version of the typical icon.

can we hope for screenshots once you get it up to the official nyeh nyeh it's better than a mac level?

---

### Post by germclown on 2007-10-24
Thanks all! Great advice!

I'll hopefully get around to checking these when midterms are over.

A few notes, though:

@seventyeights:
Changing the background in appearances only changes the colour I see prior to the login (the one I mentioned in the post). I've changed this for both the empty bg and the one I actually use.

@strabes:
I'm pretty sure the local colour in logins did the trick in Feisty, but no dice this time around.

@strabes & 78s:
My splash was centered fine at native rez under Feisty.

@Matthew:
Thanks for the file and package tips. I've only been using Linux for a couple months now, and all my dll and ini savvy is next to worthless in penguin town. Good to know a few new locations.

And I will, of course, post screenies some day... I might need to do a custom controls set among other things, so it could be a while.

---

### Post by WiFi Ed on 2007-10-24
To fix background color issue...

[http://ubuntuforums.org/showthread.php?t=578406&highlight=gutsy+background+color]("http://ubuntuforums.org/showthread.php?t=578406&highlight=gutsy+background+color")

---

