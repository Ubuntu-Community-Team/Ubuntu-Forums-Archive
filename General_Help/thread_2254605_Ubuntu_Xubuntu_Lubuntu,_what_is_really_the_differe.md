---
title: "Ubuntu Xubuntu Lubuntu, what is really the difference ?"
date: 2014-11-28
forum: General Help
---

### Post by blnl on 2014-11-28
I'm still puzzled by a variety of Ubuntu branches. Need some explanation please...

Take for example Xubuntu and Lubuntu, when I read about them the main topic being mentioned is different desktop environment (Xfce, LXDE). Yet, I'm not able to figure out if that is the only difference or is there more to it.
[LIST]
[*]Is Xubuntu/Lubuntu the very same Ubuntu distro, only instead of Unitiy it comes with Xfce/LXDE? Is that all?
[*]Or is it completely independent distro that goes its own direction and over time it will be related to Ubuntu just as much as Ubunut is today related to Debian (or OpenSUSE to Slackware)?
[/LIST]

If it's only the desktop environment then I do not understand the need for branching. When I install Fedora it offers me the choice of the desktop environment (during installation setup): GNOME Desktop, KDE Plasma Workspaces, Xfce Desktop, LXDE Desktop, Cinnamon Desktop, MATE Desktop, Sugar Desktop Environment. So it is the very same Fedora only with different desktop environment.
Why Ubuntu does not have a choice of desktop environment? Is that the way how Ubuntu offers the choice of desktop environment, just download another distro... What is really the truth about Ubuntu distros?

---

### Post by sudodus on 2014-11-28
Except for the obvious differences, that you describe,

- different packages are bundled in the distributing ISO files
- settings, shortcuts and tweaks are done differently

- so Lubuntu is different from Ubuntu mini.iso plus LXDE and Xubuntu is different from Ubuntu mini.iso plus XFCE, they even look different.

- But the engine under the hood is the same as in standard Ubuntu and Kubuntu and Ubuntu Gnome ... , and the same repositories are used, so that you can install the same programs. You can even install lubuntu-desktop, xubuntu-desktop etc into the same installed standard Ubuntu system. It works but will be bloated with several tools for the same task, for example pcmanfm and thunar will be added alongside nautilus (or 'files' in the newest versions).

- Standard Ubuntu is provided by Canonical while the other flavours are provided by community teams, completely voluntary so without any paid staff, but some infrastructure provided by Canonical can be used. By the way, the Ubuntu Forums are also managed by volunteers while the internet infrastructure is provided by Canonical.

Correct me if I'm wrong! Someone else might explain it in another way, and it might help to get replies from different perspectives.

---

### Post by oldos2er on 2014-11-28
No, there's no branching involved; the only difference is the desktop environment.

> Why Ubuntu does not have a choice of desktop environment? Is that the way how Ubuntu offers the choice of desktop environment

Yes. You can also install a different DE after you have the OS installed.

---

### Post by grahammechanical on 2014-11-28
Ubuntu is Free and Open Source Software (FOSS). Its developers use software from other FOSS projects in accordance with the terms of the software license. So, the kernel is Linux. The display server is Xserver. The desktop environment is Gnome 3 Desktop Environment (DE). To name just a few components of a distribution.

Because Ubuntu is also a FOSS project others are allowed to take Ubuntu and modify the software in accordance with the licence. And so, we have different distributions built on Ubuntu. Some of which are accepted as officially recognised flavours of Ubuntu.

To give an example, one of the developers of the Mate desktop environment and user interface has been working on putting Mate on to Ubuntu and he is seeking official acceptance as a Ubuntu Flavour. If the application succeeds there will be a Ubuntu Mate flavour. He, and those who have joined him in this project have produced a version based on the Ubuntu 14.10 code and recently they released a version built on the Ubuntu 14.04 code. All the other flavours started out the same way, with a few developers wanting to do something different and being free to do it.

We have to understand that the decision was taken a long time ago to build Ubuntu using the Gnome DE. Ubuntu developers, whether volunteers or paid employees of Canonical, have the purpose of developing Ubuntu. I actually think it would be wrong for Ubuntu developers to claim for themselves the responsibility of putting various desktop environments on top of Ubuntu. That would deny others the freedom to do things differently. So, I am glad that the Ubuntu family is developed in way it presently is developed. Freedom = Choice.

Regards.

---

### Post by buzzingrobot on 2014-11-28
The different interfaces offered in Fedora's installer are also available as individual 'Fedora Spins' that can be installed.  E.g., if you download and install the Fedora XFCE spin, you get exactly the same system you'd get from selecting the XFCE option in Fedora's installer (although that option is not shown in the installer for the single-desktop live images AKA spins.

The Fedora community is organized differently that the Ubuntu community, but the Fedora Spins are analagous to the Ubuntu flavors.

BTW, if you do an Ubuntu mini/netinstall, you will be given the same option to install any of the other desktops, just as in Fedora's netinstall (I believe that's the only image that will offer those in Fedora 21.)

---

### Post by blnl on 2014-12-01
Thank you all for the explanations, I believe that now I understand better how Ubuntu family is related.

---

### Post by blnl on 2014-12-01
> **sudodus said:**
> Except for the obvious differences, that you describe,

- different packages are bundled in the distributing ISO files
- settings, shortcuts and tweaks are done differently


I would like to understand better the diff between Ubuntu and Lubuntu settings and tweaks (especially the ones that are not related to desktop environments).
Is it possible to get somewhere the settings and tweaks for Lubuntu? It must be documented somewhere, I suppose this information is not confidential.

---

### Post by vasa1 on 2014-12-01
> **blnl said:**
> ...It must be document somewhere, **I suppose this information is not confidential**.
What do you mean by that? AFAIK, it isn't confidential. It is documented somewhere. Use the search feature at help.ubuntu.com/community for whatever needs you have.

---

### Post by buzzingrobot on 2014-12-01
> **blnl said:**
> 
Is it possible to get somewhere the settings and tweaks for Lubuntu? It must be document somewhere...

At a high level, the Lubuntu site will summarize the differences, which are almost entirely in the visual layer the users sees:  destkop environment and tools, window manager, file manager, different themeing, and a different selection of default applications. 

Low level differences aren't going to be spelled out someplace in user-friendly style.  The source code to everything can be acquired, examined, and compared at packages.ubuntu.com. A middle approach might be to simply install both and have a look.

[EDIT:  The differences that exist are driven by the requirements of the different interfaces. It's the wish for using a different interface on an Ubuntu base that motivates the creation and maintenance of these spins. If, for example, you want to build a distribution that uses LXDE and Openbox on an Ubuntu base instead of Unity on the same Ubuntu base, then the process of pulling Unity out will also remove some if its dependencies, and the process of adding LXDE and Openbox will entail adding their dependencies. ]

---

### Post by vasa1 on 2014-12-01
Well, OP seems to have an issue other than source code:
"What **is really the truth** about Ubuntu distros?" from the first post.
"...It must be document somewhere, I suppose this information is not confidential."
If I come across a support question about Lubuntu, appropriately worded and limited in scope, I'll try to answer it.

---

