---
title: "[SOLVED] Compiz missing titlebars"
date: 2008-07-06
forum: General Help
---

### Post by jbrackett on 2008-07-06
There have been many posts on this but none have helped me unfortunately.

compiz --replace
results in losing titlebars and losing keybindings so I can't alt-drag windows for example
(Window Decoration effect is enabled in CCSM) 

emerald --replace
nothing happens and nothing is printed to terminal

gtk-window-decorator --replace
gtk-window-decorator: error while loading shared libraries: libwnck-1.so.18: cannot open shared object file: No such file or directory
(tried creating a symlink to libwnck-1.so.21 which does exist but it didn't help solve the missing titlebars)

metacity --replace
Window manager warning: "Disabled" found in configuration database is not a valid value for keybinding "toggle_shaded"
(irritating because it means I have to restart X to get titlebars back)

I used compiz-check and everything checked out OK.

I've tried uninstalling and reinstalling compiz via apt with no change.  Let me know if I can provide any more info.


Info:
Ubuntu 8.04
2.6.24-19-generic #1 SMP Wed Jun 18 14:15:37 UTC 2008 x86_64 GNU/Linux
Nvidia 8800GTS 640MB
173.14.09 binary

---

### Post by sayakb on 2008-07-06
Did you play around with CCSM? If you somehow managed to spoil the settings, open CCSM, click preferences and click **Reset to defaults.**

---

### Post by jbrackett on 2008-07-06
Thanks for the quick response.  I have tried to reset the settings in the past and even deleted ~/.config/compiz

Just tried again to reset through ccsm and ended up having to reboot.  If I compiz --replace in terminal and then ctrl-z to stop it - it freezes up the comp.

---

### Post by sayakb on 2008-07-06
Try installing the latest version of Compiz
[http://ubuntuforums.org/showpost.php?p=5332505&postcount=5](http://ubuntuforums.org/showpost.php?p=5332505&postcount=5)

---

### Post by jbrackett on 2008-07-06
It says I have version 0.52 now, but still not working.

Probably not related, but all of a sudden when rebooting I get the splash screen - the progress bar moves - disappears - and just sits there until I ctrl-atl-backspace after which it continues loading.

Edit: shouldn't compiz --version give 0.7x?:confused:

---

### Post by sayakb on 2008-07-07
```
glade@Mean-Machine:~$ dpkg --list compiz
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  compiz         1:0.7.6-0ubunt OpenGL window and compositing manager
glade@Mean-Machine:~$ 

```
It should show 0.7.6 
Did you upgrade using the link I posted?

---

### Post by jbrackett on 2008-07-07
Yea I did

```

dpkg --list compiz
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  compiz         1:0.7.6-0ubunt OpenGL window and compositing manager

```

```

compiz --version
compiz 0.5.2

```

```

sudo apt-get install compiz
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Edit: Also I do now have the "cube reflection and deformation" option in ccsm

Edit2:
```

ccsm --version
CCSM 0.7.6

```

---

### Post by jbrackett on 2008-07-08
Any other ideas?

(I'm at work so excuse me if I don't respond right away)

---

### Post by sayakb on 2008-07-08
> **jbrackett said:**
> Any other ideas?

(I'm at work so excuse me if I don't respond right away)
```
glade@Mean-Machine:~$ compiz --version
<snip>
compiz 0.7.6
glade@Mean-Machine:~$ 

```

Seems like you don't have the latest compiz. Remove and add the repository again and re-install compiz. If necessary, remove it completely and install again.

---

### Post by jbrackett on 2008-07-08
This is getting really irritating now :(

```
WARNING: The following packages cannot be authenticated!
  compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main
  libdecoration0 compiz-plugins libcompizconfig0 compiz-gnome compiz
Install these packages without verification [y/N]? y
Selecting previously deselected package libx11-xcb1.
(Reading database ... 174194 files and directories currently installed.)
Unpacking libx11-xcb1 (from .../libx11-xcb1_2%3a1.1.3-1ubuntu2_amd64.deb) ...
Selecting previously deselected package compiz-core.
Unpacking compiz-core (from .../compiz-core_1%3a0.7.6-0ubuntu2~ppa1_amd64.deb) ...
Selecting previously deselected package compiz-fusion-plugins-extra.
Unpacking compiz-fusion-plugins-extra (from .../compiz-fusion-plugins-extra_0.7.6-0ubuntu1~ppa1_amd64.deb) ...
Selecting previously deselected package compiz-fusion-plugins-main.
Unpacking compiz-fusion-plugins-main (from .../compiz-fusion-plugins-main_0.7.6-0ubuntu1~ppa1_amd64.deb) ...
Selecting previously deselected package libdecoration0.
Unpacking libdecoration0 (from .../libdecoration0_1%3a0.7.6-0ubuntu2~ppa1_amd64.deb) ...
Selecting previously deselected package compiz-plugins.
Unpacking compiz-plugins (from .../compiz-plugins_1%3a0.7.6-0ubuntu2~ppa1_amd64.deb) ...
Selecting previously deselected package libcompizconfig0.
Unpacking libcompizconfig0 (from .../libcompizconfig0_0.7.6-0ubuntu1~ppa1_amd64.deb) ...
Selecting previously deselected package compizconfig-backend-gconf.
Unpacking compizconfig-backend-gconf (from .../compizconfig-backend-gconf_0.7.4-0ubuntu1_amd64.deb) ...
Selecting previously deselected package compiz-gnome.
Unpacking compiz-gnome (from .../compiz-gnome_1%3a0.7.6-0ubuntu2~ppa1_amd64.deb) ...
Selecting previously deselected package compiz.
Unpacking compiz (from .../compiz_1%3a0.7.6-0ubuntu2~ppa1_all.deb) ...
Setting up libx11-xcb1 (2:1.1.3-1ubuntu2) ...

Setting up compiz-core (1:0.7.6-0ubuntu2~ppa1) ...
Setting up compiz-fusion-plugins-extra (0.7.6-0ubuntu1~ppa1) ...

Setting up compiz-fusion-plugins-main (0.7.6-0ubuntu1~ppa1) ...

Setting up libdecoration0 (1:0.7.6-0ubuntu2~ppa1) ...

Setting up compiz-plugins (1:0.7.6-0ubuntu2~ppa1) ...
Setting up libcompizconfig0 (0.7.6-0ubuntu1~ppa1) ...

Setting up compizconfig-backend-gconf (0.7.4-0ubuntu1) ...
Setting up compiz-gnome (1:0.7.6-0ubuntu2~ppa1) ...

Setting up compiz (1:0.7.6-0ubuntu2~ppa1) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
joshb@joshb-desktop:~$ compiz --version
compiz 0.5.2

```

This is after completely (as far as I could tell) removing compiz and associated libraries.

---

### Post by jbrackett on 2008-07-09
Could the 64bit version perhaps just have a bug and it displays the wrong version when calling compiz --version?

When I go and look at the added files they are all relatively new - created in late April or early June, so it looks like the updated files are there.

Very strange.

---

### Post by jbrackett on 2008-07-11
Ended up doing a clean install, which fixed all my issues.

---

