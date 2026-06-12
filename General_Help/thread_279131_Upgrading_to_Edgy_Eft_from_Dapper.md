---
title: "Upgrading to Edgy Eft from Dapper"
date: 2006-10-17
forum: General Help
---

### Post by Jordan Meeter on 2006-10-17
Hey,

Since the release of Edgy Eft is pretty much right around the corner, I figured I'd go ahead and upgrade now. What do I have to do in order to upgrade? Is there anything I should be concerned about? i.e. unstable.

Thanks

---

### Post by Jordan Meeter on 2006-10-17
I followed the steps at [https://wiki.ubuntu.com/EdgyEft/Beta#head-393b07741f71e473393b6677bba8d66fb4bde7ec](https://wiki.ubuntu.com/EdgyEft/Beta#head-393b07741f71e473393b6677bba8d66fb4bde7ec) but it did not update...

---

### Post by Kateikyoushi on 2006-10-17
Then try the steps recommended in [this thread]("http://ubuntuforums.org/showthread.php?t=227052&highlight=upgrade+to+edgy") did you do an aptitude update and upgrade before you tried to upgrade to edgy ?

---

### Post by chirayu on 2006-10-17
gksu "update-manager -c -d"

Did it for me!

---

### Post by BigWillyT on 2006-10-17
gksu "update-manager -c -d" worked like a champ for me too!  Upgrading as I typed this.  Man those are a lot of upgrades. :D  Hopefully since it's nearing final release, it'll be a little more stable than some of the threads I've read.

Just finished with the upgrade and so far so good.  Keep your fingers crossed cause now I gotta get some NVIDIA drivers installed. :)

---

### Post by hotani on 2006-10-20
Just tried it on my laptop and got:

```

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

```

When I tried it on my work machine it completely hosed the window manager because of some language file. So far 0 for 2, not doing so hot.

---

### Post by doobit on 2006-10-20
> **hotani said:**
> Just tried it on my laptop and got:

```

Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.

```

When I tried it on my work machine it completely hosed the window manager because of some language file. So far 0 for 2, not doing so hot.

That was pretty much my experience. I'm gonna try to reinstall Dapper.

---

### Post by hotani on 2006-10-20
I did install it on the work machine that failed, but did it clean. So far I have not seen an "update" actually work.

---

### Post by hotani on 2006-10-20
[BUG 1](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/58424), [BUG 2](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/67103)

Looks like it has something to do with compiz - yikes.

from the comments in bug 58424, this fixed it for me: Run these before doing the upgrade:
> 
$ sudo dpkg -r --force-depends libgl1-mesa libgl1-dev libgl1-dri libglu1-mesa libglu1-mesa-dev mesa-common-dev mesa-utils
$ sudo apt-get install -f


---

### Post by Tobster on 2006-10-20
guys

I been told that the release date is not until 22 or the 26 October

---

### Post by hotani on 2006-10-20
yes that is correct - this is RC1 I believe.

---

### Post by nicjasno on 2006-10-23
After doing the upgrade, except in firefox, xchat and console all i got instead of fonts are squares, all looking exactly the same. WTF!? How can i solve this without reinstalling...?!

---

