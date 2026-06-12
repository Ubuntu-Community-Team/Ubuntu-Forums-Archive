---
title: "This is definitely a problem (but I doubt it's a bug)"
date: 2013-02-12
forum: General Help
---

### Post by Ykun on 2013-02-12
Yesterday I installed lubuntu 12.10 on a USB stick, but it is not persistent. That seems to be a typical error and there is a fix that involves editing the file txt.cfg. To do that I tried to install gedit, first using terminal then using the lubuntu software center - here are the results:

1) using terminal:

[COLOR=Purple]The following packages have unmet dependencies:
 gedit :
Depends : libpeas-1.0-0 (>= 1.1.0) but it is not going to be installed
Depends : python-gi-cairo (>=3.0) but it is not going to be installed
Depends : gir1.2-peas-1.0 but it is not going to be installed
E: Unable to correct problems,you have held broken packages.[/COLOR]


2) using the lubuntu software center:

[COLOR=Purple]Package dependencies cannot be resolved

This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

Details
The following packages have unmet dependencies:
gedit: Depends: python (< 2.8) but 2.7.3-0ubuntu7 is to be installed
       Depends: libice6 (>= 1:1.0.0) but 2:1.0.8-2 is to be installed[/COLOR]

So what is a newcomer to do?:(

TIA for helpful hints

PS: dear moderators: please move this to a better forum if it is not in the right place here - thanks

---

### Post by Ykun on 2013-02-13
I fixed the problem in a roundabout way: when using the installation on the first USB stick to create another one on a second USB stick, I checked the box "download updates while installing" (or something to that effect), and on the new installation I was able to install gedit via apt-get install (I imagine that there was some necessary updating going on during the installation). So I just seem to have got lucky without understanding what was/is going on...;)

---

### Post by oldfred on 2013-02-13
If it is a liveCD on flash without persistence you cannot update or save anything. You run it just like a liveCD, can add some things as long as they fit into RAM, but liveCD is not update-able. 

But since you can write to flash drives, you can add persistence if you have extra space. Then you can write your data, do some updates, but live version is not changed or upgradable. 

Did you do a full install with your second install? If flash drive is larger 8GB or more a full install is possible.

       Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

    With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

    Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)

---

### Post by snowpine on 2013-02-13
I believe you could have solved the "apt-get install gedit" problem by first executing:

```
sudo apt-get update
```

---

### Post by Ykun on 2013-09-04
> **snowpine said:**
> I believe you could have solved the "apt-get install gedit" problem by first executing:

```
sudo apt-get update
```

Thanks to both oldfred and yourself for the replies!
(I got sidetracked by life and neglected to come back here to check for follow-ups; thus my late reaction.)

---

