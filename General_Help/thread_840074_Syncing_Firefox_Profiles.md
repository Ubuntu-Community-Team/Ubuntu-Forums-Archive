---
title: "Syncing Firefox Profiles"
date: 2008-06-25
forum: General Help
---

### Post by phoenixankit on 2008-06-25
I want to sync my Bookmarks between Windows firefox and Ubuntu FF.
Remember, I do NOT want to sync extensions.
Now, I tried using foxmarks, I went to Ubuntu FF(UFF) and installed foxmarks there. It downloaded all my Windows FF(WFF) bookmarks. Now, I made some bookmarks in UFF, then I went to my WFF, but there, those newer bookmarks were not present.
I can use Google Sync, which works really well, but I had some problem's with it, so I'd use it only as a Last Resort.
If I share UFF and WFF profiles, will the extensions also get synced? I do not want to do that because most of my WFF extensions are incompatible with UFF.

EDIT: Just figured out the process with Foxmarks. But if I can do it with the FF profiles, it'd be much easier.

---

### Post by p_quarles on 2008-06-25
All versions of Firefox store bookmarks in a file called bookmarks.html, which is in the profile folder. Presumably you should be able to use rsync or unison to automatically sync two instances of this file on a frequent basis.

---

### Post by phoenixankit on 2008-06-25
Is there a way to share that bookmarks.html between the two FFs?

---

### Post by p_quarles on 2008-06-25
As far as I know, you'd have to sync entire profiles, not just the bookmarks. I could be wrong about this, but the best I could say is that you can copy the bookmarks file between profiles.

---

### Post by ad_267 on 2008-06-25
You could probably symlink the ubuntu bookmarks.html one to your windows one. It's worth a try.

Edit: You use "ln -s /path/to/windows/file /path/to/ubuntu/file" and you'd probably want to rename the ubuntu one first to make sure you've got a backup.

---

### Post by p_quarles on 2008-06-25
> **ad_267 said:**
> You could probably symlink the ubuntu bookmarks.html one to your windows one. It's worth a try.
Yeah, that would work, definitely. 

```
ln -s /path/to/windows/firefox/bookmarks.html bookmarks.html
```

---

### Post by phoenixankit on 2008-06-25
Thanks guys! Problem solved!

---

