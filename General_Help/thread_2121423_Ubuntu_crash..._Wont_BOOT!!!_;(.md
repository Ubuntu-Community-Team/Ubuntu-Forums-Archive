---
title: "Ubuntu crash... Wont BOOT!!! ;("
date: 2013-03-01
forum: General Help
---

### Post by ganten7 on 2013-03-01
I have a Dell Inspiron dual-booting ubuntu 12.10 and Windows 7. So yesterday I was derping around on ubuntu and decided to shut it down. Upon turning it back on, I was greeted with the normal dual-boot menu. I scrolled down until ubuntu was selected then I pressed enter to boot it, but the only thing that came up was a command line that says "Grub." Please note that I am an absolute noob so I dont know anything about this. PLEASE SOMEONE HELP MEEEEE. ;/

---

### Post by tgalati4 on 2013-03-01
I had to look up *derping*.   [http://www.urbandictionary.com/define.php?term=derping](http://www.urbandictionary.com/define.php?term=derping)

Apparently, it's not related to your boot problem.  There are 2 entries for Ubuntu:  Normal boot, and rescue boot.  If you hit escape before hitting return, you will get a GRUB command line, that allows you to give temporary boot options--for advanced users.  Typically you would hit escape or return to get back to the GRUB menu, then hit return on the operating system that you want to boot.

Try to boot into the rescue shell--you will get a menu with some options:  Select disk check.  Then resume normal boot.  More burping, less derping.

---

### Post by ganten7 on 2013-03-04
Urgh I dont know what you mean. All I get when booting my computer is two options: Windows, and ubuntu, which I navigate to via the up and down arrow buttons, and select using the enter key. When I select windows, it boots normally, but when I select ubuntu, ONLY the command line pops up. There isnt anything I can do at this point but enter commands into grub, or press Ctrl+Alt+Delete and bring me back to the main menu where I can select them.

---

