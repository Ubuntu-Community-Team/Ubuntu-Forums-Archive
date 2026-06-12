---
title: "Implications of installing &quot;stuff&quot;"
date: 2005-10-15
forum: General Help
---

### Post by user_stu on 2005-10-15
I'm familiar with Photoshop and so would like to install Gimpshop... Some questions about installing stuff in general though (using the Gimpshop as an example):

Note: Instructions and .deb availalbe at  [http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)

1. Since the provided .deb has filename gimp_2.2.4-2_i386.deb, it would appear to be an earlier version than ships with Breezy. If this stuffs things up, can I just use Synaptic to uninstall and reinstall The Gimp if necessary? Or do I have to install the corresponding Gimp version for this Gimpshop thing to work? 

2. How can you handle security and patch updates on software that is installed "manually" (ie, not via the official Synaptic repositories)? Is it a case of manually checking, say, the Gimpshop website for alerts and/or upgrades and applying them as required? I guess that makes sense--coming from windows, you expect core OS things and Office security/updates to be handled automatically, but if you go install some non-Microsoft game, then it becomes a manual task to keep the game up to date.

3. They also provide "source". Why/when would I use this instead of the .deb package?

4. Has anyone installed this particular package?

---

### Post by garretjax on 2005-10-15
For you first question i cannot help.
The second, as far as I know, your bang on, if you install something from source or [i think] by RPM you would have to provide your own updates and patches that way.

As for WHY source installs are offered, not all distros use .deb or .rpm packages for installing, most noteably would be slackware [great distro - its close competion to ubuntu for my main desktop use]


Hope this helps

---

### Post by chaumurky on 2005-10-15
Q1 Yep, it appears in Synaptic and you can remove it cleanly. Any dependancies will be from Ubuntu repositories and are safe to keep (but won't be removed).

---

### Post by jobezone on 2005-10-15
> **user_stu]I'm familiar with Photoshop and so would like to install Gimpshop... Some questions about installing stuff in general though (using the Gimpshop as an example):

Note: Instructions and .deb availalbe at  [http://linux.suramya.com/tutorials/Install_GIMPShop/](http://linux.suramya.com/tutorials/Install_GIMPShop/)

1. Since the provided .deb has filename gimp_2.2.4-2_i386.deb, it would appear to be an earlier version than ships with Breezy. If this stuffs things up, can I just use Synaptic to uninstall and reinstall The Gimp if necessary? 
[/quote] Either this package can co-exist with breezy's gimp, or you'll first need to remove breezy's gimp. If so, and after you install gimpshop, you'll probably need to prevent it (gimp(shop)) from being upgraded to breezy's gimp, by "locking" it in Synaptic.
 > Do I have to install the corresponding Gimp version for this Gimpshop thing to work?There really isn't a need for a corresponding Gimp version. Gimp in Breezy is: Gimp 2.2.8 released by Gimp developers and packaged by ubuntu developers said:**
> 2. How can you handle security and patch updates on software that is installed "manually" (ie, not via the official Synaptic repositories)? Is it a case of manually checking, say, the Gimpshop website for alerts and/or upgrades and applying them as required? In this case, it seems so. Some application developers provide their own repository which you can use to automatically get their updates through Synaptic (Wine is such a case. There is ubuntu's Wine, but wine developers also provide their own repository with usually more recent versions)
> 3. They also provide "source". Why/when would I use this instead of the .deb package? The source is the most universal way and low-level way of installing software in Gnu/linux (and unix) systems. People use it if:

- It is the only fashion the software is provided in. Bleeding edge and development releases of applications are usually released in source even (not even binaries are released). Recently, say in the last years or so, developers have been releasing their development releases more in package format or in binaries, so to get more feedback from "novice" users.

-They want to modify some options that the application provides during compilation (of the source).

-There is no available package for their distribution, and they want to convert it (usually from .rpm to .deb, or vice-versa) using **alien**, but the resulting package doesn't work.

-Their distribution's application package is (slightly, or a lot) outdated, and they can't wait to get the new version.

> 4. Has anyone installed this particular package?
Not me, but I'll try it in the near future.

---

### Post by Arktis on 2005-10-15
>  3. They also provide "source". Why/when would I use this instead of the .deb package?

"Use the source, Luke!"

You can actually create your own debian package from the source code using checkinstall, availible from the repositories.  Here's how it normally works:

extract the sourcecode somewhere, go to where you extracted it in a terminal, run the configure script as normal, then type 'sudo checkinstall'.  (note: I like to run make before I run checkinstall, just to ensure there won't be any problems and if there are any, to fix them first.)

Checkinstall builds the source for you, and then creates a debian package and installs it.  So when you want to remove the program, just do so from synaptec.  When you want to upgrade, download the new source and run checkinstall on it again to create an updated package for yourself.

---

### Post by jobezone on 2005-10-15
> 
extract the sourcecode somewhere, go to where you extracted it in a terminal, run the configure script as normal, then type 'sudo checkinstall'.
Isn't it safer to do ```
fakeroot checkinstall
```?
. Sure, you're going to install it anyway later in the system, but at least it's one less risky operation being done.

---

