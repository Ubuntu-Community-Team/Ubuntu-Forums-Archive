---
title: "[SOLVED] sftp problem in KDE apps"
date: 2008-01-04
forum: General Help
---

### Post by rpeters on 2008-01-04
In Krusader, I try to open an sftp connection, and this appears:

> Error encountered while talking to ssh.

Same happens in Konqueror. KFTPgrabber just says "connecting..." and does nothing.
This problem is quite recent, I think since upgrading to 7.10.  Maybe a KIOslave is clobbered?   Any ideas on what to do?

[Edit]
Problem not exactly solved (see my last post), since I don't know _why_, but I'll hope it stays fixed (or be forced to use Filezilla again).

---

### Post by p_quarles on 2008-01-04
Just tried it with Krusader, and had no problem. Maybe the problem is with sftp itself? Have you tried connecting with CLI sftp?
```
sftp *username*@*server.address*
```

---

### Post by rpeters on 2008-01-04
Yes, that works OK.

---

### Post by p_quarles on 2008-01-04
> **rpeters said:**
> Yes, that works OK.
Hmm. So it's definitely something at the KDE level. But what?

Any chance you have SSH set to a custom port? Krusader will automatically use port 22, but many people setup SSH itself to use a port that is less likely to get scanned by scriptkiddies. 

If that's not the case, then perhaps you could try running a GTK app and seeing if you get different results:
```
sudo aptitude install filezilla
```
(note: I'm suggesting "aptitude" because this will allow you to easily remove all GTK dependencies when you want to uninstall it).

---

### Post by rpeters on 2008-01-05
Thanks for the replies.  Tried Filezilla this morning, and it worked fine for 3 sftp accesses.
Now, mysteriously, sftp works again in Krusader!

---

