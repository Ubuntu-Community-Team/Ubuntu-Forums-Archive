---
title: "Installed OPENOBD DEB pkg and now I can't find it??"
date: 2013-11-12
forum: General Help
---

### Post by egruber on 2013-11-12
I downloaded a DEB package called OPENOBD to work with my car's OBD scanner.  It installed with Ubuntu Software Center.  But I don't see it anywhere to run it.  It's not in my Applications list.  If I look at Installed Programs in the Software Center it doesn't appear, either.  When I installed it, I did get a warning that it wasn't a quality package, but it gave me the option to install it anyway...which I (stupidly) did.  If I reclick on the DEB package, it opens the software center and allows me to reinstall.  But at this point, I just want to delete it.  If I could find it.  Any ideas??

---

### Post by ian-weisser on 2013-11-12
You downloaded it from where, exactly?

You don't need to find it to delete it. Finding it won't help you delete it. 

Open a terminal and try the **dpkg -L openobd** command to see what the openobd package installed to your system, and where.
Since I don't have openobd, I'll show you an example with a different package, an example package called *hello* (it's a real package in Software Center).
```
$ dpkg -L hello
/.
/usr
/usr/bin
[COLOR=#ff0000]/usr/bin/hello[/COLOR]
/usr/share
/usr/share/man
/usr/share/man/man1
[COLOR=#ff0000]/usr/share/man/man1/hello.1.gz[/COLOR]
/usr/share/doc
/usr/share/doc/hello
/usr/share/doc/hello/copyright
/usr/share/doc/hello/changelog.Debian.gz
/usr/share/doc/hello/NEWS
/usr/share/info
/usr/share/info/hello.info.gz

```

See the entry at /usr/bin/hello? That's where the hello program installed to. If I type the command **/usr/bin/hello**, the program runs and I get a response.

See the entry at /usr/share/man/man1/hello.1.gz? That's an online manual page with lots of information. If I type the command **man hello**, the built-in manual reader will show it to me.

If you really want to delete the obenobd package, try the command **sudo apt-get remove openobd**

---

### Post by egruber on 2013-11-13
This was perfect.  I was able to find it and delete it.  Thanks very much !

I downloaded it from here.  It didn't look like anything odd.

[http://sourceforge.net/apps/mediawiki/openobd/index.php?title=OpenOBD](http://sourceforge.net/apps/mediawiki/openobd/index.php?title=OpenOBD)

---

