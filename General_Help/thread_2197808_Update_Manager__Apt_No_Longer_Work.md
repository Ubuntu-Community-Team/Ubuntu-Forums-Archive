---
title: "Update Manager / Apt No Longer Work"
date: 2014-01-05
forum: General Help
---

### Post by RamonBianco on 2014-01-05
Hello, ForuMembers.

I have recently found that I cannot run the Update Manager any more.  I'm running Ubuntu 10.04.4 LTS, and uname -a gives "Linux GBubuntu 2.6.32-54-generic #116-Ubuntu SMP Tue Nov 12 19:27:09 UTC 2013 i686 GNU/Linux".

I get no response from the Update Manager GUI links, and when I try to run the underlying program in a terminal window, I get:

```
/usr/bin/update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 36, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 22, in <module>
    import apt_pkg
ImportError: /usr/lib/python2.6/dist-packages/apt_pkg.so: undefined symbol: _ZN16pkgAcquireStatus7FetchedEmm
```

Apt no longer works, either:
```

$ sudo apt-get update
[sudo] password for *^&%*&^%: 
apt-get: symbol lookup error: apt-get: undefined symbol: _system
$ sudo apt-cache search anything
apt-cache: symbol lookup error: apt-cache: undefined symbol: _system
```

Is there anything I can do to rescue my PC installation?

Thanks.

---

### Post by bapoumba on 2014-01-05
Looks like your apt is broken for some reason.
You need to reinstall it, and of course you cannot use apt-get.

Download it from here : [http://packages.ubuntu.com/lucid/apt](http://packages.ubuntu.com/lucid/apt)

Then install it with dpkg :
```
sudo dpkg -i apt_0.7.25.3ubuntu9.13_i386.deb
```

[http://ubuntuforums.org/showthread.php?t=1618789](http://ubuntuforums.org/showthread.php?t=1618789)
I'm not quite sure you need to restart for being able to use apt-get again. Might give it a try.

```
sudo apt-get update
```

---

### Post by Bucky Ball on 2014-01-05
I wouldn't have thought you'd have been able to get any updates via update manager for awhile now. 10.04 LTS reached end-of-life in April 2013. 

Might be time for an upgrade. You can get to 12.04 LTS via an update through the Update Manager. Hope the links provided by bapoumba work for you, though.

---

### Post by jamesisin on 2014-01-05
As has been said, 10.04 is dying/dead (at least in terms of updates and support).  I personally have skipped all the way to 13.10 and am eagerly awaiting 14.04 (the next LTS) because 12.04 is meager in its customizations compared to 10.04.  They will all be slightly more buggy (11.10 --> 13.10 more than 10.04) but this stands to reason since there is so much new software involved.

---

### Post by bapoumba on 2014-01-05
Thanks BB, I misread the release number..
In any case, if the OP wants to upgrade, they wont be able to use apt-get. Better do a fresh install or grab the apt package from the live cd : [http://old-releases.ubuntu.com/releases/lucid/](http://old-releases.ubuntu.com/releases/lucid/)

---

### Post by RamonBianco on 2014-01-08
Thanks, all, for your responses.
[QUOTE=bapoumba]Looks like your apt is broken for some reason.
You need to reinstall it, and of course you cannot use apt-get. . . .[/QUOTE]
I'll probably give that a try, when I can get some time, and after I take a current back-up.  That may at least cure the Apt problem, then I can tackle the Update Manager issue.
[QUOTE=Bucky Ball]I wouldn't have thought you'd have been able to get any updates via update manager for awhile now. 10.04 LTS reached end-of-life in April 2013.  Might be time for an upgrade. . . .[/QUOTE]
I was getting updates somewhat regularly even recently - kernel updates, various security patches, etc.  But it may indeed be time for an upgrade.  I prefer the LTS versions, and to keep them Long-Term, rather than doing all the intermediate upgrades.
[QUOTE=jamesisin]As has been said, 10.04 is dying/dead (at least in terms of updates and support). I personally have skipped all the way to 13.10 and am eagerly awaiting 14.04 (the next LTS) because 12.04 is meager in its customizations compared to 10.04. They will all be slightly more buggy (11.10 --> 13.10 more than 10.04) but this stands to reason since there is so much new software involved.[/QUOTE] 
Well, that's not exactly a "ringing endorsement", is it?  I had considered an upgrade, but I was not thrilled with what I heard about Unity.  But IIRC, there are Gnome editions of newer Ubuntu versions, so I might check those out, since I'm used to that interface.

Anyway, thanks again.

---

### Post by Bucky Ball on 2014-01-08
Ubuntu 12.04 has Gnome fallback if you don't like Unity. I use Xubuntu with xfce4 myself because Unity doesn't suit the way I work at all. You might want to try that. Lighter too and highly customisable.

---

### Post by jamesisin on 2014-01-09
You can install a variety of desktop environments and select from among them at the login screen.  You can find pretty easy instructions for doing so all over.  With the introduction of the Unity Tweek Tool you can get a lot of the old customizations and some new ones.  I talk a little about it here:

[http://jamesisin.com/a_high-tech_blech/index.php/2013/11/return-customizations-to-unity-in-ubuntu-13-10/](http://jamesisin.com/a_high-tech_blech/index.php/2013/11/return-customizations-to-unity-in-ubuntu-13-10/)

---

### Post by RamonBianco on 2014-02-01
Thanks again, all.  I'm still hesitating on the upgrade.  The main "tweaks" I use are personal keyboard short-cuts, like <Ctrl><Alt>X to open the spreadsheet app, etc.; I'm more of a keyboarder, not a mouse-r.  And I don't really care that much about "cool" visual effects in the GUI, I just want to get to my app with minimal effort.

But the main "scary" thing to me about upgrading Ubuntu versions is support for my "peripheral" equipment.  I'm especially concerned about support for my somewhat ancient video card (GeForce 7300 GT), and for my printers.

Anyway, I'll keep checking into things and try to get up for the upgrade.

---

### Post by Bucky Ball on 2014-02-02
I don't have icons! Every app is opened with keyboard shortcuts, and it is extremely easy to create those in xfce4. In fact, it is setup so you can!

Old hardware? I have, I think it is the 6900? nvidia in the desktop running a minimal install with xfce4 and it didn't blink. All picked up, all fine. ;)

Heck, I have an eight channel audio interface (breakout box in some circles) connected to that machine and they get along fine and I didn't need to do a thing. It just worked!

xfce4 keyboard shortcut setup:

Apps>Settings>Keyboard>Application shortcuts.

That easy. As long as you know the command to launch an app from a command line, then your app is a finger press away.

---

