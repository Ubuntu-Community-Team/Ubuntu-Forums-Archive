---
title: "remove unnecessary updates"
date: 2008-04-09
forum: General Help
---

### Post by rishav on 2008-04-09
Hi, I am using ubuntu for my home computer since 7.04. I dont have any printer attached to my computer nor I need to do any print related work.

I removed sudo cups and similar items by apt-get remove cups<tab>

But the update is nagging me to update cups and other cups related stuffs. 

I dont want to waste my internet updating the thing which I dont require.

How can I stop it asking me from updating unnecessary items.

---

### Post by mc4man on 2008-04-10
If you want to keep your ubuntu-desktop you have to have cupsys and related packages. Nothing says you have to update if you don't want.  It seems if you lock a version of any package in gutsy while an update won't install it will still show up in updates. In hardy when you lock a package updates  won't show up. (from what i've seen)

---

### Post by rishav on 2008-04-10
Hi, I accidently removed ubuntu-desktop while removing evolution. Nothing bad seems to happen till now.

you mean to say that I'll always have to uncheck cupysys and other cupsys related updates so that they dont get downloaded. Isn't there any other ways out?

---

### Post by forestpixie on 2008-04-10
Find the files you don't want to be updated in synaptic - then when it's highlighted go to the package menu and lock the version and it shouldn't be part of an update.

---

