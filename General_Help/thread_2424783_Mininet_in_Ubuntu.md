---
title: "Mininet in Ubuntu"
date: 2019-08-14
forum: General Help
---

### Post by luismime12 on 2019-08-14
Hello!

I'm really newbie with Ubuntu and Linux enviroment. I'm trying to install Mininet (software that allows you to create virtual networks).

If I install the software on an Ubuntu virtual machine it works perfectly. The problem comes when i try to install the same software on a mobile phone (also with Ubuntu).

I installed Ubuntu on the mobile with the help of Userland (works as kernel of Ubuntu) with the command: **$sudo apt-get install gnome-shell **and in other test with **$sudo apt-get install lxde lxde-core. **I've tried also Debian.

[COLOR=#24292E][FONT=-apple-system]The current enviroment is:
                 Nexus 5[/FONT][/COLOR]

[LIST]
[*]ARMv7 Processor rev 0 (v7l)
$lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 18.04.3 LTS
Release: 18.04
Codename: bionic
[/LIST]



[LIST]
[*]Samsung s8
[*]Aarch 64 GNU/Linux
$lsb_release -a
"Same as above"
[/LIST]
[COLOR=#24292E][FONT=-apple-system]On both devices the problme is that mininet never starts.[/FONT][/COLOR]
[COLOR=#24292E][FONT=-apple-system]When run the command: $sudo mn --test pingall
*** Error setting resource limits. Mininet's performance may be affected.
*** Creating network
*** Adding controller
*** Adding hosts:
... (here is where it get stuck).

With the same version of Ubuntu on the laptop works perfectly (and folling the same steps for the installation). Is there something I'm missig here?

Thank you in advance,

Kins Regards.[/FONT][/COLOR]

---

