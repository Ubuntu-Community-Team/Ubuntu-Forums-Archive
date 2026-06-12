---
title: "Anyone have a copy of the debs for fingerprint-gui 1.06 in their apt cache?"
date: 2015-07-15
forum: General Help
---

### Post by jwbrase on 2015-07-15
Fingerprint-gui no longer works on certain systems after being upgraded from version 1.06 to 1.07. (See [http://home.ullrich-online.cc/fingerprint/Forum/topic.php?TopicId=481&Posts=18](http://home.ullrich-online.cc/fingerprint/Forum/topic.php?TopicId=481&Posts=18))

After being bitten by this bug on one of my systems, I locked the version of the package to 1.06 on another system that hadn't yet upgraded, but, unfortunately, that system does not have fingerprint-gui in its apt cache and I have been unable to find any debs of 1.06 on the web.

Does anybody happen to have a system with fingerprint-gui that has not yet upgraded to version 1.07? If so, could you see if your apt cache contains copies of the debs for fingerprint-gui and policykit-1-fingerprint-gui (both version 1.06)?

---

### Post by kerry_s on 2015-07-16
if you've never done "sudo apt-get clean" then check /var/cache/apt/archives/
see if theres still a deb there.

---

### Post by marco.tonoli@libero.it on 2015-07-16
Hi,
i have the same problem, i check my folder but there is only 1.07 version (also policikit is 1.07) but i didn't clean apt cache before.


[I]ls /var/cache/apt/archives/ |grep fing
fingerprint-gui_1.07-dfsg1-0ppa1~trusty1_amd64.deb
policykit-1-fingerprint-gui_1.07-dfsg1-0ppa1~trusty1_amd64.deb[/I]



please if you find share result and please tell us how to downgrade. is strange to not have directly answers from authors....

thanks
marco

---

### Post by dino99 on 2015-07-16
might help you  :p 

[https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)

---

### Post by jwbrase on 2015-07-16
> **kerry_s said:**
> if you've never done "sudo apt-get clean" then check /var/cache/apt/archives/
see if theres still a deb there.

Nope. It was replaced by the deb for 1.07 when the upgrade was performed.

> **dino99 said:**
> might help you  :p 

[https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/ubuntu/fingerprint-gui)

I can only find debs for version 1.07 there. I have tried contacting the repository maintainer, but haven't heard back yet.

---

### Post by jwbrase on 2015-07-17
I managed to regenerate 1.06 packages by using dpkg-repack on the system I have that hasn't upgraded yet. Anyone who is also having this issue can use these debs to restore fingerprint-gui to a working state.

```
$sudo dpkg -i --force-downgrade
$sudo chown -R your-username:your-username /var/lib/fingerprint-gui/your-username
$sudo chmod -R 755 /var/lib/fingerprint-gui/your-username
$sudo chmod 600 /var/lib/fingerprint-gui/your-username/your-fingerprint-reader-name/*
```

Then lock the package version until such time as you hear that the bug has, been fixed. (I use Synaptic, so I used Package > Lock Version to do this)

Unfortunately, I can't seem to attach them to this post, so if you need them, PM me and I'll try to find a way to get them to you.

---

