---
title: "Cleaning Cache Safely"
date: 2022-05-08
forum: General Help
---

### Post by mongo42 on 2022-05-08
Hi all,

I noticed that my /home/user/.cache folder is growing significantly, mostly due to the vmware subfolder (which is not automatically cleaned upon exit...?!?).  My question is, is it safe to simply delete stuff to clean it out (something like "rm -fr /home/mongo/.cache/vmware/drag and drop/..."), or is there a better way to accomplish the same thing (like apt-get "clean" or "autoclean")?  Thanks!

Mongo

---

### Post by Impavidus on 2022-05-09
> **mongo42 said:**
> is it safe to simply delete stuff to clean it outIf it isn't, it shouldn't have been called cache. The whole idea behind cache is that it speeds things up, but isn't vital. But then, some programmers ignore the guidelines.> something like "rm -fr /home/mongo/.cache/vmware/drag and drop/..."
That command won't work. If there are spaces in the argument, you have to quote it or escape the spaces. I don't expect you need the -f option. Best to leave it out if you don't need it. -f is to ask for confirmation to delete write-protected files, which are usually write-protected for a reason.

---

