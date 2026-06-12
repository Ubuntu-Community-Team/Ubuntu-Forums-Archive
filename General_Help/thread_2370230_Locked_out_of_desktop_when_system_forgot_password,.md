---
title: "Locked out of desktop when system forgot password, but terminal still recognizes it"
date: 2017-08-31
forum: General Help
---

### Post by gbambo on 2017-08-31
My Ubuntu installations are routinely unusable from the outset. Yet, I have been admonished not to claim this is one problem and to instead spawn a multitude of postings. So here goes.

[COLOR=#000000]Incident Ia. Install of 17.04 minimal server. Then manual upgrade to Ubuntu-Desktop with "no-recommends" switch. Cannot find a menu for launching programs to save my life. Googling around I see references to several desktop interface elements I cannot find. Shortly thereafter I uninstalled Ubuntu-Desktop and installed Enlightenment. Result? I can log into via a terminal mode SSH session, but If I remote in graphically the Ubuntu-Desktop sign-in does not recognize those same credentials. Only one user (other than root.) Password was never changed. 

And why is there an Ubuntu-Desktop sign-in and not an Enlightenment sign-in? Changing pw does not help. Isn't the same underlying service being called in both cases?[/COLOR]

[COLOR=#000000]I am no noob. I was the Director of IT for a $20M company. But I am no Linux expert either. Something weird is happening that spans all my installs. Each results in a system crippled in an entirely different way.

[/COLOR][COLOR=#000000]Context. All installs were to the same physical server (I only have access to one) and done to bare metal. Each incident involved re-downloading the install image (so it cannot involve a single incident of corruption). In some cases a, different mirror was used. No install survived more than a day or two before being abandoned.[/COLOR]

[COLOR=#000000]Am I mistaken in my belief that nothing beyond disk structures (partitions, LVM, RAID arrays) can survive a reinstall? The installer claims to be reformatting all volumes.[/COLOR]

---

### Post by gbambo on 2017-09-02
Seriously, no one has any comment on how two different interfaces to the same system have two different opinions as to what a single user's password is? It seems to me this is a bug and not user error. Or is someone aware that it an arcane feature?

---

### Post by ChuangTzu on 2017-09-02
if you want to install an ubuntu server then install that from the net/minimal install, if you need a GUI/DE then install a minimal one only and build up.  IE: ```
sudo apt install enlightenment
``` if this does not bring in a display manager then ```
sudo apt install lightdm
``` that should be enough as enlightenment and lightdm should bring in xorg etc...

None of that will cause a change to your password, user or root if you enabled root password.

---

### Post by gbambo on 2017-09-03
I agree none of what I did should change my password. And I proved my password did not change at the CLI. But my password is not recognized on the desktop. I tried to login over 20 times. My complaint is that something went wrong and I want to fix it. Your instructions do not fix anything and only reinforce my belief I did not contribute to the issue.

---

### Post by oldos2er on 2017-09-03
> **gbambo said:**
> [COLOR=#000000]Incident Ia. Install of 17.04 minimal server. Then manual upgrade to Ubuntu-Desktop with "no-recommends" switch. [/COLOR]

ubuntu-desktop is a [metapackage]("https://help.ubuntu.com/community/MetaPackages"), not sure why you would want it without its dependencies; installing it that way defeats its entire purpose. It's possible some missing component is causing your problem(s).

---

### Post by gbambo on 2017-09-03
There is a very good chance that you are right and I made a dumb choice. But that observation does not justify the result. I installed a package with valid switches and then remove the package a day later and my system was essentially destroyed. That should not occur. How could missing components in the install of Ubuntu-Desktop be the explanation of why my system does not work after uninstalling Ubuntu-Desktop? All the components of U-D are supposed to be missing in that scenario.

There are more ways to hang yourself with Linux than are dreamt of in the nightmares of Windows users. And that's fine because there are counterbalancing virtues. But I do wish the "it's as easy as a Mac" crowd would shut-up. That claim is just delusional.

In the last week, 1/3 of my installs were unusable from the moment the installer completed a fresh install. The last time that happened to me with Windows was in the last century.

I have tried installing a desktop (usually whole) on top of various distros several times in the last month. It is phenomenally difficult. I don't think any worked perfectly. This is a relatively simple task on Windows, where I have never seen it fail.

A big problem with Linux is there are few up-to-date guaranteed to work tutorials. This may be an unavoidable consequence of the extreme heterogeneity of the Linux world. But it does make many comparisons to other operating systems a little less than honest.

I really want to consider it as a primary personal OS though, as I am finding licensed software taxing on my budget. But it seems a successful conversion would take years if I expected to achieve equal levels of competence. Moving from Windows to Mac (a *nix derivative) is almost an order of magnitude less complex.

---

### Post by grahammechanical on 2017-09-03
Strictly speaking Ubuntu does not have a Ubuntu desktop sign in but a LightDM sign in. Once we log in the Gnome 3 desktop environment should load along with the Unity user interface.

If we install an alternative desktop environment with its own user interface then we get options at the LightDM log in screen. The password panel will have a Ubuntu icon that will present a menu when clicked. And from the menu we will have the option to login to Ubuntu or the alternative desktop environment with its user interface.

I can only guess that when you installed the Ubuntu desktop without the recommended dependent packages that you may have failed to install the Unity 7 user interface which would have included a side panel (Launcher) on the left that would launch a few default applications and a Ubuntu icon at the top that opens the Dash from which we load/launch other installed applications.

Your install may also be lacking a password word manager.

Regards

---

### Post by gbambo on 2017-09-03
Thank you for the clarifications. I did have the Unity 7 user interface though, as I had the launcher and icons you describe. But those were the only applications I could access, even after I installed additional applications. The no-recommended switch was clearly the source of many of my problems though. And notwithstanding the poor choice of invoking no-recommends, I still feel it is a bit buggy than uninstalling one desktop and installing another result in zero access to a desktop. Maybe I overestimate how many circumstances a good install script can manage. I look forward to a day in the near future when I succeed in installing and configuring Ubuntu.

---

### Post by again? on 2017-09-03
Have a look at what's missing when you use "--no-install-recommends".
```
apt depends ubuntu-desktop | grep -i recommends
```

> **gbambo said:**
> How could missing components in the install of Ubuntu-Desktop be the explanation of why my system does not work after uninstalling Ubuntu-Desktop?
ubuntu-desktop is a [metapackage]("https://help.ubuntu.com/community/MetaPackages") and as such does not contain any software. It is just a list of dependencies.
Uninstalling the ubuntu-desktop metapackage, removes the list. Any packages pulled in by ubuntu-desktop remain on your system.
Logical thinking is flawed when you don't have the appropriate knowledge.

---

