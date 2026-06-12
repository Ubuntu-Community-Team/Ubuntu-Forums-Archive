---
title: "Problems with 12.04 and Gnome desktop."
date: 2014-06-12
forum: General Help
---

### Post by Randy M on 2014-06-12
I was recently forced to upgrade to 12.04, one of the latest software updates cratered 10.04. I decided to install Gnome using the instructions here: [https://www.ibm.com/developerworks/community/blogs/netcooltips/entry/how_to_return_to_classic_gnome_in_ubuntu_12_04_precise12?lang=en](https://www.ibm.com/developerworks/community/blogs/netcooltips/entry/how_to_return_to_classic_gnome_in_ubuntu_12_04_precise12?lang=en)

That machine no longer boots. I really don't have time to rebuild it this weekend, but it looks like I have no choice. In the past, Ubuntu has been solid. I'm beginning to worry.

For the record, I tried safe mode and let it repair packages. It boots part way and stops. Maybe a fresh install will work better.

---

### Post by kansasnoob on 2014-06-13
Those instructions leave a lot to be desired, this would have been better IMHO:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Are you at least able to access the login screen?

If so be sure to select Classic (no effects).

What exactly happens when you do try to boot?

I'm really just guessing here but I suppose it's possible you may have both gdm and lightdm installed :confused:

If so maybe run:

```
sudo dpkg-reconfigure lightdm
```

And be sure to select lightdm if offered a choice.

---

### Post by Impavidus on 2014-06-13
Usually upgrading is quite reliable, especially if you don't have third-party software. Upgrading a broken install however often gives you a broken install. You could better have done a fresh install of 14.04 in the first place. 12.04 only has 3 years of support left (1 for some other desktops), and you don't seem eager to upgrade. 20 minute download (depending on your connection), 20 minute install and one day to configure your system, reinstall your software and find replacements for software that is no longer supported.

---

### Post by Randy M on 2014-06-13
It starts booting and gets to the part where it's starting the CUPS printing service. At that point it locks up. I can boot using safe mode, but nothing there will allow a normal boot. I'll try the most basic boot and see if I can get to a command prompt. Thanks!

---

### Post by Randy M on 2014-06-13
> **kansasnoob said:**
> Those instructions leave a lot to be desired, this would have been better IMHO:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Are you at least able to access the login screen?

If so be sure to select Classic (no effects).

What exactly happens when you do try to boot?

I'm really just guessing here but I suppose it's possible you may have both gdm and lightdm installed :confused:

If so maybe run:

```
sudo dpkg-reconfigure lightdm
```

And be sure to select lightdm if offered a choice.

I tried that, but it just changed the owner of a directory. I'm rebuilding now and have a question in on how to proceed without doing more damage. Thanks for the suggestion.

---

### Post by QIII on 2014-06-13
I have changed the title of the thread.

It is hasty to assume that our own issues are universal.

---

### Post by Randy M on 2014-06-13
The problem wasn't with the upgrade to 12.04, the problem was with the Gnome installation. I have no idea what happened, but a rebuild is underway. This will be a complete re-install and not a repair or update.

---

### Post by Randy M on 2014-06-13
> **QIII said:**
> I have changed the title of the thread.

It is hasty to assume that our own issues are universal.

Quite true, The title should have included "Don't try it this way."

---

### Post by slickymaster on 2014-06-13
I've merged your [similar thread]("http://ubuntuforums.org/showthread.php?t=2229399") with this one and deleted a duplicated post.

Please do not create duplicate threads, it dilutes community effort.

---

### Post by Bucky Ball on 2014-06-13
*Thread moved to **Ubuntu, Linux and OS Chat**.*

Not a support request. If you want help with anything please post a new thread with a descriptive title in the appropriate forum. Good luck.

(For the record, gnome desktop environment is in the repos. Think you could have installed it from Software Centre. Always look there first. You might like to also try xfce4. Much more of a gnome feel. Maybe even try an Xubuntu install. It is more pared back and faster than Ubuntu. Xubuntu has three years LTS support, so 12.04 reaches EOL in April 2015.)

---

### Post by deadflowr on 2014-06-13
Even I, who is a huge supporter of the upgrade method, would say don't try to upgrade already messed up machines, go the fresh install in that case. But that's water under the bridge now.

That said all you need, as Kansasnoob point out in the link is to install gnome-panel.
If you want to install a tweak tool, then simply install gnome-tweak-tool, which will pull in the gnome-panel with it.

The NO effects(metacity option) works out of the box.
From what I remember, the effects(compiz option) needed some initial tweaking because, if I remember right was loading compiz as if no plugin were loading.
To fix, if I remember right, I loaded compiz with
```
compiz --replace
```
which loaded unity.
I then opened the program ccsm and disable unity plugin and re-enabled the plugins I wanted to use, such as cube and 3d windows(which still worked on 12.04!!)
After I set those, gnome classic with effects has worked correctly ever since. Well over a year now.

All that said, the no effects option is simply much easier to deal with.

As well, I have no clue as to whether or not anything I said will be useful, but I hope it is.

---

