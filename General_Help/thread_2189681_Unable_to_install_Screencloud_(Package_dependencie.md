---
title: "Unable to install Screencloud (Package dependencies cannot be resolved)"
date: 2013-11-23
forum: General Help
---

### Post by lemort on 2013-11-23
I searched the net but was unable to find a solution, so I hope someone here can help me out of this!

Trying to install [Screencloud]("http://screencloud.net/") on Ubuntu 12.04 I get the following error:[INDENT]
[COLOR=#ff0000]**Package dependencies cannot be resolved**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]The following packages have unmet dependencies:[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]
[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]screencloud: Depends: libc6 (>= 2.4) but 2.15-0ubuntu10.5 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libqca2 (>= 2.0.2) but 2.0.3-2 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libqt4-network (>= 4:4.6.1) but 4:4.8.1-0ubuntu4.4 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libqt4-script (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.4 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libqt4-xml (>= 4:4.5.3) but 4:4.8.1-0ubuntu4.4 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.4 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libqtgui4 (>= 4:4.6.1) but 4:4.8.1-0ubuntu4.4 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libquazip0 but it is not going to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libsdl1.2debian (>= 1.2.11) but 1.2.14-6.4ubuntu3 is to be installed[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]             Depends: libstdc++6 (>= 4.1.1) but 4.6.3-1ubuntu5 is to be installed[/COLOR]


[/INDENT]
Tried installing via Software Center, via Synaptic and via terminal.

Terminal greets me with the following error:
[INDENT][COLOR=#ff0000]Some packages could not be installed. This may mean that you have[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]requested an impossible situation or if you are using the unstable[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]distribution that some required packages have not yet been created[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]or been moved out of Incoming.[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]The following information may help to resolve the situation:[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]
[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]The following packages have unmet dependencies:[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]screencloud : Depends: libquazip0 but it is not installable[/COLOR][/INDENT]
[INDENT][COLOR=#ff0000]E: Unable to correct problems, you have held broken packages.
[/COLOR]

[/INDENT]
Synaptic shows no broken packages and this libquazip0 is nowhere to be found...

---

### Post by ian-weisser on 2013-11-23
Software Center, synaptic, and apt-get are all different faces of the  same package manager. If one complains about breakage, then usually all  of them will.

> **lemort said:**
> Trying to install [Screencloud]("http://screencloud.net/") on Ubuntu 12.04 I get the following error:Are you trying to install from the Ubuntu Repositories, from a PPA, or some other way?


Take a look at some of those dependency versions:
> **lemort said:**
> 
Package dependencies cannot be resolved
screencloud: Depends: libc6 (>= [COLOR=#ff0000]2.4[/COLOR]) but [COLOR=#ff0000]2.15-0ubuntu10.5[/COLOR] is to be installed[INDENT]             Depends: libgcc1 (>= [COLOR=#ff0000]1:4.1.1[/COLOR]) but [COLOR=#ff0000]1:4.6.3-1ubuntu5[/COLOR] is to be installed[/INDENT]
[INDENT]
[/INDENT]
libc6 2.4 is *ancient*. Your version is 2.15
Similarly, libgcc1 4.1 is long obsolete. Your version is 4.6.3.

This kind of package manager error usually means you have added some non-Ubuntu repository or PPA. A very old one.

First, open your Software Sources control panel. You can open it from Software Center, from Synaptic, or by using the command **software-properties-gtk**

Disable (uncheck) ALL non-official Ubuntu repositories. Disable ALL PPAs.
Close the Software Sources control panel.

Try the command **sudo apt-get update && sudo apt-get upgrade**
In many cases, that's all you need to do to get you package manager working again.

However, if yours still isn't working, then please post your /etc/apt/sources.list,
and please post the list of your /etc/apt/sources.list.d directory.

---

