---
title: "Upgrade to 21.04 - no reaction..."
date: 2021-07-31
forum: General Help
---

### Post by 2CV67 on 2021-07-31
Software Updater today tells me there are no further updates available for my Ubuntu 20.10 & I should upgrade to 21.04.

But when I click on "Upgrade" - there is no reaction, except Software Updater closes.
I tried this 3 times.

I searched a bit & saw there had been serious problems with 21.04 & that upgrades would not be pushed until those problems had been fixed.

Have they been fixed now?

Any idea what is happening for me?

Thanks!

---

### Post by Impavidus on 2021-07-31
The upgrade from 20.10 to 21.04 was delayed, but has been available for a while. I upgraded (just checking my logs...) on 7 June.

Check your settings. Software & Updates &#8594; Updates &#8594; Notify of new versions of Ubuntu must be set to every new version. You can also start the release upgrade from command line: sudo do-release-upgrade

Also see [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades). If you installed all upgrades released before end-of-life of 20.10, the do-release-upgrade step should be the only one you need.

Don't spend too much time troubleshooting this, or a fresh install will be easier.

---

### Post by 2CV67 on 2021-08-06
Thanks for your comments, Impavidus.

My Software Updater settings now include "Notify for any new version".

I tried to start from the command line (which I normally try to avoid!) but with no success:
```
chris@AcerTC:~$ do-release-upgrade
Checking for a new Ubuntu release
Your Ubuntu release is not supported anymore.
For upgrade information, please visit:
http://www.ubuntu.com/releaseendoflife

Please install all available updates for your release before upgrading.
chris@AcerTC:~$ 
```
As far as I know, I have installed all available updates until Updater told me no new updates were provided for 20.10, but I don't know how to confirm this...

The various links to "releaseendoflife" are not exactly clear, even for somebody using Ubuntu since 2006!

I realize I can scrap 20.10 & make a fresh install of 21.04 (or 20.04LTS?) but I would still prefer to upgrade if at all possible.
Does it seem impossible?

Thanks for any further simple advice!

---

### Post by Impavidus on 2021-08-07
If the repositories are still available on the regular server, a simple```
sudo apt update
sudo apt full-upgrade
``` should do it. If the repositories are no longer available, it will tell so in an error message and you can change the server to old-releases, as explained in the link in post #2. Then try again.

If there's some other problem, it should at least give an error message.

---

### Post by 2CV67 on 2021-08-07
Thanks very much, Impavidus, for your continued help!

I ran sudo apt update:
```
chris@AcerTC:~$ sudo apt update
[sudo] password for chris: 
Hit:1 http://fr.archive.ubuntu.com/ubuntu groovy InRelease
Hit:2 http://fr.archive.ubuntu.com/ubuntu groovy-updates InRelease
Hit:3 http://fr.archive.ubuntu.com/ubuntu groovy-backports InRelease
Hit:4 http://security.ubuntu.com/ubuntu groovy-security InRelease
Reading package lists... Done                             
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
chris@AcerTC:~$ sudo apt list --upgradable
Listing... Done
dh-python/groovy,groovy 4.20200925 all [upgradable from: 4.20191017ubuntu7]
N: There is 1 additional version. Please use the '-a' switch to see it
chris@AcerTC:~$ sudo apt list --upgradable -a
Listing... Done
dh-python/groovy,groovy 4.20200925 all [upgradable from: 4.20191017ubuntu7]
dh-python/now 4.20191017ubuntu7 all [installed,upgradable to: 4.20200925]

chris@AcerTC:~$ 
```
I opened Synapt & saw there were "no packages broken or to install/upgrade or remove".
But when I searched for dh-python, Synapt did confirm the possible upgrade from 4.2019.. to 4.2020..
So I upgraded that, then tried Software Updater again & this time it worked quite normally.
Don't know why Synaptdidn't flag that potential upgrade.

I am now running 21.04 successfully.

Thanks again!

---

