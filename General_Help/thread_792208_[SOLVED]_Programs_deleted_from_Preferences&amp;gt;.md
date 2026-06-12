---
title: "[SOLVED] Programs deleted from Preferences&amp;gt;Sessions&amp;gt;Startup but still load - help!"
date: 2008-05-12
forum: General Help
---

### Post by itsjustarumour on 2008-05-12
Help, I'm going totally Bertie...

I have some programs that I can't stop from starting when my Desktop loads, even though I have deleted the entries to do so in System>Preferences>Sessions>Startup Programs. 

For instance, I can't stop Cairo Clock from starting (I'm also having other problems with Cairo clock documented elsewhere on the forum), and also "MyIP" and "Radio" screenlets keep starting, despite repeatedly and thoroughly deleting all their config files etc (I've spent a fair bit of time on the Screenlets forum looking for the answer to this but to no avail.)

I guess there is a config file somewhere that has got "corrupted" and isn't being edited by the GUI - perhaps something along the lines of "gnome-session-properties" or such - but where???  I've looked all over and I can't find anything relevant.... HELP!  :confused: :confused: :confused:

---

### Post by itsjustarumour on 2008-05-13
Bump.  Anyone?  :rolleyes:

---

### Post by gwpritch on 2008-05-13
Close all the programs you don't want to start then open the Sessions dialog. In one of the tabs there is a check box for save desktop configuration on exit. Uncheck that box and before exiting hit the save desktop configuration button now. That should do the trick.

---

### Post by itsjustarumour on 2008-05-13
> **gwpritch said:**
> Close all the programs you don't want to start then open the Sessions dialog. In one of the tabs there is a check box for save desktop configuration on exit. Uncheck that box and before exiting hit the save desktop configuration button now. That should do the trick.

Hi Gwpritch,

Thanks for the post - I'd already tried that though, and it didn't work  However, I've just managed to fix the problem  :-)

The file I was looking for is /home/ian/.gnome2/session .  I deleted the lines for "Cairo-Clock" and also those to run the "MyIP" and "Radio" screenlets, and everything is working fine again.  Looks like there may be some issues with gnome-sessions-properties, and also the way in which screenlets-manager writes to the config file. I'm going to investigate further anyway when I get the chance, and maybe file a bug report or two.  Cheers again.

itsjustarumour

---

