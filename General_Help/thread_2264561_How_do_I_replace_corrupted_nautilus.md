---
title: "How do I replace corrupted nautilus?"
date: 2015-02-08
forum: General Help
---

### Post by fatcatthetinker on 2015-02-08
Hi,
Nautilus is corrupted on my system, showing part of a lower window. Clicking on portions of the lower window changes what directory is shown in the upper window, but I cannot move the uppper window or close the upper or lower window to leave the other window intact. How do I remove and replace Nautilus. Think problem appeared after last routine update. Thanks.

---

### Post by oldrocker99 on 2015-02-08
Here's one way:

Load Synaptic, search for Nautilus, right-click on the file, and select "Mark For Complete Removal." Then, select Nautilus for reinstall.

Another way to do it is to open a terminal and type:
```
sudo apt-get purge nautilus && apt-get install nautilus
```

This should get your problem solved.

---

### Post by ajgreeny on 2015-02-08
Just be careful as that command will remove a whole load of other packages along with nautilus, all of which may have their own dependencies and you could end up removing your complete DE.  Don't just go ahead blindly without noting all the packages that have gone or you could be in big trouble; reinstalling ubuntu-desktop might solve this, but it might not.

There may be a far easier and more efficient way to do what you want, but it depends on the reason for your problem, of course, and as I don't have nautilus installed on Xubuntu I can't help further.

NB: I say this not because I know it will do this but simply to warn you that it might.

What version of Ubuntu are you running, and with which desktop?

---

### Post by fatcatthetinker on 2015-02-08
Thanks for the responses. I am running
ubuntu 12.04  kernal 3.13.0-45-generic  Gnome 3.4.2 

The problem leaves me without the usual easy navigation up and down directory levels. Sounds as if I don't dare try the fix till I have backed up and am ready to do a complete reinstall.

---

### Post by mörgæs on 2015-02-08
If you choose the reinstall (not saying it's the only solution) then it's a good opportunity to get to 14.04.1 or 14.10.

---

### Post by mc4man on 2015-02-08
If you have an issue with an app like nautilus it's better to see if it's a local config issue or in general rather than to just remove/re-install.
12.04 probably has a guest session available (been a long time since I used 12.04

If so, just  log out, log into the guest session & see if nautilus works there.

---

### Post by fatcatthetinker on 2015-02-09
mc4man, the problem seems confined to my session, the guest session does not have the problem,although the guest session is unity and not gnome. I will consider this today to see if a cure is obvious. Thanks.

---

### Post by fatcatthetinker on 2015-02-09
Ok, have searched a bit to try and figure out what to do next, but can come up with nothing useful. Now that I know that the problem is local to my main session how do i fix it? 

It is easy to restore my files and pictures but it takes me weeks to get the user interface back to near something I'm used to after a reinstall . I am inexperinced  working at this level in Ubuntu. but can do a few things in terminal. Thanks.

---

### Post by ajgreeny on 2015-02-09
Your user configuration for nautilus is in the hidden folder .config in your home, so try command ```
mv .config/nautilus .config/nautilusbak
``` and then either restart or logout and in again to make sure nautilus is totally shutdown and then start it again.

---

### Post by fatcatthetinker on 2015-02-09
Renamed folder nautilus to natilusbak and rebooted. Found a new folder and contents had been created. However the problem remains.

---

### Post by fatcatthetinker on 2015-02-09
A screenshot is attached showing the windows overlapping. Clicking the lower window controls the upper window but the upper window cannot be moved.

---

### Post by fatcatthetinker on 2015-02-21
I have upgraded to 14.04 and that fixed my file manager. 
Thanks for the help.

---

