---
title: "WINE - WinXP Software Configurations Not Being Saved..."
date: 2007-02-01
forum: General Help
---

### Post by SMPS on 2007-02-01
I have gotten Wine working fine with all but one problem...

Short story:
When running Wine with a PCB design SW (PCAD 2004) it does not save PCAD's user configurations (how i setup the windows, the tools, colours, grids, etc...) when I reopen it the next time.

Long story:
I had to copy PCAD off of my NTFS windows partition into the Linux partition because the read-only access (WHICH I COULD NOT DISABLE! in XP) was preventing me from operating PCAD - it would load the screen but not allow me to save and gave me tons of errors.  So I copied/moved the folder and now running it with Wine, it is flawless except PCAD is only efficient if it is tailored to the user... chaning plane colours, grid snaps, storing trace widths, rearranging toolbars, etc..  well when I reopen it all of those changes are lost.  I think it is some ini file somewhere where those settings may be stored, i just dont know where and why they aren't being stored.

I really love Linux now and there are only 2 peices of SW that prevent me from completely removing windows... This one and MPLAB, which I've heard others have already gotten working properly.

Thank you in advance!

Phil

---

### Post by hikaricore on 2007-02-01
You may need to check you winxp registry, most software stopped using ini files for configuration a long time ago.  If you can find the registry keys for your software in windows you can export them, then reboot to ubuntu and import them.

---

### Post by SMPS on 2007-02-01
:D   I just solved my own problem... I hate when I jump the gun and underestimate myself bringing in others when it was unnecissary.

But for the record... There def was a .ini file that stored all of the parameters... a ton of them.  I noticed as a std user it is read only.  So I logged out and sudo su'ed in and gave write permission to the .ini config file for the SW and it works like a champ.

I think the most satisfying thing about Linux for me is the satisfaction of figuring this crap out and the NEXT time... even in Windows I will know what the heck is wrong with the SW.

Thanks for your reply!  I'm sure I'll have more stuff that will stump me for good!

Phil

---

