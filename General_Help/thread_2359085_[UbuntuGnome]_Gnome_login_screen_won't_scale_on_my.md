---
title: "[UbuntuGnome] Gnome login screen won't scale on my HiDPI display"
date: 2017-04-20
forum: General Help
---

### Post by jefferson9 on 2017-04-20
Ubuntu gnome 17.04 (gnome 3.24), I have a laptop with a high resolution display. My desktop scaled fine by default without any configuration. But my login screen, everything is too small to read. 

**Edit: **solved, see [https://ubuntuforums.org/showthread.php?t=2359085&page=2&p=13637852#post13637852](https://ubuntuforums.org/showthread.php?t=2359085&page=2&p=13637852#post13637852)

What i've tried:

```

sudo xhost +SI:localuser:gdm
sudo su gdm -s /bin/bash
gsettings set org.gnome.desktop.interface scaling-factor 2

```
mouse pointer gets bigger, no change to window or text

I've tried editing 
```

/usr/share/glib-2.0/schemas/org.gnome.desktop.interface.gschema.xml

```
and changing the default value for scaling-factor to 2, and recompiling schemas
```

sudo glib-compile-schemas /usr/share/glib-2.0/schemas

```
mouse pointer gets bigger, no change to window or text

I've tried adding scaling-factor=2 under [org/gnome/desktop/interface] in this override file
```

/usr/share/glib-2.0/schemas/20_ubuntu-gnome-default-settings.gschema.override

```
and recompiling schemas, no change just mouse pointer.

And i've tried creating a new user for gdm under /etc/dconf/:
```

/etc/dconf/profile/gdm

user-db:user
system-db:gdm

/etc/dconf/db/gdm.d/10-scaling

[org/gnome/desktop/interface]
scaling-factor=2

```
and running 
```

sudo dconf update

```
again no change to text or windows, only mouse pointer.

I've also tried changing text-scaling-factor in the ALL OF THE ABOVE methods and it makes no change.

Why can't I make my login screen scale properly? If anyone has any info it would be great appreciated. I'm wondering if I should submit a bug report?

Thanks

---

### Post by polrus on 2017-04-21
I have the same problem - in 16.10 it worked fine

---

### Post by doubled on 2017-04-21
I recently purchased a high resolution (3200 x 1800) laptop, and have notice the same issue. 

In addition to the login screen, the sliding panel on the lower left has a Dropbox icon I can identify and two others -- one very, very tiny (unidentifiable) and another that has only a placeholder as best I can tell. 

Changing the resolution to 1920 x 1080 lets me know that the very, very tiny icon is a Chromium Browser icon, while the placeholder does not contain an icon, though right-clicking lets me know what it is from the menu. 

At the same time, ironically, the dock icons are actually smaller at this new resolution, as is the page into which I am typing this. Go figure.

---

### Post by jefferson9 on 2017-04-21
I found this gnome bugzilla [https://bugzilla.gnome.org/show_bug.cgi?id=780208](https://bugzilla.gnome.org/show_bug.cgi?id=780208) (site seems to be extremely slow)

Original report was from gnome 3.22 and they claim 3.24 fixed it. I'm currently have the problem on 3.24 though.

---

### Post by doubled on 2017-04-22
As am I.

---

### Post by mc4man on 2017-04-22
It would appear that the fix is not in the version of gnome-settings-daemon used in 17.04 nor in a new build in 17.04 -proposed.
query here - [https://ubuntuforums.org/showthread.php?t=2359293&p=13636459#post13636459](https://ubuntuforums.org/showthread.php?t=2359293&p=13636459#post13636459)

---

### Post by jefferson9 on 2017-04-22
> **mc4man said:**
> It would appear that the fix is not in the version of gnome-settings-daemon used in 17.04 nor in a new build in 17.04 -proposed.
query here - [https://ubuntuforums.org/showthread.php?t=2359293&p=13636459#post13636459](https://ubuntuforums.org/showthread.php?t=2359293&p=13636459#post13636459)

do you know if that fix will be included in gnome 3.24.1? and should hit the ubuntu repos soon?

---

### Post by jefferson9 on 2017-04-24
Well trying out gnome 3.24.1 (including gnome-settings-daemon 3.24.1 and gnome-shell 3.24.1) from ubuntu proposed repo and the issue still persists. It sounded like it should have been fixed in gnome-settings-daemon 3.24.1 ( [https://bugzilla.gnome.org/show_bug.cgi?id=780208](https://bugzilla.gnome.org/show_bug.cgi?id=780208) )

Fingers crossed for 3.24.2

---

### Post by mc4man on 2017-04-24
It will not be coming to 17.04 unless someone wants to pursue an SRU for gnome-settings-daemon. I don't think I'm inclined to do so. 
Otherwise fixed package is in 17.10 or will be shortly

---

### Post by jefferson9 on 2017-04-24
> **mc4man said:**
> It will not be coming to 17.04 unless someone wants to pursue an SRU for gnome-settings-daemon. I don't think I'm inclined to do so. 
Otherwise fixed package is in 17.10 or will be shortly

I'm not totally clued in on the whole upstream ecosystem and how it works with ubuntu, but I enabled the zesty proposed repo and I recieved the gnome-shell and gnome-settings-daemon 3.24.1 upgrades. It sounds like this bug was fixed after 3.24.1 was released, so shouldn't the fixes come with 3.24.2 via the proposed repo?


[https://wiki.gnome.org/ThreePointTwentyfive](https://wiki.gnome.org/ThreePointTwentyfive)

---

### Post by mc4man on 2017-04-24
> **jefferson9 said:**
> I'm not totally clued in on the whole upstream ecosystem and how it works with ubuntu, but I enabled the zesty proposed repo and I recieved the gnome-shell and gnome-settings-daemon 3.24.1 upgrades. It sounds like this bug was fixed after 3.24.1 was released, so shouldn't the fixes come with 3.24.2 via the proposed repo?


[https://wiki.gnome.org/ThreePointTwentyfive](https://wiki.gnome.org/ThreePointTwentyfive)
Glance at the thread I linked in post 6

---

### Post by mc4man on 2017-04-24
While I can't test as I've lent my 4k laptop out you may be able to use the gnome-settings-daemon packages just built for 17.10.
It appears they are the same as 17.04's with **just **the patch to fix this applied. I did install them & see no ill effects.
See here - [https://launchpad.net/ubuntu/+source/gnome-settings-daemon](https://launchpad.net/ubuntu/+source/gnome-settings-daemon)
So I downloaded 2 .debs, put in a folder, cd'ed to that folder in a terminal & installed both with
sudo dpkg -i *.deb

see screen for packages dl'ed from here for amd64 install [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu2/+build/12460693](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu2/+build/12460693)

---

### Post by jefferson9 on 2017-04-25
> **mc4man said:**
> While I can't test as I've lent my 4k laptop out you may be able to use the gnome-settings-daemon packages just built for 17.10.
It appears they are the same as 17.04's with **just **the patch to fix this applied. I did install them & see no ill effects.
See here - [https://launchpad.net/ubuntu/+source/gnome-settings-daemon](https://launchpad.net/ubuntu/+source/gnome-settings-daemon)
So I downloaded 2 .debs, put in a folder, cd'ed to that folder in a terminal & installed both with
sudo dpkg -i *.deb

see screen for packages dl'ed from here for amd64 install [https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu2/+build/12460693](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu2/+build/12460693)

Just tried it, didn't work :(


```

~$ apt search gnome-settings-daemon


gnome-settings-daemon/now 3.24.1-0ubuntu2 amd64 [installed,local]
gnome-settings-daemon-schemas/now 3.24.1-0ubuntu2 all [installed,local]

```


Any other packages I should try? I'm willing to try anything.

---

### Post by jefferson9 on 2017-04-25
New build (3.24.1-0ubuntu3) in artful proposed

[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3)
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3/+build/12475372](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3/+build/12475372)

They finally fixed the scaling problems on login screen. The developer warned against installing artful packages on zesty but I haven't found any issues yet. (see [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1685035](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1685035) )

---

### Post by mc4man on 2017-04-25
> **jefferson9 said:**
> New build (3.24.1-0ubuntu3) in artful proposed

[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3)
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3/+build/12475372](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3/+build/12475372)

They finally fixed the scaling problems on login screen. The developer warned against installing artful packages on zesty but I haven't found any issues yet. (see [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1685035](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1685035) )

It probably should be ok in 17.04, the newer package added a little extra. Apparently the last one, (3.24.1-0ubuntu2) forgot to add the patch itself, i.e. for ...3
> * Really add git_fix-gdm-plugins.patch

---

### Post by jefferson9 on 2017-04-25
> **mc4man said:**
> It probably should be ok in 17.04, the newer package added a little extra. Apparently the last one, (3.24.1-0ubuntu2) forgot to add the patch itself, i.e. for ...3

Just glad I finally have a readable login screen without reverting to gnome 3.22. All seems stable to far. Thanks for your help


> 
Would you be interesting in applying the SRU template to bug 1685035?

Is this something worth doing on my end (considering the package is already built)?

---

### Post by sunre on 2017-05-03
> **jefferson9 said:**
> New build (3.24.1-0ubuntu3) in artful proposed

[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3)
[https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3/+build/12475372](https://launchpad.net/ubuntu/+source/gnome-settings-daemon/3.24.1-0ubuntu3/+build/12475372)

They finally fixed the scaling problems on login screen. The developer warned against installing artful packages on zesty but I haven't found any issues yet. (see [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1685035](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/1685035) )

Thanks, I was looking for a fix for the last couple of weeks. This did it for me too. No issues encountered yet (ubuntu gnome 17.04, nvidia drivers).

---

