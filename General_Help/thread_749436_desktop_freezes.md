---
title: "desktop freezes"
date: 2008-04-08
forum: General Help
---

### Post by b0ltkutt3r on 2008-04-08
after installing ubuntu 7.10 , after the updater finnished installing updates. I suddenly got logged out, had to re-log back in, and the desktop freezes up. any ideas, what might cause this?

---

### Post by redbob on 2008-04-08
This diagnostic is not so clear. You must log command-line, since desktop is freezing. Try Ctrl-Alt-1 before gdm is going to show gui. Then login into command-line, and try execute this command:
> sudo dpkg-reconfigure xserver-xorg
It must be video-card misconfiguration. What kind of video adapter you have installed?

---

### Post by b0ltkutt3r on 2008-04-08
I think i got it worked out now, thanks for your help.
 I think part of the problem was my mouse, lol.
as I still have much yet to learn, any help is greatly appreciated :) 



(nvidia 7900 gs):

---

