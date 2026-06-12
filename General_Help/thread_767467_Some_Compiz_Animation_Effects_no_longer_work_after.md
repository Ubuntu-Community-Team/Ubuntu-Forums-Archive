---
title: "Some Compiz Animation Effects no longer work after upgrading to 8.04"
date: 2008-04-25
forum: General Help
---

### Post by VictorR on 2008-04-25
I used Update Manager to upgrade my system from Ubuntu 7.10 to 8.04 yesterday. Then I found that all last lines of Compiz Fusion Animation plugin settings were missed. Say, for Focus effect it looked like this:
None  50  (class=Wine) & (name=Picasa2.exe)
None  50  (class=Lazarus) | (class=Gimp)
Dodge 428 (type=Normal | Dialog | ModalDialog | Utility | Unknown) <<--- this line was lost.

If I clicked New the dialog appeared with the missing settings (Dodge effect, as above), so I saved them and seemed recovered.
But It does not work.

Regex matching is enabled. Two effects - Minimize and Shade had only one line of settings each, they continue to work, but others don't.

 Any ideas?

---

### Post by Zorael on 2008-04-25
I'm not sure of the cause, but the standard workaround for all upgrader Compiz issues would be to completely remove it and reinstall. You wouldn't lose your settings, but if you want to make sure, Export them first, under Preferences.

Open up Synaptic, search for Compiz and mark the installed packages for **Complete** Removal. Important.

```
$ sudo apt-get autoremove --purge compiz* libcompiz* libdeco* emerald* libemerald*
```


Then reinstall.

---

### Post by VictorR on 2008-04-28
Thanks, but it did not work.
Seems, if I remove all settings for a particular kind of animation, and then add them one by one, testing the result every time, it will work. Probably, something changed in parsing, so Compiz did not understand old settings.

---

### Post by mgmiller on 2008-04-28
I'm having the same problem.  How did you get the minimize and shade options to work again?  I tried adding in 1 item at a time, but nothing had any effect.

---

### Post by toallpointswest on 2008-04-28
I'm having the same problem over here.  The effects work initially but nearly immediately afterwords the animation plugin will not stay enabled. 

I'm using the Ubuntu provided ATI driver (8.3) on a X1950XT card

---

### Post by VictorR on 2008-04-29
Sorry, I was wrong. If there is more, than one line in the effect settings, the only top one is executed, the rest is just ignored. For Open/Close animation it is not good, because what suitable for main application windows can be pretty annoying for tooltips and menus.

---

### Post by VictorR on 2008-04-29
Actually it works, but may have some stronger restrictions, than before.

Talking about Animation plug-in and its effects.
If one has the same rule in two lines (for example: type=Normal for two different effects), nothing will likely work.
I also got the completely frozen system, when one line contained only type=... rules, while another only class=.. rules. So I changed the second rule to
(type=Normal & (class=Gimp) | (class=Lazarus)) to get it working. I think the type=... rule MUST be in every effect setting, as this is the default rule.

So the animation effects work in general, the new guide is found here:
[http://wiki.compiz-fusion.org/WindowMatching]("http://wiki.compiz-fusion.org/WindowMatching")

For example, below are my settings for Close animation:
```
<Effect>    <Duration>  <Window Match>
Fade          100      (type=Tooltip | Notification | Utility)
Fade          366      (type=Menu | PopupMenu | DropdownMenu | Dialog | ModalDialog)
Zoom          664      ((type=Normal | Unknown) | name=sun-awt-X11-XFramePeer | name=sun-awt-X11-XDialogPeer) & !(role=toolTipTip | role=qtooltip_label) & !(type=Normal & override_redirect=1) & !(name=gnome-screensaver)
```

---

### Post by josh2112 on 2008-05-09
Mine was exhibiting odd behavior too... I could import some previously-saved settings from a file and things worked fine, but if I changed certain values random things like window close animations stopped working.

I found out via another thread on the forums (don't have a link, sorry) that the KDE and GConf Configuration Backends are both buggy.  The strange behaviour above is in Kubuntu, but I was using Ubuntu last week and having a problem trying to assign window move to <Alt>Button1 and window resize to <Control>Button1 at the same time.

Once I changed the configuration backend to Flat File (on both distros), these problems went away.

---

### Post by Slarty Bardfast on 2008-05-09
Not sure if this is related or not.  I haven't checked all the animations but come to think of it I may be seeing less since the upgrade to Hardy.  Another thing I noticed is when I try to enable the 3D window plug in, it checks off for about 2 seconds and then unchecks itself.  I tried to enable error notifications for a clue as to what might be going on and the same thing happened! Anyone know if there are some compiz logs stored around or a way to run the 3D Windows plugin from the command line to see what errors are thrown? Any tips would be appreciated, thanks!

---

### Post by mgmiller on 2008-05-09
After upgrading from Gutsy to Hardy, I had all kinds of weird things happening in the ccsm.  Window blinds stopped working and I couldn't enter any changes reliably.

This is how I fixed it:
I did a complete uninstall of compizconfig-settings-manager.

Then I installed simple-ccsm.  This has the old ccsm as a dependency, so it will reinstall itself.

Problems were all solved.

---

### Post by CMEPTb on 2008-06-18
to fix dodge animation, I just had to press "Restore Defaults" (button with a scrambled paper in lower right corner of "Focus Animation") and then edit the entry to change from "Fade" to "Dodge" type. 

So yeah, I guess it's some change in Window rules. Might help in other animations, too.

---

