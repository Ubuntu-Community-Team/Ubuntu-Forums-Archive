---
title: "After hibernate/s2disk, desktop looks crazy [screenshot]"
date: 2008-05-24
forum: General Help
---

### Post by wastedfluid on 2008-05-24
Hi guys.  

After trying a standard hibernation, with much success - only one problem was in my way.  My desktop looked nuts afterwards..

So, I installed uswsusp, which has been a long time favorite.. success, twice! (Can I ask for much more?)  Although - it still looked crazy.  It has something to do with window borders.. and menus.

Here's a screenshot attached.

Maybe it's Emerald.  Maybe it's Compiz??  Perhaps I could run some sort of script on resume that would restart them both? 

Any clues/help you could provide would be greatly appreciated!

---

### Post by pytheas22 on 2008-05-24
Yes, try turning compiz off before hibernating and see if it makes a difference.  I have similar issues if I try to hibernate with compiz running with my i810 graphics card.  I think it worked at one time under Fedora and possibly on Ubuntu 7.04, but since then it's been broken.

---

### Post by wastedfluid on 2008-05-24
> **pytheas22 said:**
> Yes, try turning compiz off before hibernating and see if it makes a difference.  I have similar issues if I try to hibernate with compiz running with my i810 graphics card.  I think it worked at one time under Fedora and possibly on Ubuntu 7.04, but since then it's been broken.

Thanks for your reply.

Simply restarting X fixes it;  and yes, disabling Compiz stops it from doing it, as well.

I'm positive if I could just find a way to run a script to simply restart compiz after resuming - I'd be fine.  I could kill $(pgrep compiz) - and run "compiz -fusion" - but I'm sure there's a much better way of doing it.

---

### Post by pytheas22 on 2008-05-24
I'm not positive, but it seems to me that simply adding the commands you mentioned above to one of the scripts in /etc/acpi/resume.d would make the computer automatically kill and restart compiz whenever it resumes.

---

