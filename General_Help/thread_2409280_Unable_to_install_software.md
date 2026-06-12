---
title: "Unable to install software"
date: 2018-12-30
forum: General Help
---

### Post by sniper8752 on 2018-12-30
I am trying to install xen-tools on a ubuntu 18 desktop.  The install failed, recommending that I run "apt --fix-broken install".  After doing this, I get this error message:

[ATTACH=CONFIG]282056[/ATTACH]

---

### Post by Bashing-om on 2018-12-30
sniper8752; Well ,,,

You have 72 packages to be updated:
and an elevated version of xe-guest-utilities installed.

So where is this xe-guest-utilities coming from ?
show us:
```

apt policy xe-guest-utilities

```
And then we see what it will take to get this system updated.

[INDENT]ain't nothing but a thing
[/INDENT]

---

### Post by clementc on 2019-01-01
Hi [**[COLOR=#000000]sniper8752[/COLOR]**]("https://ubuntuforums.org/member.php?u=1207702"),

[**[COLOR=#DD4814][B]Bashing-om**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=1111508")'s advice is what you should try following first.

However, if everything else fails, you could try forcing the installation of xenstore-utils with the following command, but I must warn you that there is a risk this might end up breaking your system, so do a backup of your important files first:
sudo apt-get -o Dpkg::Options::="--force-overwrite" install xenstore-utils

---

