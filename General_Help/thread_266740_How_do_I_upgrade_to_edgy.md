---
title: "How do I upgrade to edgy?"
date: 2006-09-27
forum: General Help
---

### Post by jsmidt on 2006-09-27
I typed:
```
sudo apt-get dist-upgrade
```

But it wants to hold back vital packages like xserver.  How do I upgrade all packages?

---

### Post by Mickeysofine1972 on 2006-09-27
I would probably do a fresh install of edgy after backing up my data.

Other than that you can edit you /etc/apt/sources.list and change every occurrence of dapper to edgy

Then do the command you already tried, however I dont know if this is a safe way to upgrade at the moment.

Mike

---

### Post by jsmidt on 2006-09-27
I discovered this works:
```
gksu "update-manager -c -d"
```

Which I found on the edgy beta wiki:

[https://wiki.ubuntu.com/EdgyEft/Beta](https://wiki.ubuntu.com/EdgyEft/Beta)

---

### Post by Dinerty on 2006-09-27
Just download the knot 3 cd and install that way, saves the need to re-download it, if things went wrong

[http://cdimage.ubuntu.com/releases/edgy/knot-3/](http://cdimage.ubuntu.com/releases/edgy/knot-3/)

---

### Post by PriceChild on 2006-09-28
Edgy is unstable! Do NOT use on any production machines or as your primary desktop.

I always advise doing a fresh install of a new OS... some say otherwise :)

Personally i've d/l and edgy cd and isntall of that.

---

### Post by ayoli on 2006-09-28
> **jsmidt said:**
> I discovered this works:
```
gksu "update-manager -c -d"
```

Which I found on the edgy beta wiki:

[https://wiki.ubuntu.com/EdgyEft/Beta](https://wiki.ubuntu.com/EdgyEft/Beta)

a friend is trying to upgrade to edgy, update-manager -c -d doesn't work. he gives a try to aptitude dist-upgrade (yeah, he loves risk :p )
wait and see :)

---

### Post by hanzomon4 on 2006-09-28
I tried gksu "update-manager -c -d" but it would fail and tell me to file a bug, so I did a sudo apt-get update and sudo apt-get upgrade. After that gksu "update-manager -c -d" stopped detecting edgy.

I'm now left with new ubuntu sounds but everything else is dapper.

Could this be the issue ```
current dist not found in meta-release file
```

---

### Post by ayoli on 2006-09-28
aptitude dist-upgrade seems to work, but have told about unmet depndencies and have suggested a solution which kept back a bunch of package such as nautilus, mplayer ...
we'll try another upgrade after reboot [-(

---

### Post by hanzomon4 on 2006-09-28
I found this in that /var/lib/update-manager/meta-release file
```
Dist: warty
Name: Warty Warthog
Version: 04.10
Date: Wed, 20 Oct 2004 07:28:17 UTC
Supported: 1
Description: This is the warty warthog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/warty/Release

Dist: hoary
Name: Hoary  Hedgehog
Version: 05.04
Date: Fri, 08 Apr 2005 08:18:19 UTC
Supported: 1
Description: This is the Hoary Hedgehog release
Release-File: http://archive.ubuntu.com/ubuntu/dists/hoary/Release

Dist: breezy
Name: Breezy Badger
Version: 05.10
Date: Thu, 13 Oct 2005 19:34:42 UTC
Supported: 1
Description: This is the Breezy Badger release
Release-File: http://archive.ubuntu.com/ubuntu/dists/breezy/Release

Dist: dapper
Name: Dapper Drake
Version: 6.06 LTS
Date: Thu, 01 Jun 2006 9:00:00 UTC
Supported: 1
Description: This is the Dapper Drake release
Release-File: http://archive.ubuntu.com/ubuntu/dists/dapper/Release
ReleaseNotes: http://changelogs.ubuntu.com/DapperReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/dapper/main/dist-upgrader-all/current/dapper.tar.gz.gpg

Dist: edgy
Name: Edgy Eft
Version: 6.10
Date: Thu, 31 Jul 2006 9:00:00 UTC
Supported: 0
Description: This is the Edgy Eft release
Release-File: http://archive.ubuntu.com/ubuntu/dists/edgy/Release
ReleaseNotes: http://archive.ubuntu.com//ubuntu/dists/edgy/main/dist-upgrader-all/current/ReleaseAnnouncement
UpgradeTool: http://archive.ubuntu.com/ubuntu/dists/edgy/main/dist-upgrader-all/current/edgy.tar.gz
UpgradeToolSignature: http://archive.ubuntu.com/ubuntu/dists/edgy/main/dist-upgrader-all/current/edgy.tar.gz.gpg

```

I tried deleting the edgy reference at the end of the file, but gksu "update-manager -c -d" still failed to detect edgy.

I feel like I'm stuck with some dapper-edgy mutant ](*,)

---

### Post by hanzomon4 on 2006-09-28
Ok I checked /var/log/dist-upgrade/main.log and found lines saying updated to new dist and ending with an error. I'm still not sure why gksu "update-manager -c -d" won't detect edgy or why I have edgy sounds. 

Changing my source.list and upgrading thorough aptitude holds too many things back. I'll attach the apt.log:EDIT: can't its too big

It seems like I'm stuck between dapper and edgy and because of this the update-manager does not recognize edgy as an update. Is there any way to reverse this?

I'll attach the main.log

---

### Post by hanzomon4 on 2006-09-28
Hell after reading the main.log I realize it was just changing my source.list to edgy, So I can do that by hand.

This is what I got from aptitude > 1064 packages upgraded, 166 newly installed, 66 to remove and 25 not upgraded Let you know if it works.

---

### Post by ayoli on 2006-09-28
after changed sources.list to edgy repos, then aptitude dist-upgrade, upgrade went fine even if some packages were kept back. then reboot and then update with the update manager, old packages removed, some missing packages fetched and installed, then reboot again, now seems to work fine, all edgy :)
infortunately, my friend has an old ati M4 (r128 ) which doesn't want to work with compiz, no eye candy for him.

