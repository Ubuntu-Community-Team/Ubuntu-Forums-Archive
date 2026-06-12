---
title: "[SOLVED] applications menu will not open"
date: 2008-06-16
forum: General Help
---

### Post by terry f on 2008-06-16
Hi

I am having some problems with my menus.  When I click on the Applications menu noting opens.  Any one know how to get it to work?

---

### Post by nikgare on 2008-06-16
Which applications does it occur on?

---

### Post by terry f on 2008-06-16
No I mean like the bar on the top does not open.  I click on "Applications" at the top and nothing happens.  The menu will not drop down.  "Places" and "System" still open but not "Applications".

---

### Post by mc4man on 2008-06-16
That happened to me in gutsy but i can't remember what i did to restore it. (maybe either right click on applications -> edit menus -> revert or preferences -> main menu -> revert)
what you could try is right click on empty place in top panel -> add to panel -> and choose menu bar. See if that one works, if so remove the orig. and move new one over (r. click -> move)

---

### Post by terry f on 2008-06-16
no that did not fix it.

---

### Post by terry f on 2008-06-17
any one?

---

### Post by nikgare on 2008-06-17
Does this happen with all users, or just your account?

---

### Post by terry f on 2008-06-17
I just checked, it is only under my user name that it does not work.

---

### Post by terry f on 2008-06-18
any one?

---

### Post by beckols on 2008-06-18
Under system > preferences > appearance on the Visual Effects tab, which radio button is selected?

---

### Post by johnc3 on 2008-06-18
try this, it worked for me
[http://ubuntuforums.org/showthread.php?t=827376&highlight=gnome+application+menu&page=3]("http://ubuntuforums.org/showthread.php?t=827376&highlight=gnome+application+menu&page=3")  or read the full post , only 3 pages

---

### Post by nikgare on 2008-06-19
Have you tried removing the menus from the panel, restarting X and then adding the menus again?

---

### Post by mc4man on 2008-06-19
Finally remembered - the applications.menu in .config/menus is not really needed and is used when you add (include) or remove (exclude) a menu item from applications. If you happen to edit in that file you'll lose your applications drop down. (or from other ? actions). Simply deleting applications.menu will restore your applications drop down. If and when you add or remove a menu item the applications.menu is recreated.

---

### Post by VMC on 2008-06-19
> **mc4man said:**
> Finally remembered - the applications.menu in .config/menus is not really needed and is used when you add (include) or remove (exclude) a menu item from applications. If you happen to edit in that file you'll lose your applications drop down. (or from other ? actions). Simply deleting applications.menu will restore your applications drop down. If and when you add or remove a menu item the applications.menu is recreated.

I have "applications.menu" file and my Applications works. I will post it so the topic poster can compare it to his:

```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Games</Name>
		<Exclude>
			<Filename>alacarte-made.desktop</Filename>
		</Exclude>
		<AppDir>/home/vmc/.local/share/applications</AppDir>
	</Menu>
</Menu>
```

---

### Post by terry f on 2008-06-19
Thanks to every one for there help.  I tried what johnc3 posted and it worked.

---

### Post by BobSongs on 2008-07-07
> **mc4man said:**
> Finally remembered - the applications.menu in .config/menus is not really needed and is used when you add (include) or remove (exclude) a menu item from applications. If you happen to edit in that file you'll lose your applications drop down. (or from other ? actions). Simply deleting applications.menu will restore your applications drop down. If and when you add or remove a menu item the applications.menu is recreated.

Bang on, dude!

I had this entry under Applications > Games called London Law. When I tried running it I got th is message: **Cannot Launch Menu Item**: Failed to execute child process "/usr/games/london-client (No such file or directory). So I figured: Meh. Might as well remove it from the menus if it doesn't work.

As soon as I removed it I got the same error: clicking **Applications** gave me no dropdown menu.

---

