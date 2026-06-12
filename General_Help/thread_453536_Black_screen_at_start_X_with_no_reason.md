---
title: "Black screen at start X with no reason?"
date: 2007-05-24
forum: General Help
---

### Post by 0x45455844 on 2007-05-24
i'm new to linux. i've installed ubuntu 7.04 and everything was fine.
i installed ati drivers from package and everything was fine,

but after one of reboots i got black screen with cursor waiting (rolling circle).
that's all i got and it doesn't start my gnome enymore.. what can be wrong?
please i need some advices how can i fix that? after first time i got it i didn't find a solution and reinstalled ubuntu from scratch, but on the second day i've got the same situation...

the reason meaybe i've tried to install vnc server but i couldn't beat it and removed.
nothing changed... please help

---

### Post by Dzenhax on 2007-05-24
Does the cursor ask you to log in?  If so you can fix it like this:

Run the live cd
stick a thumb drive (USB Key, Solid state hard drive, whatever you wanna call it)
copy xorg.conf onto it /etc/X11/xorg.conf
reboot witout the live CD
copyt the xorg.conf to the same location on the hard drive
reboot.

If you don't get a login cursor, I don't know what to tell you.  Sorry.

---