---

### Post by hanzomon4 on 2006-09-28
I got it to work, but for hours I was chasing down dependinces. I had to remove and then reinstall alot of stuff. But yeah don't do this unless you don't mind the risk of spending hours working on it, althought it may be easy as cake for you as it is for some.. not me though

---

### Post by BLTicklemonster on 2006-09-29
I installed edgy on vmware and it was good enough for me to feel confident that the time to mess everything up is NOW. Therefore I have resolved to edit my sources.list and update and dist-upgrade (which is running in the background right now).

I have the edgy iso on a different hard drive (fat 32 storage drive) so if everything goes normal, I can just boot to windows and burn it and do a fresh install. Hopefully everything will go ABnormal, and I'll get an update to edgy that isn't broken.

Wish me luck!

---

### Post by orb9220 on 2006-09-29
Yep I just got done installing edgy rc1 on my p4 1.3ghz,640mb ram,fx-5200 nvidia.

The liveCD would not do my wireless even tho dapper did. But installed and worked like a champ.

Also installed the new nvidia beta drivers on dual monitors & Berly for all the fancy rotating cube,Transparency,and Jiggley Jellow windows and all. They have  a great sticky howto in the edgy forum.   [http://www.ubuntuforums.org/forumdisplay.php?f=144](http://www.ubuntuforums.org/forumdisplay.php?f=144)

So far stable need to do alot more testing, and shutdown and startup is fast.

---

### Post by JeevesBond on 2006-09-30
I'm having similar problems to those experienced by hanzomon. When I run the upgrade using ```
gksu "update-manager -c -d"
``` the update manager offers the distribution upgrade correctly, but when I select it the following error pops out:
> Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
My question is: Should I raise a bug? It tells me to, but I can imagine plenty of other people are having the same problem... Malone is going to get swamped! :(

---

### Post by jsmidt on 2006-09-30
> **JeevesBond said:**
> 
My question is: Should I raise a bug? It tells me to, but I can imagine plenty of other people are having the same problem... Malone is going to get swamped! :(

If you are told to file a bug, and if nobody has filed a bug for the same thing you might want to file it.  You should check to see if it has been previously filed, but if everyone concluded somebody else will file the bug it won't ever get filed.

---

### Post by eschreib on 2006-10-01
n00b ?: Edgy rollback.  How do revert to dapper?  I selected all 6 OS to boot into I had available, to no avail:
2.6.17-10-386
2.6.15-27-386
2.6.15-27-386

(My issue is the Xserver failor issue, and after having read and followed instructions from at least 20 post, threw in the towel (for tonight).

This thread had a lot of ideas, but to no avail:

" PLEASE READ: The Latest Updates Break the Xserver!"

---

