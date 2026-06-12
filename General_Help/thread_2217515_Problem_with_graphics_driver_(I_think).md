---
title: "Problem with graphics driver (I think)"
date: 2014-04-17
forum: General Help
---

### Post by lou6 on 2014-04-17
I have Saucy running on Dell d620, 2gb ram, intel 945gm. I used to dual-boot xp and at that time Morrowind ran like a champ. Since I dumped xp for full-time Saucy I've spent a bit of time getting MW running with wine (1.6) but it's not a champ now - it's so slow that it's unplayable. Also, gltron won't run at all and glxgears (with vblank=0) shows only 1200 fps.

glxinfo says I have the correct driver (i915) so I'm baffled as to what is slowing 3d accel down...

Can someone help?

Thanks

---

### Post by den_ on 2014-04-17
You could tried running the latest mesa and drivers from oibaf repo. There is oibaf thread in Phoronix forums, for the case you have some issues.

It is not clear from your post if you was only running MW on XP, or it was running well on Ubuntu too? If you was playing it on XP only, then chances are, the intel drivers are still not on the same level as ones for XP, and that seems to be a bit older machine (Development focus is on newer hardware, from Sandy Bridge forwards.).

---

### Post by lou6 on 2014-04-17
I was afraid that it might be an outdated driver issue (yes, MW was running great on xp only). 

Thanks for the suggestion - I also am awaiting the 14.04 release hoping for a newer xorg with better drivers...

---

### Post by den_ on 2014-04-17
> **lou6 said:**
> I was afraid that it might be an outdated driver issue (yes, MW was running great on xp only). 

Thanks for the suggestion - I also am awaiting the 14.04 release hoping for a newer xorg with better drivers...

You are still awaiting? Installing oibaf will give you even newer drivers, and it works pretty stable. If an issue arise, one can simply run ppa-purge, and you get everything back to stock settings.

I was using it for a while, until I updated to trusty yesterday. I am bit disappointed. Upgrade from 13.10 didn't work (I was upgrading from 12.04 to 13.10 without real problems.), so I have done a clean install (I had to do a so called secure delete of SSD, to re-plug the disk, etc., and I even forgot to backup some important stuff : (, like Win 7 VM files. I got the disk, which is a real SSD actually, but now I have a different 'hardware' what means I lost my OEM licence.) and now, with clean install, some thing crash not so seldom, like tracker processes, and system doesn't appear stable as 13.10. It hangs on shutting down sometimes, sometimes during boot... And I really don't have much time to be a geek and start a Gentoo install. So I will have to stick with this for while, it seems.

Sorry for the OT.

---

### Post by lou6 on 2014-04-17
I read on Phoronix that the mesa 10 drivers will be in 14.04 (which I was going to upgrade to anyway). Thanks for the info and I hope you get your system sorted...

---

