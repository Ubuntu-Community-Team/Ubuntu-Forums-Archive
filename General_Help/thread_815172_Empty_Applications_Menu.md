---
title: "Empty Applications Menu"
date: 2008-06-01
forum: General Help
---

### Post by totemg on 2008-06-01
For some reason, my Applications menu is empty. When I click on it, the Applications button highlights, but that is it. I try right clicking and selecting Edit Menus, but nothing happens. I read that perhaps this is a problem with home/user/.config/applications.menu
The file is empty though. Can someone tell me how to fix this problem, or maybe give me their applications.menu file to see if I can replace mine?

---

### Post by wolfen69 on 2008-06-01
```
sudo apt-get install ubuntu-desktop
```

---

### Post by hal8000 on 2008-06-01
The file is ~/.config/menus/applications.menu

This may not be the way to solve your problem though.
Copy and paste into  anew file between the angle < > brackets.

[email]anc@orac:~/.conf[/email]ig/menus$ cat applications.menu 
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>


What I would do is create a new user on your system, this should recreate a new set of menus and you may be able to copy your settings across that way.
You may get other solutions as well.

---

### Post by totemg on 2008-06-01
No, the Applications menu still doesn't open.
Edit: hal8000, both of our posts appeared at about the same time. I made another user and that menu file worked, thanks. Problem solved.

---

