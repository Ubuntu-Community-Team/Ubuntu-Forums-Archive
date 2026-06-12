---
title: "apt-build + update manager"
date: 2007-07-03
forum: General Help
---

### Post by hudsonhauck on 2007-07-03
Greetings!

I am rebuilding my system with apt-build. I only got part of the way finished and then an error occurred. *Then*, the next day Update Manager told me that I have 29 packages that need to be updated. But the versions are all *identical* to what I have installed. 

Is there a way to make apt-build + update manager communicate correctly?

Thanks!

-Matt

---

### Post by hudsonhauck on 2007-07-09
Nobody has had this problem? Does anybody use apt-build?

---

### Post by smileysteve on 2007-07-31
You have to change the way that pinning works to be able to not receive the updates notification. This is where I learned the most about apt-build: [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

"And now, this is dramatical !

You used apt-build in order to build your own packages, and when you upgrade with apt-get dist-upgrade, one of your beautiful package is replaced by an official one, what a pitty. You could have avoided this by modifying the pinning of your built packages with apt-build. To put a higher priority for packages built by apt-build, you will have to edit the /etc/apt/preferences file like this:

   Package: *
   Pin: release o=apt-build
   Pin-Priority: 990 
"

But awwee crap, I don't see a preferences file in 7.04,  but you can make one, make sure to delete the spaces to get it to work.
One problem might be that you may or may not get notified of the new version.

---

### Post by Prometheum on 2008-02-04
Shouldn't that only be for upgrades, though?

I just experimented for a while with a preferences file (which doesn't exist by default on 7.10) and it didn't seem to change anything. the output of "apt-cache policy" appears the same.

How does one go about pinning and changing repository preferences on ubuntu? The tutorials on the wiki are eons old and outdated. How must one go about this?

---

### Post by hudsonhauck on 2008-02-20
Hmm....no conclusion on this yet, eh?

---

### Post by Prometheum on 2008-02-20
After screwing around a bit, I was able to change the apt-cache output, but it didn't really matter, Apparently, synaptic and apt use different files. At this point I got frustrated and switched to Gentoo, a distro built for optimization.

Just kidding. What I did find, however, is that the command ```
apt-build upgrade --reinstall --rebuild --force-yes
``` removes any need of an update and lets you keep your built packages. I can confirm this because I installed the SILC toolkit before building, and now I have a Pidgin that can handle SILC (something the repo pidgins STILL don't have by the way), proving that the libpurple installed is in fact mine.

---

### Post by hudsonhauck on 2008-02-21
> **Prometheum said:**
> removes any need of an update and lets you keep your built packages.

What do you mean by "removes any need of an update"? It will never tell you that you need updates anymore for those packages? What happens when updates are needed?

---

### Post by Prometheum on 2008-02-21
Wow, that's a really awkward sentence. I guess I was up a bit late.

To be precise, it takes away the nagging orange box telling you to clobber your custom-compiled packages and accepts them as what they are. If you need an upgrade, it'll still want that, and when you need to do that, you can do it with ```
apt-build --rebuild --reinstall --force-yes upgrade
```

---

### Post by hudsonhauck on 2008-02-21
Excellent. I will give it a try. Thanks!

---

### Post by darkaudit on 2008-07-17
> **smileysteve said:**
> You have to change the way that pinning works to be able to not receive the updates notification. This is where I learned the most about apt-build: [http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

"And now, this is dramatical !

You used apt-build in order to build your own packages, and when you upgrade with apt-get dist-upgrade, one of your beautiful package is replaced by an official one, what a pitty. You could have avoided this by modifying the pinning of your built packages with apt-build. To put a higher priority for packages built by apt-build, you will have to edit the /etc/apt/preferences file like this:

   Package: *
   Pin: release o=apt-build
   Pin-Priority: 990 
"

But awwee crap, I don't see a preferences file in 7.04,  but you can make one, make sure to delete the spaces to get it to work.
One problem might be that you may or may not get notified of the new version.

Made one. Exactly like that one. Made no difference at all. Apt still sees remote packages as newer, even though the version number is the same. Apt will also prefer to download and install the remote repository's package instead of the one that just finished compiling with apt-build. Either there's a bug, or I don't know what I'm doing. Which is it?

---

