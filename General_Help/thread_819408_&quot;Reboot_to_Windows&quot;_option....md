---
title: "&quot;Reboot to Windows&quot; option..."
date: 2008-06-05
forum: General Help
---

### Post by Netich on 2008-06-05
Hi. I dual boot Ubuntu and XP.
I think it would be great to have a option in the reboot button, to select which line in the grub will be loaded. So by default it uses the defaul line in menu.lst. But you can, for example, reboot to XP. Then the default line is changed, and you dont have to wait to the grub to select Windows.

Is there something like this already done? Even if its a script in an applet or something. I havent found anything, and seems a useful option to me. What do you think?

---

### Post by Zorael on 2008-06-05
There's a terminal tool for just that, but it needs to run with superuser permissions unless you change the ownership of /boot/grub/menu.lst (exceedingly dangerous).

```
$ grub-set-default --help
**Usage: grub-set-default [OPTION] entry**
Set the default boot entry for GRUB.

  -h, --help              print this message and exit
  -v, --version           print the version information and exit
  --root-directory=DIR    Use the directory DIR instead of the root directory

ENTRY is a number or the special keyword `default\'.

Report bugs to <bug-grub@gnu.org>.
```
```
$ sudo grub-set-default *<num>*
```
The first grub entry has the number 0, I think. So second is 1, third 2, etc.

---

### Post by Netich on 2008-06-05
Ops, i should have search better:

[http://www.cs.unm.edu/~dmohr/grub.php]("http://www.cs.unm.edu/~dmohr/grub.php")

Its written in python and has a windows app too!!
Im going to try it and post the results

---

