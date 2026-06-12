---
title: "Disabale 'Turn Off' option for users"
date: 2020-06-09
forum: General Help
---

### Post by vjp1978 on 2020-06-09
I'd like to deny to turn off or restart the workstation for regular users. I read many solutions but non of them the right one for me. It is an Ubuntu desktop 20.04, and the users are AD users they will use this via xrdp.
  Thank's for your help

---

### Post by howefield on 2020-06-09
Support thread, so moved to the "*General Help*" forum.

---

### Post by SeijiSensei on 2020-06-09
You could try disabling /sbin/shutdown by renaming it (as root with sudo) to something like /sbin/shutdown.disabled.  You'd also have to deal with the programs /usr/sbin/halt, /usr/sbin/poweroff, and /usr/sbin/reboot.  I don't know which of these programs are run when you hit the shutdown or reboot button in an Ubuntu distribution, but these seem the most likely candidates.

---

### Post by vjp1978 on 2020-06-10
[]("https://askubuntu.com/posts/1248481/timeline")                                I'd like to deny to turn off or restart the workstation for regular users. I read many solutions but non of them the right one for me. It is an Ubuntu desktop 20.04, and the users are AD users they will use this via xrdp.
  Thank's for your help

---

### Post by CelticWarrior on 2020-06-10
Please post the solutions that aren't right for you and why in order to avoid getting replies with those solutions.

---

### Post by wildmanne39 on 2020-06-10
Threads merged. Please do not post duplicates, it dilutes community effort.

---

### Post by vjp1978 on 2020-06-10
@SeijiSensei sadly it is not working :( I renamed shutdown, power off, halt and reboot but it didn't matter. Sorry about the post duplication.

---

### Post by GhX6GZMB on 2020-06-10
In Lubuntu/LXQt this is pretty easy, as you can remove those items (shutdown, reboot, logout etc.) from the application menu.
I have no experience with Ubuntu/Gnome, sorry.

---

### Post by SeijiSensei on 2020-06-10
I couldn't figure out how to edit the menus, so I suggested a more brute force approach.  Apparently the GUI runs a program not among those I listed earlier (shutdown, poweroff, halt, reboot).  Wonder what it could be, unless the GUI button sends the signal directly to the kernel rather than invoking one of these programs.

---

### Post by GhX6GZMB on 2020-06-10
> **SeijiSensei said:**
> I couldn't figure out how to edit the menus, so I suggested a more brute force approach.  Apparently the GUI runs a program not among those I listed earlier (shutdown, poweroff, halt, reboot).  Wonder what it could be, unless the GUI button sends the signal directly to the kernel rather than invoking one of these programs.

My suggestion is just about hiding the menu items in the Application Menu. It's in no way bullet-proof, I'm sure a smart user could get around this, eg, using Ctrl+Alt+T. And I've only done this in Lubuntu/LXQt.

In LXQt, there's no menu file as such, every menu _item_ is a file. The Application Menu is built from collecting these files during login.

The menu item files can be found under:
 ```
/usr/share/applications 
```
(for the admin user)

or:
```
~/.local/share/applications
```
(for a normal user)

For each menu item you want to suppress, use a text editor and add the following line anywhere in the file:
```
NoDisplay=true
```

Repeat until the Applications Menu contains only the items you want.

You'll need to this with sudo permissions, of course. And you need to logout/login before the changes take effect.

Whether this will work under Gnome? I don't know.



_**EDIT:**_ according to this, it should work in Gnome as well: [https://developer.gnome.org/integration-guide/stable/desktop-files.html.en](https://developer.gnome.org/integration-guide/stable/desktop-files.html.en)

---

### Post by vjp1978 on 2020-06-16
I read the answers and I found a solution it is not so elegant.
In the /usr/share/polkit-1/actions/org.freedesktop.login1.policy I can find 3-3 reboot and power-off options. In the rebbot section modificated the permissions, and now the User cannot rebbot the machine while somebody are loged in.
<allow_any>auth_admin</allow_any>
<allow_inactive>auth_admin</allow_inactive>
<allow_active>auth_admin_keep</allow_active>
In the power-off section:
<allow_inactive>yes</allow_inactive> I turned the button to inactive.

---

