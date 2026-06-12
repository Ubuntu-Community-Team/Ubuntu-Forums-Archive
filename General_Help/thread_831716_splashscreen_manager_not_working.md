---
title: "splashscreen manager not working"
date: 2008-06-17
forum: General Help
---

### Post by dexter.deepak on 2008-06-17
i was trying to install a mac-login screen to ubuntu-gutsy desktop, but the manager applet simply crashes, even if i run it as root...hereis the output in the terminal:

dpak@dpak-server:~$ gnome-splashscreen-manager
/usr/bin/gnome-splashscreen-manager: line 22
   Gtk-WARNING **:Theme file for Shere_Khan_X has no directories

/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `last_write': Unrecognized image file format (Gdk::PixbufError)
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:192:in `download_pixbuf'
        from /usr/lib/ruby/1.8/open-uri.rb:32:in `open_uri_original_open'
        from /usr/lib/ruby/1.8/open-uri.rb:32:in `open'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:191:in `download_pixbuf'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:199:in `create_thumbnail'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:271:in `get_splash_screens'
        from /usr/lib/ruby/1.8/rexml/element.rb:934:in `each'
        from /usr/lib/ruby/1.8/rexml/xpath.rb:53:in `each'
        from /usr/lib/ruby/1.8/rexml/element.rb:934:in `each'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:221:in `get_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:261:in `reload_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:458:in `initialize'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:62:in `new'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:62:in `main'
        from /usr/bin/gnome-splashscreen-manager:25

---

### Post by dexter.deepak on 2008-06-18
someone please help ](*,)

---

### Post by Phantom3D on 2009-02-23
[https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/199229](https://bugs.launchpad.net/ubuntu/+source/gnome-art/+bug/199229)

"Solution: remove the file "~/.gnome2/gnome-art/download/splashscreens/Splash-CountrySplash.png"
...and the manager starts up properly"

This might be the problem?

---

