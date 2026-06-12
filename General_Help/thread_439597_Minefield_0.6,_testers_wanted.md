---
title: "Minefield 0.6, testers wanted"
date: 2007-05-10
forum: General Help
---

### Post by ago on 2007-05-10
[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.6.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield0.6.exe)

This includes new code not available in test1 (which is based on minefield 0.4). Have a go. No fix for grldr error 17 yet, but there is fat detection, new progressbar during disk partitioning, raid0 support, should now work with Xubuntu...

EDIT: version 0.7 is out, use that [http://ubuntuforums.org/showthread.php?t=440609](http://ubuntuforums.org/showthread.php?t=440609)

---

### Post by ago on 2007-05-11
Please test it out, the above is almost feature-complete as far as Lupin goes. Only 2 things left are grub error 17 and m-a support.

---

### Post by PersistentLurker on 2007-05-11
> **ago said:**
> should now work with Xubuntu...

I hate to report that it still does not work: it fails at the exact same place.

I'll comment more in the bugs thread ([http://ubuntuforums.org/showthread.php?t=396546](http://ubuntuforums.org/showthread.php?t=396546))

---

### Post by ago on 2007-05-11
NP that is what minefields are for. Have a look at [https://bugs.launchpad.net/lupin/+bug/87997](https://bugs.launchpad.net/lupin/+bug/87997)
I posted the new kernel detection code in there. I did not actually test it with xubuntu. The relevant line is probably

isodir="${ISOMNT}/dists/${suite}"
grep -q "Package: linux-image-$(uname -r)" "${isodir}/main/binary-i386/Packages" || return ${ERR_INVALID_ISO}

Let me know if something jumps out

---

