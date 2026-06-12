---
title: "prioritize repositories?"
date: 2008-05-17
forum: General Help
---

### Post by idanool on 2008-05-17
Hello!

Is there a way to set priorities to different repositories defined in sources.list or in sources.list.d/*.list ?

I want to set highest priority to a local repository on my usb key.
somehow apt-get uses web repository for packages that I have on my local repository.

thanks.

---

### Post by ibuclaw on 2008-05-17
There is a technique called Apt-Pinning. This will fix your problem.

Open up a terminal.
And type in the following:
```

sudo touch /var/lib/synaptic/preferences
sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```
This will generate a preferences file in synaptic and link it to apts preference file, so your Pinnings are enforced throughout all of your system.

Now we've done that, now it's time to edit your preference file (This will alter both in one go).
```

sudo gedit /etc/apt/preferences

```
Then type in something like the following line:
```

Package: *
Pin: origin <path of repo>
Pin-Priority: 900

```
The "path of repo" should work when you enter the path that follows the word "deb" in your sources list, but not any lines after it.

ie:
**Pin: origin [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)**
or
**Pin: origin /var/apt/mirror/**
Should work too.

But since you are wanting to consider other repositories too.
This is what mine looks like:
```

Package: *
Pin: release a=hardy-security
Pin-Priority: 1001

Package: *
Pin: release a=hardy
Pin-Priority: 800

Package: nvidia-glx-new
Pin: version 169.12+2.6.24.12-16.34
Pin-Priority: 1001

Package: nvidia-kernel-common
Pin: version 20051028+1ubuntu8
Pin-Priority: 1001

```
Basically. Hardy-Security gets the full priority. And the main Hardy group follows.
It's set so because I have the "hardy-proposed" and "hardy-backports" repos in my source list too, but I don't want to upgrade my system to them, so keeping it like this means that packages are only installed from them when they are "needed".

The number "1001" is also across the page too. This is basically a trigger which prevents all package upgrades from other repositories to upgrade package installs from the "hardy-security" repo. And where applicable, sometimes packages are "force-downgraded" to make dependancies meet.

You'll also notice that I've pinned specific packages too. This is because games won't run on the newest version of the nvidia graphics driver. So I've locked the package at it's current stable version, and all problems with my graphics card has gone!

For more information on Pinning, [read here.]("http://wiki.debian.org/AptPinning")

Regards
Iain

---

### Post by idanool on 2008-05-17
Thanks!

I'll check this out.

---

