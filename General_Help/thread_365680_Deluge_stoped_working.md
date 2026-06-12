---
title: "Deluge stoped working"
date: 2007-02-19
forum: General Help
---

### Post by andnobodyslept on 2007-02-19
Hey all,
So Deluge stopped working on me, not really sure how. I had the debian package installed from the offical website, everything was working fine for about a week and a half, and now it will open just long enough for me to see it open on my panel and sometimes to see the program and then it will fail. I've tried reinstalling it, reinstalling the dependencies (I supposedly have them all there) and even tried pulling the deb package from the feisty repos, which caused a problem involving me having to upgrade libc6, which caused a whole mess of problems for edgy (I was being stupid). Anyway, I have the backport version installed now and nothing, already did update, upgrade and dist-upgrade.

any ideas? I really like deluge and hope to get it back working the way it was earlier today.

Thanks

EDIT:
Figured it out, didn't have the external hard drive that I was using to save the torrents in plugged in...I officially accept that I am an idiot.

---

### Post by Jaymoon on 2007-11-08
Thank you for being an idiot.

I did the same thing.  Except I was using a shared folder via FuseSMB.  Once FuseSMB stopped working out of nowhere, I was wondering why Deluge wasn't working either.

In case anyone else was in my situation, I simply made a folder that normally it would look for if FuseSMB were to be working properly.

In my case I made** /media/Network/MSHOME/Computer5/Torrents-E/TV**

Once that path was created, Deluge worked fine, and I was able to go in and change the default download directory.

Live and learn, but at least you (and I) weren't the only one to do this... :P

---

