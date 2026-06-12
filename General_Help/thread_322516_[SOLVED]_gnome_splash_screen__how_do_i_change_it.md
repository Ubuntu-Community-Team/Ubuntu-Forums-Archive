---
title: "[SOLVED] gnome splash screen : how do i change it?"
date: 2006-12-20
forum: General Help
---

### Post by Beowulf.1000 on 2006-12-20
I want to change my gnome splash screen-- from the default Ubuntu brown tone rectangular screen that shows the hardware being set up, etc. (this is *after*  the GDM login manager screen). I have read other posts but still do not have a solution. I installed gnome-splashscreen-manager using
 [FONT="Courier New"] sudo apt-get install gnome-art[/FONT]
then I can run 
  [FONT="Courier New"]sudo gnome-splashscreen-manager[/FONT]
and browse and "install" and "activate" a gnome splash image but then when I reboot I get the same old same old brown rectangular Ubuntu splash showing initiation of printer, etc. just before my gnome Desktop displays.  What am I doing wrong? If I try to run  [FONT="Courier New"]gnome-splashscreen-manager[/FONT] as user without sudo or from my user System menu it crashes. Here is the output of trying to run  [FONT="Courier New"]gnome-splashscreen-manager[/FONT] without sudo:

[FONT="System"]beowulf@Chaos:~$ gnome-splashscreen-manager 
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:207:in `initialize': Permission denied - /home/beowulf/.gnome2/splash-screens.xml (Errno::EACCES)
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/splash_screens.rb:207:in `get_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:261:in `reload_splash_screens'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/ui/main_window.rb:458:in `initialize'
        from /usr/lib/ruby/1.8/gnome-splashscreen-manager/gnome_splashscreen_manager.rb:62:in `main'
        from /usr/bin/gnome-splashscreen-manager:25
beowulf@Chaos:~$ [/FONT]

---

### Post by tkjacobsen on 2006-12-20
open "gconf-editor"

go to apps -> gnome-session ->options

and you'll find it under splash_image

EDIT:
the folder containing the splash images is:
/usr/share/pixmaps/splash

this will be a handy place to put your new spalsh

---

### Post by rotten777 on 2006-12-20
what I did,

open a terminal, mkdir .splash, extract the splash png's to that directory, and specify it in the section tkjacobsen mentioned.

here's the one i'm using:
[http://www.gnome-look.org/content/show.php?content=28458](http://www.gnome-look.org/content/show.php?content=28458)

---

### Post by Beowulf.1000 on 2006-12-20
> **tkjacobsen said:**
> open "gconf-editor"
go to apps -> gnome-session ->options
and you'll find it under splash_image
EDIT:
the folder containing the splash images is:
/usr/share/pixmaps/splash
this will be a handy place to put your new spalsh

Ughhhh... well I did that, rebooted, and nothing changed, still the same old brown Ubuntu gnome splash screen. I set 
   splash_image    /apps/gnome-session/options/splash_image

Here is a 'ls' showing the file I put there after running 'sudo gconf-editor'

[INDENT]beowulf@Chaos:~$ ls -l /usr/share/pixmaps/splash/splash.png
-rw-r--r-- 1 root root 137671 2006-12-20 15:57 /usr/share/pixmaps/splash/splash.png
beowulf@Chaos:~$ [/INDENT]

---

### Post by Beowulf.1000 on 2006-12-20
> **rotten777 said:**
> what I did,
open a terminal, mkdir .splash, extract the splash png's to that directory, and specify it in the section tkjacobsen mentioned....


Well I had actually tried something like that before my original post, going by what I had read off the net (using gnome-splashscreen-manager) and made a director ~/.gnome and put splash.png there.  Frustrating, I do not know why that fricken Ubuntu brown splash keeps coming up.

---

### Post by tkjacobsen on 2006-12-20
maybe gnome-splashscreen-manager is messing things up.. The quick and dirty way would be to replace the file itself "ubuntu-splash.png" (the default one) with the one you like (back it up first).

---

### Post by Beowulf.1000 on 2006-12-20
> **tkjacobsen said:**
> maybe gnome-splashscreen-manager is messing things up.. The quick and dirty way would be to replace the file itself "ubuntu-splash.png" (the default one) with the one you like (back it up first).


Success !!! I needed to do
  $ gconf-editor
and not
  $ sudo gconf-editor

I am guessing the use of sudo was setting the splash screen for root, not me as ordinary user beowulf, hence I was not seeing the splash screen during reboot. It works now, looks sweet!!!! Thank you guys!!!! :mrgreen:

---

### Post by Phire on 2006-12-21
I think i may have a simpler procedure though it should be undertaken with caution

In the /usr/share/pixmap/splash folder, there will contain some splash images and one link named 'ubuntu-splash.png'. To change your splash screen, just change the image the link points to. 

Right, i think this would be better understood with an example. First we need to open the splash folder as root. In edgy, the following command would be entered into the terminal.

```
sudo nautilus /usr/share/pixmaps/splash/
```

Say, i want to change the splash image to 'ubuntu-smooth.png' from 'ubuntu-slick.png'. All you need to do is rename the 'ubuntu-splash.png' link to something like 'ubuntu-splash1.png', right click on the 'ubuntu-smooth.png' file and choose 'make link'. Rename the link to 'ubuntu-splash.png' and that should do it.

This is my first ever erm ...'tutorial' for lack of a better term, and i'd say its too wordy. There are probably better ways of just changing the link to point to a different file, but i do not know them, hence, my more unrefined and 'unelegant' approach, but hey whatever works, right? Hope this helps those who are, like me,  wary of messing with the 'gconf-editor'

Phire

---

### Post by hollerith on 2007-01-15
None of this gconf-editor stuff works.  It is broken by ubuntu  - the only way is to change the symlink ubuntu-splash.png to point to some other file as stated above.

---

### Post by SSupport on 2007-01-16
Just installed Edgy Eft last week, and followed Phire's advice on how to change to splash screen I like.  Very easy instructions to follow- worked wonderfully! 
Thanks, Phire!!

---

