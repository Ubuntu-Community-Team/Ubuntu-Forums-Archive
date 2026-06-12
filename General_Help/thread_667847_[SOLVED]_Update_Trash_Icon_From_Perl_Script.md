---
title: "[SOLVED] Update Trash Icon From Perl Script"
date: 2008-01-14
forum: General Help
---

### Post by wsmoser2004 on 2008-01-14
I have no idea where to post this, so I'll post it here. :)  Anyway, I do a lot of command-line stuff, and I wrote a small Perl script to move things to the Trash bin when I delete them with rm.  (This is Kubuntu.)  However, the only problem with this setup is that the Trash icon still shows that it is empty when I do this, and when I mouse over it it says "0 items in Trash."  

I figure there must be some way to do this, considering that Dolphin/Konqueror do it...but I don't know how!  If anyone does, please let me know!

---

### Post by wsmoser2004 on 2008-01-15
I figured it out - there's a command called kfmclient, and you can just do 'kfmclient move <file> trash:/' to move something to the trash.  It almost completely negates what I wrote for my script, but it does the job. :)

---

