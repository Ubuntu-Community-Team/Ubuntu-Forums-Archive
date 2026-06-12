---
title: "nfs freezes"
date: 2006-11-05
forum: General Help
---

### Post by jimisdead on 2006-11-05
Since upgrading to edgy on my server I am having alot of trouble copying to it from my laptop (also edgy) via the wireless network.

It seems to copy at 5-10MB/s until about 50-70MB is completed then it stalls and freezes the laptop (can't even move the mouse cursor). It seems to stay frozen until, in reality (at 600k-1.0MB/s), the copying has reached this 50-60MB mark, where the process repeats itself until the whole file is copied. Altogether making my laptop useless until the file is finished.

I have no problem copying from my server to my laptop, it just chugs along nicely at the real 600k-1.0MB/s rate.

I guess my laptop can't properly determine what the maximum copying speed is, so it fills up some buffer until hitting the limit, and freezes the computer until the buffer is emptied.

Does anyone have any idea on how to fix this? thanks.

---

### Post by troncoso on 2006-11-08
The same thing has happened to me since I upgraded my desktop computer from dapper to edgy, except that my server is still working with dapper and my computer seems to freeze completely. However NFS seems to work fine on my son's computer, which I've also upgraded to edgy. I'll try to find out more about what's happening.

Cheers

---

### Post by jimisdead on 2006-11-08
what sort of setup are you running - I'm on a dell inspiron 9300 laptop, ipw2200, wpa encrypted wireless network, and I just compiled the latest ipw2200 drivers + firmware and ieee80211 modules from source... and it still hasn't fixed the problem.

also, we're not alone - I've seen some posts on other forums too.

---

### Post by jimisdead on 2006-11-08
i just tried compiling the latest ipw2200 modules (+ firmware), and the latest ieee80211 module, with no success.

I also tried some previous versions, also without success. :(

---

### Post by jimisdead on 2006-11-09
strangely enough, sftp connections copy fine.

---

### Post by troncoso on 2006-11-09
I believe it's a bug in the nfs drivers in the current edgy kernel. My son's computer also freezes, I thought it didn't but it does. I've just returned to  the latest kernel for dapper, and I'm copying 1.4GB of movies to my NFS system as I'm posting this. The copy has now finished without any problem at all, so I'm going to stick to this kernel until there's a new one to try.

Cheers

---

### Post by troncoso on 2006-11-13
The bug report I sent three days ago has now been confirmed and given high priority:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/71212](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/71212)
Cheers

---

### Post by Permafrost91 on 2006-11-29
I'm having the same issues copying files from my laptop (running edgy) to my desktop (running edgy) via NFS. What's the state of the issue? Has anyone gotten this to work? Will my laptop actually unfreeze? Thanks!

---

