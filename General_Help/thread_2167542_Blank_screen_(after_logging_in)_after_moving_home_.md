---
title: "Blank screen (after logging in) after moving /home folder"
date: 2013-08-14
forum: General Help
---

### Post by szczepan2 on 2013-08-14
Hi.

I installed Xubuntu 12.10 with success - I was able to log in and everything worked fine. Then I moved all my files (separate partition) and my home folder from Xubuntu 13.04, overwriting all the files (and skipped those, that couldn't be copied - e.g. 'socket'). After restarting and logging in (no matter Xubuntu or Xfce session) I can only see black screen. It's not dimmed and I can hear hard drive working after using shortcuts (e.g. to open application).

On 13.04 I had propriety AMD drivers installed (and downgraded X server), now I have integrated Intel graphics card (used default driver, and there's not used NVidia discrete graphics as well).

What should I do? I don't want to install everything all over again...

Edit.

I'm able to acces terminal with ctrl+alt+f# - before and after logging. I recursively changed owner of the home folder - still the same.

Edit 2.

Ha! Deleted Xfce4 folder and now it works. :)

Must remove ~/confing/Xfce4 and restart machine (sudo shutdown -r 0).

Hope it'll help somebody, somewhere, sometime. B)

---

