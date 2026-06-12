---
title: "Gusty Broke"
date: 2007-10-21
forum: General Help
---

### Post by NFITC1 on 2007-10-21
Yesterday I started the Gutsy upgrade like a good Feisty user should. I didn't know it had to be monitored or I would have watched it the whole hour and a half that it said it would take. Anyway, during upgrade it said it was going to remove or replace several edited conf files. I said it was ok for all of them since I didn't make huge changes to any of them. After the whole process was over and it asked me to reboot I was excited to see that "7.10" was in front of all my kernel revisions in the boot loader. However, something doesn't work right. The fglrx drivers don't work anymore (I suspected this would happen anyway) and when I switched back to mesa, gutsy would get to the log in screen and let me type my user/pass. After this, it just sat there for a while and restarted the X Server as if I had just hit Ctrl-Alt-Bksp. I thought, maybe that was a weird fluke so I tried again. Same effect. Then I rebooted into a earlier kernel (2.6.20-16 instead of Gutsy's new 22-14), but it had the same effect. When It booted up, the on-screen text said somethings I'd never seen before, but they disappeared almost as soon as they appeared so I'm not sure what they said. Something about "Nothing to do with PCI Device 0.something and then "Too much to do" for something else. I'm not sure where the boot log file would be so I can identify these problem causing packages. Can anyone direct me to it (I can get to it in recovery mode) and hopefully explain what those errors mean?

---

### Post by NFITC1 on 2007-10-21
Is it legal to BUMP here? Sorry if it's not.

---

### Post by rsambuca on 2007-10-21
Was that a typo in your previous (first) post?  Did you change the driver to 'mesa', or did you change it to 'vesa'?

And yes, by the way, it is frowned upon to bump your thread this quickly :)  Maybe wait a day next time!  If you need instantaneous help, perhaps the IRC channels are better suited for that purpose.

---

### Post by NFITC1 on 2007-10-21
It was no typo. It is "Mesa". That's the open-source ATI drivers.
Yeah, sorry about the bump. I noticed that it got to the second page in less than an hour (which is typical when a new release comes out) and was afraid (panicked) that it'd get buried even farther before someone saw it. I think I will visit the IRC room. Thanks for the suggestion.

---

