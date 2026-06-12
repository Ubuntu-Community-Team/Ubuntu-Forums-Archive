---
title: "Dell Optiplex 745 Hangs on Shutdown with 8.04"
date: 2008-04-30
forum: General Help
---

### Post by vancouverite on 2008-04-30
I recently installed 8.04 from scratch on my Dell Optiplex 745.  There are two new behaviors that I did not have in 7.10, and both manifest during shutdown when the restart command is given.

The first is that I get lots of warning from Network Manager immediately after issuing the shutdown command.  Eventually those pass and I find myself on the typical "Ubuntu" shutdown screen with the status bar.

This is where the second behavior shows up.  Once the status bar indicates that Ubuntu is finished shutting down the computer hangs, showing the "Ubuntu" logo and an empty status bar.  The only way to finish shutting the computer down is by holding down the power button.

I have attached the entries found in the system log after issuing the restart command.  Please let me know what you think. 

Cheers,
Seth

---

### Post by yvovandoorn on 2008-05-02
I have tried installing 8.04 on three Optiplex 745s... same story. 

Incredibly annoying to say the least.

---

### Post by kesman on 2008-05-02
Have you updated the bios in these pc's? Sounds like an update would solve something like this.

---

### Post by vancouverite on 2008-05-05
Hi, Thanks for the bios suggestion.  I updated the bios (from Dell Bios 2.3.1 to 2.6.1) and it took care of the NetworkManager problems :), however, the computer still hangs on the "Ubuntu" splash with the status bar showing finished.  From here I have to force shutdown.  Thankfully, since this only happens on restarts, I am sitting there to finish the job for it.  Any other ideas?

Thanks,
Vancouverite

---

### Post by stream303 on 2008-05-06
For those who don't need NM and find it hanging their machine, maybe just disabling it, rather than removing it altogether, might be something to try:

[https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager#head-1de145d05f957ff659f5fdb58974ec3e5864def5)

When I did this, I did have to go back into network prefs activate the interface, and tell it to use dhcp (which is what i'm using with my router)...

---

