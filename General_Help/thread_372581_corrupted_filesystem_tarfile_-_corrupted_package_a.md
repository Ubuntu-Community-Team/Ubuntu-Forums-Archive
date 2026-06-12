---
title: "corrupted filesystem tarfile - corrupted package archive"
date: 2007-02-28
forum: General Help
---

### Post by GoatTuber on 2007-02-28
Last night while applying the latest update for Firefox, the Update Manager failed and told me to do a 'Fix Broken Packages' through Synaptic to fix it. Then Synaptic would give me the following error message:

E: /var/cache/apt/archives/firefox_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb: corrupted filesystem tarfile - corrupted package archive

I tried removing and reinstalling it, rebooting, and running fsck to clean up the drive, all to no avail. Finally, for the hell of it I tried just deleting the .deb file and then doing an update, and it worked. (If you're reading this looking for help, use this as a last resort, as I'm sure there must be a better way of handling this, and change the .deb to whatever your corrupt package is)

```
sudo rm /var/cache/apt/archives/firefox_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb
```

The problem is fixed now. I spent an hour or so scratching my head about the problem last night, and the fix was so simple. This morning while reflecting on it, it has been bothering me. Why would a problem that was so easy to fix give me a non-working solution? I've had to fix broken packages before, ones that were just missing dependencies. Is the "Fix Broken Packages" message just a general catch-all? Wouldn't it be possible for Synaptic to have automatically fixed this problem for me? Personally, I don't mind taking the time to fix the occasional problem should one arise, but as more and more people are migrating away from Windows they're going to need things to be as simple as possible. Most Windows users I know would have no clue what to do if this had happened to them, and would have given up on it. On top of that, my corrupted package was Firefox, which meant that I couldn't use it to browse the web for a solution. (Yes, I got around that, but would they have known how to?)

So, if Synaptic knows that a package is corrupt, shouldn't it at least try to delete it and download a fresh copy? This could have easily been fixed without any input from me, yet I received messages to go fix it myself and they pointed me in the wrong direction.

---

### Post by Henk81 on 2008-04-16
I had the same problem and found your post... now it works! THANKS!!!
It seems indeed that this could have been tried automatically.

---

