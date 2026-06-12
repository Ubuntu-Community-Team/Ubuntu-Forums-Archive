---
title: "Repo file list with no internet"
date: 2007-07-16
forum: General Help
---

### Post by knorr.orange on 2007-07-16
I have a computer with a clean/fresh Ubuntu 7.04 installed.  A friend several miles away has done the same.  I have an Internet connection and he does not.  He can get packages downloaded from an Internet cafe though.

For now, I have to download the package lists, act as if I am going to install the packages and then generate a download script for him to use later at the Internet cafe.

My only goal here is for him to be able to get the package lists on his computer though so he can generate his own package download scripts.  Eventually our installations will be out of sync, so he needs to be able to do this.

My guess is for us both to have the same sources.list files and then I just copy my srcpkgcache.bin and pkgcache.bin files (from /var/cache/apt) for him.  If I do that, will he be able to see the correct package lists in synaptic and generate valid download scripts on his own?

---

### Post by kuja on 2007-07-16
In all honesty It'd probably be easier to do it like this:

Write down the names of packages he wants installed as he goes, when he gets to the cafe, just run sudo apt-get update && sudo apt-get install <list of packages>. 

Anything wrong with this approach?

---

### Post by knorr.orange on 2007-07-16
I agree that is easier, but I don't think it will work out... I didn't mention that he cannot bring his computer to the cafe.  So he takes a flash drive with him to download the packages and bring them home.

So there is no way for him to get that "update" done or the actual download of the packages.  It's full manual mode for everything.  First problem is he can't even get the list of packages (the update you mention) and even if he could, he couldn't download the packages anyway.  The saving grace there is the ability to generate that download script and manually download all of the URL's it contains.

Side note:  The generate package script is broken in Fiesty.  It makes a wget -c [url] but there's a missing space.  It's an obvious problem to fix but for new users that could be quite confusing and see as "just broken."

---

