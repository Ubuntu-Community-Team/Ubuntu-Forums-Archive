---
title: "Some problems with Gutsy"
date: 2008-01-05
forum: General Help
---

### Post by lanceg on 2008-01-05
I'm a fairly new user of Ubuntu having come from Windows (although I have had some Unix experience in the past).

 I'm running Ubuntu64 7.10 on an AMD dual core 4800+ with 8GB of memory. My video card is EVGA GeForce4 8600GTS 512MB PCI-E (dual-head) and I'm using two Phillips 170B4 (17 inch) monitors.

I really like Ubuntu but I'm having a few simple but annoying problems.

i) I cannot get the trash to display its contents. I can empty it but when I right click the icon and choose 'open' nothing happens. 

ii) When I go to the Places menu and view directories everything is fine if 'view as Icons' is selected, However if I choose 'view as List' then nothing shows up, going back to view as icons shows all the files again.

iii) I cannot seem to get the update icon to appear on the top. I was running Feisty on an old i386 machine and it was fine. It told me when updates were available. Now I have to got to System/Admnistration and use the update manager. Not a big deal but kind of annoying. I've tried finding an applet to add but nothing seems to work.

I've hunted around all the forums to see if I can see anyone having the same issue but have not been able to see anything that seems to apply to my problems.

I would be grateful for any suggestions.

Lance

---

### Post by mpgarate on 2008-01-05
i) Try clicking on it, and if that does not work, try exploring with nautilus to /(youruserneme)/.trash  That is the folder used for the trash bin. It should open when you right click and open, im not sure what would cause that to not happen

ii)im not sure whats going on here.. likely related to the previous problem

iii) that should happen too.. i dont know how to fix that


for i and ii, I think it is a problem with nautilus. Try reinstall nautilus or ubuntu all together?

---

### Post by lanceg on 2008-01-05
Thanks for the suggestions. Being new to Ubuntu I didn't realize that Nautilus was a file manager. When you mentioned reinstalling Nautilus I looked it up and saw what it was. That allowed me to do some more refined searches to see if anyone else had the problem.

I found a bug about list view. Turns out that its a really simple fix (doh!). You have to have at least one column checked in edit/preferences or nothing will show. Now that I checked a few the list view is working fine. The person who ran into this did say that it would be nice if Nautilus had said something about no columns checked, -  perhaps in Hardy Heron :)

I can see the trash from my home folder as .trash. Still not sure why it doesn't open from the trashapplet.

Still no luck with the update notification applet.

So if anyone has any advice on those two I would appreciate it.

Lance

---

