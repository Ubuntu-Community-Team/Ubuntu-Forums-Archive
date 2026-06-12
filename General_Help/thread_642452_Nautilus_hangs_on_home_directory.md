---
title: "Nautilus hangs on home directory"
date: 2007-12-16
forum: General Help
---

### Post by Juffo-Wup on 2007-12-16
Nautilus hangs when I browse my home directory, either in browser or spatial mode, with Compiz or Metacity. I can browse other folders fine, even those contained in my home folder (e.g.: folders in my desktop), but after I go to ~/, it hangs when I try to access anything in it.

Any help would be appreciated.

Edit: I tried renaming my .gconf folder to something else so that most of my preferences would be turned back to 'factory settings', and the problem disappeared. I will have to customize everything again, though...

---

### Post by mbeierl on 2007-12-16
Umm.  What's the difference between the two files?  If you want help, you could try posting the 'bad' and 'good' versions here...

---

### Post by Juffo-Wup on 2007-12-19
Thank you, but I can't do that now. I turns out that the problem wasn't really solved, it appeared to me that such was the case initially, but the situation persisted.

So I added another user in my system and I copied my files to its home folder, and Nautilus doesn't crash on this one. I deleted the other account along with its folder afterwards.

I don't think it was a good idea in retrospect, as I can't submit a useful bug report now, but I had deleted a lot of files on that folder, and I didn't want to keep that mess as I thought I had mangled the configurations way too much.

Thanks, anyway.

---

### Post by cdyson37 on 2008-04-15
I've been having this problem myself. I fixed it once by deleting some dead symlinks but it came back again today. I found deleting a .png file I had in my home folder has fixed it for now. Perhaps it's a thumbnail/preview related bug.

---

