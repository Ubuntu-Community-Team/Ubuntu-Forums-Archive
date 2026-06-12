---
title: "Help Completely Removing Virtual Package Wine?"
date: 2020-05-27
forum: General Help
---

### Post by rebeltaz on 2020-05-27
I installed wine-stable and now I cannot get it completely removed. I have run purge wine and purge wine32 as well as purge wine-stable. That got rid of everything except this - "Virtual packages like 'wine' can't be removed" 

How do I get rid of that?!

---

### Post by monkeybrain20122 on 2020-05-27
[https://askubuntu.com/questions/1131997/not-sure-if-wine-was-actually-uninstalled](https://askubuntu.com/questions/1131997/not-sure-if-wine-was-actually-uninstalled)

---

### Post by rebeltaz on 2020-05-27
> **monkeybrain20122 said:**
> [https://askubuntu.com/questions/1131997/not-sure-if-wine-was-actually-uninstalled](https://askubuntu.com/questions/1131997/not-sure-if-wine-was-actually-uninstalled)

I did that, too, and I get:

```
sudo apt-get purge wine*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package winehq.key
E: Couldn't find any package by glob 'winehq.key'
E: Couldn't find any package by regex 'winehq.key'

```

---

### Post by rebeltaz on 2020-06-07
bump?

---

### Post by T6&amp;sfpER35% on 2020-06-07
```
[COLOR=#242729][FONT=Consolas]sudo apt-get purge wine\*[/FONT][/COLOR]
```

have you tried this ?
like in [COLOR=#000000]monkeybrain20122 suggestion,,,if you've read to the end of that thread[/COLOR]

---

### Post by rebeltaz on 2020-06-07
> **3nd said:**
> ```
[COLOR=#242729][FONT=Consolas]sudo apt-get purge wine\*[/FONT][/COLOR]
```

have you tried this ?
like in [COLOR=#000000]monkeybrain20122 suggestion,,,if you've read to the end of that thread[/COLOR]

I have. I tried everything in that thread:

```

sudo apt-get purge wine\*

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'winetricks' for glob 'wine*'
Note, selecting 'wine-devel-amd64' for glob 'wine*'
Note, selecting 'wine1.9-amd64' for glob 'wine*'
Note, selecting 'wine-staging-compat' for glob 'wine*'
Note, selecting 'wine-devel' for glob 'wine*'
Note, selecting 'winefish' for glob 'wine*'
Note, selecting 'wine-binfmt' for glob 'wine*'
Note, selecting 'wine32-preloader:i386' for glob 'wine*'
Note, selecting 'wine32-development-tools' for glob 'wine*'
Note, selecting 'wine-devel-dbg' for glob 'wine*'
Note, selecting 'wine-devel-dev' for glob 'wine*'
Note, selecting 'wine64-development' for glob 'wine*'
Note, selecting 'wine-stable-dbg' for glob 'wine*'
Note, selecting 'wine-stable-dev' for glob 'wine*'
Note, selecting 'winehq-devel' for glob 'wine*'
Note, selecting 'wine1.9-i386:i386' for glob 'wine*'
Note, selecting 'wine1.4-amd64' for glob 'wine*'
Note, selecting 'wine-staging-i386' for glob 'wine*'
Note, selecting 'wine64-preloader' for glob 'wine*'
Note, selecting 'wine1.8-dev' for glob 'wine*'
Note, selecting 'wine64-development-tools' for glob 'wine*'
Note, selecting 'wine1.6-dev' for glob 'wine*'
Note, selecting 'wine1.8-i386:i386' for glob 'wine*'
Note, selecting 'wine1.0' for glob 'wine*'
Note, selecting 'wine1.2' for glob 'wine*'
Note, selecting 'wine1.3' for glob 'wine*'
Note, selecting 'wine1.4' for glob 'wine*'
Note, selecting 'wine1.5' for glob 'wine*'
Note, selecting 'wine1.6' for glob 'wine*'
Note, selecting 'wine1.7' for glob 'wine*'
Note, selecting 'wine1.8' for glob 'wine*'
Note, selecting 'wine1.9' for glob 'wine*'
Note, selecting 'wine1.5-amd64' for glob 'wine*'
Note, selecting 'wine2.0' for glob 'wine*'
Note, selecting 'wine32-development' for glob 'wine*'
Note, selecting 'wine1.4-dev' for glob 'wine*'
Note, selecting 'wine-dev' for glob 'wine*'
Note, selecting 'wine-devel-i386' for glob 'wine*'
Note, selecting 'wine1.7-i386' for glob 'wine*'
Note, selecting 'wine1.6-amd64' for glob 'wine*'
Note, selecting 'wine-development' for glob 'wine*'
Note, selecting 'wine32-tools' for glob 'wine*'
Note, selecting 'wine1.6-i386' for glob 'wine*'
Note, selecting 'wine-stable' for glob 'wine*'
Note, selecting 'wine32' for glob 'wine*'
Note, selecting 'wine64' for glob 'wine*'
Note, selecting 'wine1.5-i386' for glob 'wine*'
Note, selecting 'winehq-stable' for glob 'wine*'
Note, selecting 'wine-staging' for glob 'wine*'
Note, selecting 'wine-i386' for glob 'wine*'
Note, selecting 'wine1.4-i386' for glob 'wine*'
Note, selecting 'wine-staging-dbg' for glob 'wine*'
Note, selecting 'wine64-development-preloader' for glob 'wine*'
Note, selecting 'wine-staging-dev' for glob 'wine*'
Note, selecting 'wine-stable-i386' for glob 'wine*'
Note, selecting 'wine-staging-amd64' for glob 'wine*'
Note, selecting 'winehq-staging' for glob 'wine*'
Note, selecting 'wine1.7-amd64' for glob 'wine*'
Note, selecting 'wine' for glob 'wine*'
Note, selecting 'wine1.9-dev' for glob 'wine*'
Note, selecting 'wine-stable-amd64' for glob 'wine*'
Note, selecting 'wine-amd64' for glob 'wine*'
Note, selecting 'wine1.7-dev' for glob 'wine*'
Note, selecting 'wine1.5-dev' for glob 'wine*'
Note, selecting 'wine64-tools' for glob 'wine*'
Note, selecting 'wine1.8-amd64' for glob 'wine*'
Note, selecting 'wine32-development-preloader:i386' for glob 'wine*'
Note, selecting 'wine32-tools:i386' instead of 'wine32-tools'
Note, selecting 'wine32-development-tools:i386' instead of 'wine32-development-tools'
Note, selecting 'wine1.6' instead of 'wine1.8'
Package 'wine1.9' is not installed, so not removed
Package 'wine2.0' is not installed, so not removed
Note, selecting 'wine32-development:i386' instead of 'wine32-development'
Package 'wine1.0' is not installed, so not removed
Package 'wine1.2' is not installed, so not removed
Package 'wine1.3' is not installed, so not removed
Note, selecting 'wine1.6-amd64' instead of 'wine1.8-amd64'
Package 'wine1.9-amd64' is not installed, so not removed
Note, selecting 'wine1.6-dev' instead of 'wine-dev'
Note, selecting 'wine1.6-dev' instead of 'wine1.4-dev'
Package 'wine1.5-dev' is not installed, so not removed
Note, selecting 'wine1.6-dev' instead of 'wine1.7-dev'
Note, selecting 'wine1.6-dev' instead of 'wine1.8-dev'
Package 'wine1.9-dev' is not installed, so not removed
Note, selecting 'wine1.6-i386:i386' instead of 'wine1.8-i386:i386'
Package 'wine1.9-i386:i386' is not installed, so not removed
Note, selecting 'wine-devel-i386:i386' instead of 'wine-devel-i386'
Note, selecting 'wine-stable-i386:i386' instead of 'wine-stable-i386'
Note, selecting 'wine-staging-i386:i386' instead of 'wine-staging-i386'
Package 'wine-binfmt' is not installed, so not removed
Package 'wine-development' is not installed, so not removed
Package 'wine1.6' is not installed, so not removed
Package 'wine1.6-amd64' is not installed, so not removed
Package 'wine1.6-dev' is not installed, so not removed
Package 'wine64' is not installed, so not removed
Package 'wine64-development' is not installed, so not removed
Package 'wine64-development-preloader' is not installed, so not removed
Package 'wine64-development-tools' is not installed, so not removed
Package 'wine64-preloader' is not installed, so not removed
Package 'wine64-tools' is not installed, so not removed
Package 'winefish' is not installed, so not removed
Package 'winetricks' is not installed, so not removed
Package 'wine32-development-preloader:i386' is not installed, so not removed
Package 'wine32-preloader:i386' is not installed, so not removed
Package 'wine-devel-amd64' is not installed, so not removed
Package 'wine-devel-dbg' is not installed, so not removed
Package 'wine-devel-dev' is not installed, so not removed
Package 'wine-devel' is not installed, so not removed
Package 'wine-stable-amd64' is not installed, so not removed
Package 'wine-stable-dbg' is not installed, so not removed
Package 'wine-stable-dev' is not installed, so not removed
Package 'wine-stable' is not installed, so not removed
Package 'wine-staging-amd64' is not installed, so not removed
Package 'wine-staging-compat' is not installed, so not removed
Package 'wine-staging-dbg' is not installed, so not removed
Package 'wine-staging-dev' is not installed, so not removed
Package 'wine-staging' is not installed, so not removed
Package 'winehq-devel' is not installed, so not removed
Package 'winehq-stable' is not installed, so not removed
Package 'winehq-staging' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.

```

```

sudo apt-get purge wine

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'wine' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.

```

---

### Post by T6&amp;sfpER35% on 2020-06-07
[https://askubuntu.com/questions/1111353/unable-to-remove-wine](https://askubuntu.com/questions/1111353/unable-to-remove-wine)

[https://www.reddit.com/r/linux4noobs/comments/9wre7p/mint_19_ubuntu_i_need_help_uninstalling_wine/](https://www.reddit.com/r/linux4noobs/comments/9wre7p/mint_19_ubuntu_i_need_help_uninstalling_wine/)

---

### Post by deadflowr on 2020-06-07
> Virtual packages like 'wine' can't be removed

Virtual packages don't exist as packages.
They're typically built into other existing packages.
If you tried installing "wine" it would state *no installation candidate exists* and possibly list a few package that might be what you want.
run
```
dpkg -l | grep wine
```
Itll most likely show as empty.

Fwiw, you get the same message for virtual packages whether or not you have or had a particular package installed or not.

---

### Post by rebeltaz on 2020-06-08
> **deadflowr said:**
> 
```
dpkg -l | grep wine
```
Itll most likely show as empty.


It does.

> **deadflowr said:**
> 
Fwiw, you get the same message for virtual packages whether or not you have or had a particular package installed or not.

So chances are that everything I've done has removed wine from my system? Why doesn't it just say that the package is not installed rather than "Virtual packages like 'wine' can't be removed"? That'd be a lot more obvious and accurate. 

Meh... Thanks guys for y'alls help.

---

