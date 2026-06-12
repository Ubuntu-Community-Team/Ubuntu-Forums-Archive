---
title: "flashblock firefox2 problem"
date: 2008-06-14
forum: General Help
---

### Post by mulino18 on 2008-06-14
Hi All!

under Hardy, I switched back to firefox2 and installed flashblock.
Does not block at all :0(
I tried uninstall (first from within ff and then from synaptic),
when I look to the ff addons it tells me that flashblock will be uninstalled on ff restart... which it does not.

any clue? 
Tips to have it eventually running (I hate most of the flash banners when I read a newspaper online)
Thx in advance

---

### Post by kerry_s on 2008-06-14
you installed flashblock from synaptic?

if so, then uninstalling in synaptic should do the job.

it's better you get the add on straight from the add on's site.
[https://addons.mozilla.org/en-US/firefox/addon/433](https://addons.mozilla.org/en-US/firefox/addon/433)

---

### Post by mulino18 on 2008-06-14
Did both:
first from addon site, then tried to uninstall (even reinstalled ff...)
installed/disinstalled from synaptic...

anyway it always stays in the adond notification as will be updated/removed at ff restart and simply does not work.
Frustrating, this was one of my favourite addons when I was still under gutsy

---

### Post by windoze87 on 2008-06-14
try this...

```
sudo apt-get remove flashblock --purge
```

if flashblock has a different package name, then use it instead of what i typed in, i always install addons from Mozilla's addon page :)

---

### Post by kerry_s on 2008-06-14
it starting to sound like your profile is screwed up. export your bookmarks to add back after.
in term:
mv -rf ~/.mozilla ~/.mozilla.bak

then try firefox again it should be bone stock, just like the first day you used it.

---

### Post by mulino18 on 2008-06-15
Thanks a bunch, that worked.
(except that mv does not have/need a -r option (you meant recursive I guess))
I (wrongly) assumed a full reinstall would have fixed it though.
cheers!

---

