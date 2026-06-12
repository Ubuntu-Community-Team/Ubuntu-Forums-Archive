---
title: "Art Manager doesn't open"
date: 2008-05-20
forum: General Help
---

### Post by Ioky on 2008-05-20
I try to open Art Manager in the menu, it doesn't work. So try it in Terminal. It shows:

ioky@BiTuX:~$ gnome-art
/home/ioky/.themes/Moomex-Ultimatum/gtk-2.0/Icons/iconrc:11: Unable to locate image file in pixmap_path: "gtk-stop.png"
/home/ioky/.themes/Moomex-Ultimatum/gtk-2.0/gtkrc:288: Unable to locate image file in pixmap_path: "Menu/menubar-item.png"
/home/ioky/.themes/Moomex-Ultimatum/gtk-2.0/gtkrc:291: Background image options specified without filename
/home/ioky/.themes/Moomex-Ultimatum/gtk-2.0/gtkrc:937: Unable to locate image file in pixmap_path: "Menu/menuitem.png"
/home/ioky/.themes/Moomex-Ultimatum/gtk-2.0/gtkrc:940: Background image options specified without filename
/usr/bin/gnome-art: line 22
   Gtk-WARNING **:Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
/usr/lib/ruby/1.8/net/protocol.rb:133:in `sysread': Connection reset by peer (Errno::ECONNRESET)
	from /usr/lib/ruby/1.8/net/protocol.rb:133:in `rbuf_fill'
	from /usr/lib/ruby/1.8/timeout.rb:56:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/protocol.rb:132:in `rbuf_fill'
	from /usr/lib/ruby/1.8/net/protocol.rb:116:in `readuntil'
	from /usr/lib/ruby/1.8/net/protocol.rb:126:in `readline'
	from /usr/lib/ruby/1.8/net/http.rb:2020:in `read_status_line'
	from /usr/lib/ruby/1.8/net/http.rb:2009:in `read_new'
	 ... 10 levels...
	from /usr/lib/ruby/1.8/open-uri.rb:30:in `open'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:156:in `isConnected'
	from /usr/lib/ruby/1.8/gnome-art/gnome_art.rb:132:in `main'
	from /usr/bin/gnome-art:25

Doesn't know what is happening. Any one Help?

Thanks

---

### Post by N.N. on 2008-05-20
This is caused by a bug in gnome-art, cf. the following report on launchpad: [https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/228552](https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/228552). It seems the developer of the application is on holiday at the moment, so he won't be able to fix it until the 23rd.

Apparently you can solve the problem by adding/editing some lines of code in the program, but that involves recompiling it yourself. If you are interested in pursuing this solution, see the following link for more information: [http://developer.berlios.de/bugs/?func=detailbug&bug_id=13780&group_id=9184](http://developer.berlios.de/bugs/?func=detailbug&bug_id=13780&group_id=9184).

---

