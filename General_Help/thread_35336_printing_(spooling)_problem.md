---
title: "printing (spooling?) problem"
date: 2005-05-18
forum: General Help
---

### Post by pampelmoose on 2005-05-18
I think that this is a software problem, rather than a hardware problem...but I am not absolutely sure.

I have an incredibly slo..o..o..o.w response on my printer. The printer is an old Canon LBP-430, which is effectively an HP laserjet 3P clone. It's on my parallel port.

I set it up using the gnome-CUPS, and everything seemed to go well : no error messages. When I tried to print a test page, it sent the test page to the printer. The little "data in memory" light went on on the printer, and 2 files appeared in the /var/spools/cups/tmp directory. But the file didn't print -- at least not for a few hours!

The same behaviour has occurred with everything I have tried to print (from the command line, from within a gui application, from the CUPS "print test page") : the printer light goes on, but nothing gets printed for a few hours, maybe a day.

The printer is about 10 years old, and has had its cranky moments. But I am pretty sure that this is NOT a hardware problem. Why not? I also have another Linux distribution on my computer (Libranet 2.8.1). And the printer works normally under the other distro. 

I tried to replicate exactly the same CUPS settings here in Ubuntu. The only differences I can see is that I used the CUPS browser window under Libranet, and that's disabled under Ubuntu. [There does appear to be a different permission structure under Ubuntu : the temporary spool files are rw for the user only, and the user is cupsys..but I assume that's not a problem, since it seems to be a system default.]

So I am guessing that there is some sort of spooling problem..from the temporary spool file, to the lp0 port, to the printer. Or a permission problem?

Anyhow, its pretty unusual, I had thought, for a Linux distro not to be able to print through CUPS to an old laser printer on lp0.

---

