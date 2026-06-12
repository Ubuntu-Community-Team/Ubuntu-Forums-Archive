---
title: "Openoffice.org writer starts automatically"
date: 2007-08-27
forum: General Help
---

### Post by stchman on 2007-08-27
Hello all, everytime I start Ubuntu OO writer starts up.  Anyone have a solution?

Thanks

---

### Post by jamvegan on 2007-08-27
Pure guesswork, because I haven't played with this sort of thing since long ago in another distribution, but maybe System->Preferences->Sessions->Session Options->Save the Current Session after ensuring that you have no apps running.  Then restart, and see what happens?

---

### Post by A. J. Rimmer on 2007-08-27
A while back several of us were having a similar problem with Tomboy.  Various fixes were proposed, but for me it involved deleting Tomboy from Sessiions.  Actually, it seems that I had to delete it, add it back in, then uncheck it.  Anyway, it finally went away.

Don't know why OO would be in Sessions, but you might take a look.

---

### Post by stchman on 2007-08-27
> **A. J. Rimmer said:**
> A while back several of us were having a similar problem with Tomboy.  Various fixes were proposed, but for me it involved deleting Tomboy from Sessiions.  Actually, it seems that I had to delete it, add it back in, then uncheck it.  Anyway, it finally went away.

Don't know why OO would be in Sessions, but you might take a look.

I have the OO quickstarter in my sessions for quicker loading of OO apps.  I will try the delete-reboot-add back in thing.

Where is the sessions conf file located?

Thanks.

---

### Post by -SpaZ on 2007-08-27
- Open up Writer.
 - Go to Tools, then Options.
 - Locate the setting called &#8216;Memory&#8217;.
 - Uncheck 'Load OpenOffice.org during system start-up'.

---

### Post by stchman on 2007-08-28
I did the uncheck load quickstart tray icon.  I rebooted and it did not appear.  I was able to then recheck the quickstarter and all is fine.

---

