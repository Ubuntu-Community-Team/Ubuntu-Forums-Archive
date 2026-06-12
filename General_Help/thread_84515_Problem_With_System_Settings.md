---
title: "Problem With System Settings"
date: 2005-10-31
forum: General Help
---

### Post by alanpotpot on 2005-10-31
Hi I currently have a problem with System Settings. For some reason the Administer User button would not work. It will just prompt me for a password but will not let me edit my settings. It worked before. 

What happened was I was trying to solve why my KDE is slow. So in one of the forums I learned that I should try to reconfigure using  this command:

sudo dpkg-reconfigure xserver-xorg

I think I misconfigured(since I dont really know all the settings) and X hanged. What I did was to restore the backup of my xorg.conf. It now booted normally but Administer User of System Settings would not work,

Adept will still work but will have an error "None of the authentication protocols are supported. Check if DCOP server is running." before loading.

To make System Settings Work I just checked "Run as Different User" in the menu editor(like the setting of Adept). But if I put the usual settings(and rebooted) it will not work again.

How can I return things to normal? The workaround is fine but it may affect other services.

---

### Post by daller on 2005-10-31
I have the same problem...

But thanks for the idea of running it as root per default!

...It shouldn't affect anything in the system settings!

---

### Post by alanpotpot on 2005-11-01
Its working now! I dont know what happened though. It just worked when I booted my Kubuntu today.

---

