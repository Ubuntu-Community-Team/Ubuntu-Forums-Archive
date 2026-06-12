---
title: "GDM, Radeon, random freeze and log-off"
date: 2008-03-25
forum: General Help
---

### Post by dnairb on 2008-03-25
I really like Ubuntu; so much that I have (almost) completely switched from WinXP.
(I still have a Ghost image ready to go back if *really* necessary)

One problem holding me back though is what seem like random freezes or log-offs.
The worst case was when I was logged off, and had to try logging on 4 times before X would start.

IIRC I had just finished encoding a CD in Sound Juicer and had Firefox open (with the flashplugin-nonfree installed).
Sys log recorded something about GDM_slave (I can't remember the exact details, and I'm not at my box at the moment)

I'm running 32-bit Gutsy with all updates installed, Gnome and no remote login. I have an ATI Radeon 9600 graphics card with the open driver; I have read on posts that GDM and ATI cards sometimes have a problem.

After disabling GDM, going back to logging-in/logging-off via the CLI, I had no problems.

However, I would much rather have a graphical login - maybe SLiM or XDM.

Any thoughts?

---

### Post by americano70e10 on 2008-03-25
How do you do that? Switch from GDM to CLI?? Because I'm having some problems with GDM and my graphics card (ATI X1200)...

---

### Post by dnairb on 2008-03-28
> **americano70e10 said:**
> How do you do that? Switch from GDM to CLI?? Because I'm having some problems with GDM and my graphics card (ATI X1200)...

There are links to the GDM start script in folders **/etc/rc<number>.d/** which are of the form **S<number>gdm**.

Renaming these (I did this as root, but I don't know if this is necessary) as **~S<number>gdm** prevents gdm being loaded.

Reboot and, hey presto, you have a CLI login.

BTW I found that booting stopped, and I had to press <RETURN> to get the login prompt.

---

### Post by americano70e10 on 2008-03-30
Didn't work.. but thanks anyway...

---

