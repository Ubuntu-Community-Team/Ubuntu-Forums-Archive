---
title: "Ubuntu 13.04 Nautilus Menu Bar Fix"
date: 2013-05-17
forum: General Help
---

### Post by tecknomage on 2013-05-17
I am sure that many **Ubuntu 13.04** users are missing the **Menu Bar** for **Nautilus**.  In fact there is a [OMG Ubuntu survey]("http://www.omgubuntu.co.uk/2012/07/is-the-new-nautilus-a-step-in-the-direction-poll") that provides the evidence, over [COLOR=#ff0000]76% Nautilus going wrong way[/COLOR] (*see attached screenshot*).

I especially missed the ability to set default View/Column defaults.

Found a patch that works via Google.

Here are the Terminal codes.......

**SolusOS_Patched_Nautilus**

*****Installation:**


[LIST=1]
[*]sudo add-apt-repository ppa:webupd8team/experiments
[*]sudo apt-get update
[*]sudo apt-get dist-upgrade
[*]nautilus -q
[/LIST]


*****Revert to original Nautilus:**


[LIST=1]
[*]sudo apt-get install ppa-purge
[*]sudo ppa-purge ppa:webupd8team/experiments
[*]nautilus -q
[/LIST]


[COLOR=#ff0000]**You need to reboot after either operation.**[/COLOR]

I just tried this and it WORKS :D

---

