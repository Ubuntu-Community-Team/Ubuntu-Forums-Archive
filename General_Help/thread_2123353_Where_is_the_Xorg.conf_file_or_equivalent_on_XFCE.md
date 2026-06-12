---
title: "Where is the Xorg.conf file or equivalent on XFCE?"
date: 2013-03-07
forum: General Help
---

### Post by ubunet on 2013-03-07
I tried to search with find command but he doesn't exist.

```
sudo find / -name "xorg*"
/etc/apt/sources.list.d/xorg-edgers-ppa-quantal.list.save
/etc/apt/sources.list.d/xorg-edgers-ppa-quantal.list
/usr/share/lintian/overrides/xorg
/usr/share/man/man5/xorg.conf.d.5.gz
/usr/share/man/man5/xorg.conf.5.gz
/usr/share/doc/xorg-docs-core
/usr/share/doc/xorg
/usr/share/X11/xorg.conf.d
/usr/share/X11/xkb/rules/xorg.lst
/usr/share/X11/xkb/rules/xorg
/usr/share/X11/xkb/rules/xorg.xml
/usr/share/bug/xorg
/usr/include/xorg
/usr/lib/fglrx/xorg
/usr/lib/pxpress/xorg
/usr/lib/pkgconfig/xorg-wacom.pc
/usr/lib/xorg
/usr/lib/python3/dist-packages/xkit/xorgparser.py
/usr/lib/python3/dist-packages/xkit/__pycache__/xorgparser.cpython-32.pyc
/usr/lib/python3/dist-packages/DistUpgrade/xorg_fix_proprietary.py
/usr/lib/python3/dist-packages/DistUpgrade/__pycache__/xorg_fix_proprietary.cpython-32.pyc
/usr/lib/i386-linux-gnu/xorg
/var/lib/dpkg/info/xorg.md5sums
/var/lib/dpkg/info/xorg.list
/var/lib/dpkg/info/xorg-docs-core.md5sums
/var/lib/dpkg/info/xorg.preinst
/var/lib/dpkg/info/xorg-docs-core.list

```

---

### Post by Cheesemill on 2013-03-07
Ubuntu hasn't shipped with an xorg.conf file for several years now, all of your hardware should be detected automatically so there usually isn't any need for one.

This doesn't mean that you can't use one though, you can create it and its settings will take precedence over any auto-detected settings.

If you want to create a basic xorg.conf you can do the following...

Hit CTRL+ALT+F1 to switch to a tty and log on.
Run the command
```
 sudo service lightdm stop
```
to stop the X server, then run
```
 sudo Xorg -configure
```
to create a new xorg.conf file.
Copy it to the correct location with
```
 sudo cp /root/xorg.conf.new /etc/X11/xorg.conf
```
and you can then restart the X server by doing
```
 sudo service lightdm start
```

---

### Post by ubunet on 2013-03-07
Some HD videos run slow on SMPlayer with XV output. I change to XV *(0 - AMD RADEON AVIVO VIDEO)* and solved but I need someting like **Anti-aliasing** for better quality. I tried many outputs: gl, gl (fast), gl2, gl2 (fast), gl2 (fast - ati cards) and x11.
I found the link below on web, but I can't try to test because the file xorg.conf doesn't exists:
[http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html](http://www.linuxinsight.com/your-ati-radeon-very-slow-on-xorg-x-server-1.3.html)

I run Xubuntu 12.10 x32 on Acer Aspire One 722 with Radeon card.

---

### Post by Wroger on 2013-10-14
This person did NOT ask how to create an Xconf file, they asked this:

"Where is the Xorg.conf file or equivalent on XFCE?"

OK according to you, it does not come with Xconf, so what is it's equivalent and where is it located?

---

### Post by CatKiller on 2013-10-14
The equivalent is xorg.conf, which is at /etc/X11/xorg.conf when you put it there. Exactly as Cheesemill said.

---

### Post by Favux on 2013-10-14
lol  A bit of pseudo-necromancy Wroger?  Or is ubunet's question your question too?  Let's answer it ...

Ubunet your Find found the new configuration method.  It consists of configuration (.conf) files in /usr/share/X11/xorg.conf.d.  Look in there and you'll see files like 10-evdev.conf.  This supplement to xorg.conf, intended for better auto-configuration, means that in modern systems the xorg.conf file usually isn't generated unless you have something like a proprietary video driver that requires it.  However the Xorg developers have guaranteed that the xorg.conf file will remain valid, i.e. the new system is backwards compatible.  So you can always use a xorg.conf file if you want to, there just usually isn't a need.

You can think of it as working like this, keeping in mind that what runs last controls.  During boot up the xorg.conf file is called and it in turn immediately calls the .conf files in xorg.conf.d.  They run in the order they are numbered and then if there is an actual xorg.conf file it runs.  So whatever is in xorg.conf will override anything in one of the xorg.conf.d directories.  Please notice the syntax of the xorg.conf.d snippets is similar but not the same as the syntax in xorg.conf sections.  They are not interchangeable.  See **man xorg.conf** in a terminal for more detail.

The /usr/share/X11/xorg.conf.d is for the Distro's and you are not suppose to muck with stuff in there.  Instead the user is suppose to put custom files in /etc/X11/xorg.conf.d.  You may need to create that directory.  The .conf files in /etc/X11/xorg.conf.d run after the ones in /usr/share/X11/xorg.conf.d so they control or override anything in /usr/share/X11/xorg.conf.d.  Despite that I still usually number them a bit higher.  So if I'm modifying the 50-wacom.conf in /usr/share/X11/xorg.conf.d I'll call the custom .conf file in /etc/X11/xorg.conf.d 52-wacom.conf.  Maybe a bit of overkill.

---

