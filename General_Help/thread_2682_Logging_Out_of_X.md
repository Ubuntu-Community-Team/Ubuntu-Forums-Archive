---
title: "Logging Out of X"
date: 2004-10-30
forum: General Help
---

### Post by Cygnia on 2004-10-30
I'm trying to try out fluxbox, but it's not in the GDM menu at login, even though I installed it with Synaptic. Anyhoo I thought I'd try to log completely out of X and do startx fluxbox to see if it works.

I logged out of Gnome to the GDM login screen and Ctrl-Alt-F1 to the first console and typed sudo init 3. That didn't do anything other than asking for my password. So I logged in directly as root but with the same response. ](*,) 

So what I want to know is how do I completely stop the X server or whatnot so I can restart it on the command line.

Thanks for any pointers.

-- 
Bryce

---

### Post by gezzabob on 2008-01-14
To stop gdm.

sudo /etc/init.d/gdm stop

To start X again.

startx

As for changing what desktop environments run by default I cannot remember at the moment sorry but I hope the above helps.

---

