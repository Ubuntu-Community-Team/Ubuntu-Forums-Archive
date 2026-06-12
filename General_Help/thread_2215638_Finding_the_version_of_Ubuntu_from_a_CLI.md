---
title: "Finding the version of Ubuntu from a CLI"
date: 2014-04-07
forum: General Help
---

### Post by sideburns on 2014-04-07
Recently my sister was asked if she wanted to upgrade from Xubuntu 3.04 to 3.10 and clicked on Yes.  Nothing obvious happened, so we're not sure which version she's running.  There may be a way to tell from the Xubuntu Menu, but as an old CLI hack, I'd like to be able to find out that way, as it doesn't depend on which DE she's running.

I use Fedora, and for me it's easy because the full name of each kernel contains the release number it was compiled for.  As an example:

[joe@khorlia ~]$ uname -r
3.13.7-100.fc19.i686.PAE

The fc19 shows that I'm running Fedora 19.  Alas, Ubuntu doesn't seem to do this.  I know that there's always at least one file in /etc that has the pertinent information in it, but I don't know what Ubuntu calls it and I'd rather not go hunting around on somebody else's computer for a file that I may or may not need.  If somebody here can give me a pointer to it, I'd appreciate it because it can save time and effort later, and having the info posted here might help somebody else as well.

---

### Post by sudodus on 2014-04-07
```
lsb_release -a
```

will print something like this

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

```

While uname prints information about the kernel

I use ```
uname -a
``` to print some more information than with the option -r.

---

### Post by grahammechanical on 2014-04-07
> [COLOR=#000000]Nothing obvious happened[/COLOR]

That is very strange. Something very obvious should have happened. A lot of packages should have downloaded and then a lot of time would have been needed to install those packages and then a reboot would have been necessary and the default desktop wallpaper would have changed.

Was your sister connected to the internet when she clicked on "Yes?" Perhaps she clicked "Not now." Or something like that. I cannot imagine Ubuntu or its flavours upgrading from one version to another without that being noticed.

Regards.

---

### Post by sideburns on 2014-04-07
Yes, her computer was on-line because it's connected to our router by CAT 5 at all times.  I don't think that she clicked "Not now" because I was there watching her; is there a way to force the upgrade, as I gather that 13.04 has reached its End Of Life.

Thanx for the pointer to lsb_release; I'd not been aware of it before and will add it to my toolkit.

---

### Post by grahammechanical on 2014-04-07
The best I can suggest at the moment is to follow again the instructions here:

[http://docs.xubuntu.org/1310/migrating-upgrading.html#upgrading](http://docs.xubuntu.org/1310/migrating-upgrading.html#upgrading)

There is another way. Does this machine have a DVD drive? Then It should be possible to download a Xubuntu 13.10 ISO image and burn it to DVD disk. Then with Xubuntu 13.04 loaded put the Xubuntu 13.10 disk in the drive. It will be detected and the OS will ask if you want to use the DVD to upgrade from 13.04 to 13.10. We can do this with a USB memory stick as well.

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

Regards.

---

### Post by sideburns on 2014-04-07
We know about doing it from a DVD (Her desktop doesn't boot from USB.) but I was hoping for a way to do it from inside her current version.  Thanx, grahammechanical, for that pointer.  I've sent it off to her, and we'll probably do it tonight.

---

