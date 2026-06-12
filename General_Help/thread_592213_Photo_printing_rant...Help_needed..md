---
title: "Photo printing rant...Help needed."
date: 2007-10-26
forum: General Help
---

### Post by jethro10 on 2007-10-26
I never really did much sophisticated printing with my cheap old HP inkjet but it all worked fine I though.

However have got an HP Photosmart D5160 printer and i'm learning more about quality and graphical  printing and have found some startling limitations with linux I think. Maybe someone could convince me otherwise and offer some solutions? Perhaps i'm mis-interpriting something....

With windows you set a default printer setup, eg draft mode, in grayscale only, lets say. Within each program, pressing print uses this and using file-->print (usually) allows you to override this to print lets say photos, but the default remains there for all applications.

Now with f-spot, it just prints. Thats it. You need to change the default setup, then print, then remember to change it back. Does that seem right.

Gimp seems worse, there is a limited number of printer drivers withing gimp, but not mine. I choose general postscript Version 2 and do the same as f-spot for priinter setup. I assume Gimp saves a psotscript file somewhere and then forwards this to the printer. My Brother in law, an average XP user, finds it toally confusing, thinks its basic and this linux thing is nuts.

Glabels (printing CD /DVD labels) is the same it seems, just prints, that's it, no options.

Is this how it is then? it seems so... It's like printing is not integrated, although OOo seems a 
lot better - strange.

Now to another little issue. In windows, my wife can print several pictures to a page 2, 4, 6 ,8 ,9 and a little wizard in windows allows this. She would like to do the same in Linux. Anyone any ideas of a program for this.

And finally although, were really happy with gimp for photo editing, cropping etc. Is there a nice photo printing solution for linux?

phew, thats it

Jeff

---

### Post by jethro10 on 2007-10-26
Forgot to Add:-

Some facilities of the printer, like ink levels and the memory card reader are not available in the Ubuntu printer section, you need to open a terminal and type hp-toolbox ( I think I remember correctly)

Thats going to totally floor a new user.

I've since put a shortcut to that on my desktop.

J

---

### Post by evilc on 2007-10-26
You can use Gnome-photo-printer it's in synaptic.

With the toolbox you will find it in the system-prefs-main-menu it's just not ticked in there if it's installed, then it shows up in the prefs.

---

### Post by rbmorse on 2007-10-26
> **jethro10 said:**
> Forgot to Add:-

Some facilities of the printer, like ink levels and the memory card reader are not available in the Ubuntu printer section, you need to open a terminal and type hp-toolbox ( I think I remember correctly)

Thats going to totally floor a new user.

I've since put a shortcut to that on my desktop.

J

Install hplip-gui (from repository) to add the hp-toolbox to your system menu and enhance the settings and options available.

---

