---
title: "Ubuntu Mate 16.10 won't let me change home page"
date: 2016-11-03
forum: General Help
---

### Post by danbuter on 2016-11-03
I just installed the newest version of Ubuntu Mate 16.10.  It will not allow me to change the homepage. I just get stuck with the [https://start.ubuntu-mate.org/](https://start.ubuntu-mate.org/). I do NOT want this. I previously was using Mate 16.04, and this was not an issue on that release.

I've reset Firefox, and removed all addons. I can change the homepage, and it will stay correct until I exit Firefox. The next time I restart Firefox, I'm back on that crappy Mate page. Is there any way to fix this?

I'm STRONGLY considering changing distros because of this.

---

### Post by #&amp;thj^% on 2016-11-03
> **danbuter said:**
> I just installed the newest version of Ubuntu Mate 16.10.  It will not allow me to change the homepage. I just get stuck with the [https://start.ubuntu-mate.org/](https://start.ubuntu-mate.org/). I do NOT want this. I previously was using Mate 16.04, and this was not an issue on that release.

I've reset Firefox, and removed all addons. I can change the homepage, and it will stay correct until I exit Firefox. The next time I restart Firefox, I'm back on that crappy Mate page. Is there any way to fix this?

I'm STRONGLY considering changing distros because of this.

This was bug... and it was meant to compliment Mate.... But the bug was reported here:[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-settings/+bug/1605887](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-settings/+bug/1605887)
You can try the work around mentioned there or you simply remove "ubuntu-mate-default-settings"...which is what I did.
```
sudo apt remove ubuntu-mate-default-settings
```
Cheers

---

### Post by danbuter on 2016-11-03
> **1fallen said:**
> This was bug... and it was meant to compliment Mate.... But the bug was reported here:[https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-settings/+bug/1605887](https://bugs.launchpad.net/ubuntu/+source/ubuntu-mate-settings/+bug/1605887)
You can try the work around mentioned there or you simply remove "ubuntu-mate-default-settings"...which is what I did.
```
sudo apt remove ubuntu-mate-default-settings
```
Cheers

That fixed it! Thanks!

---

### Post by #&amp;thj^% on 2016-11-03
You are Very Welcome.:)

---

### Post by hobsonrgg on 2016-12-05
Thanks It worked for me too.didn't like the upgrade from 16.04, then this thing with Firefox,  always something when we have to upgrade..almost left  too..but problems were solved.Thank again...

---

### Post by #&amp;thj^% on 2016-12-05
[COLOR=#ff0000]***Just A Heads Up***
[/COLOR][COLOR=#000000]There has been at least one member here reporting on their next Reboot they had a _**Session Failed error**_...so here is some more information and choices for you if this happens to you also.
See Post#11: [https://ubuntuforums.org/showthread.php?t=2342859](https://ubuntuforums.org/showthread.php?t=2342859)
You will also see a warning with Soft Ware Boutique saying you are Not using Ubuntu Mate...But that is the extent of it...**I have had "NO" problems using and installing software with with it.**
Hope this helps.
[/COLOR]

---

