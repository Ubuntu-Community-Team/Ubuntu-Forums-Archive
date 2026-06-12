---
title: "Deleted pcmanfm by accident"
date: 2016-12-16
forum: General Help
---

### Post by Mike_Andrews on 2016-12-16
Lubuntu 16.04 LTS

Firefox failed to load following latest upgrade; crashed repeatedly. Decided to try a refresh, so ran a reinstall from Synaptic to see if that would fix the problem.
But, made the mistake of deleting pcmanfm at the same time, along with a few other packages, hoping to fully remove whatever was causing the crashes. Dpkg no help. Error messages indicated a plugin as the cause; sorry I couldn't make a copy. After Firefox' initial crash I went the reinstall, remove-and-reinstall and finally fully-remove-and-reinstall routes, rebooting at each juncture; no dice. 
Reinstalled pcmanfm via Synaptic from grayed-out Desktop using R-click menu. Pcmanfm was accompanied by 8 other pkgs that were reinstalled as well. Still, no dice.
. . .System is functional now but Level 5 desktop remains a solid gray with no icons and no tool bars. Fully blank. It's playing hide 'n seek. User login screen, which follows decryption PW prompt screen, displays default Lubuntu  (lurid) green 'cracked glass' background but after 2nd login to final Desktop, the blank gray persistently reappears. I still have R-click access to System once arriving at Desktop1 but cannot bring back [lurid-green] default desktop theme with its icons and tool bars. (May be better off without it, ha!) I wonder whether it's even worth fooling with since an unknown issue still prevents Firefox from loading?
Can someone please advise as to how I should proceed? (Take the old HP box to the landfill, maybe?)
BTW -- Tried running a restore from a previously made thumb drive-backup using deja-dup, but System refused to recognize deja-dup.

---

### Post by DuckHook on 2016-12-16
Sounds like you have a pretty gummed up system alright. Made ten times more difficult because you don't recall all the pkgs that you removed.

Seems to me that you have two general options here:

[LIST=1]
[*]Keep wrestling with the problem(s) until you beat it(them),
[*]Reinstall Lubuntu and start with a pristine environment.
[/LIST]
Of the two, #2 depends on you having backups of your data, but it will be by far the easiest and fastest. Besides, so long as you can still access your /home directory, you can back up.

Re: old box/landfill

Only you can decide if you want to keep dancing with the old bear. I have a soft spot in my heart for ancient-ware (see sig), but even I throw stuff out when they no longer have any appreciable use. If you post the specs, that may tell us if it's worthwhile keeping around as a server. No GUI, not even LXDE, no more wrestling with FF…

---

### Post by Mike_Andrews on 2016-12-17
DuckHook,

Thank you for the well-worded reply.
. . . You and I think along the same lines -- in this instance, at least; I would happily overwrite the current mess with a new install of Lubuntu and never look back.
Even though. . . my gut tells me that there is something radically amiss with the old HP's hardware, that it either somehow isn't designed to operate within the Lubuntu environment or there is a 'hitchhiker' living in the CMOS.
I'm informed that in the latter instance there is only one recourse, which entails a mobo replacement.
. . . Maybe I'll just retire the old junker, because these anomalous circumstances have continued recurring throughout multiple installs.
As written, one of the principle indications of insanity is the repeating over and over of a failed action hoping each time to achieve a different outcome.
After thinking about the above it comes to mind that there are some instances when persistence pays off.
. . . Perhaps this is not one of them.
Thanks again, DuckHook.

M.

---

### Post by DuckHook on 2016-12-18
> **Mike_Andrews said:**
> …it either somehow isn't designed to operate within the Lubuntu environment or there is a 'hitchhiker' living in the CMOS.The former is more likely than the latter. It's very difficult to infect the CMOS, especially of older boxes. You almost have to install it as firmware. As to the age of your HW, there is a point beyond which even Linux won't work. However, yours doesn't seem that old. You've obviously gotten it working before. I'm betting that it can still work with the right tweaks.> I'm informed that in the latter instance there is only one recourse, which entails a mobo replacement.Possibly true, but a waste of money in old boxes.> …these anomalous circumstances have continued recurring throughout multiple installs.Have you looked into your HDD? If stuff keeps getting corrupted some time after install, but was working OK till then, the culprit is often bad sectors on the HDD. They are cussed little devils to ultimately diagnose too, because they give rise to a different set of bad behaviours with each install. If you have another HDD, it may be worthwhile to swap out the existing one and try another.

If you do decide to keep the old dog alive for a bit longer, feel free to start new threads in the Hardware subforum, one thread per issue. But please give HW specs each time so that helpers have something to work with.

Good Luck and Happy Lubuntuing!

---

