---
title: "Problem with checkinstall and Pidgin."
date: 2007-05-07
forum: General Help
---

### Post by Cable on 2007-05-07
I'm trying to compile and install Pidgin from source.  The compiling finishes fine.  When checkinstall builds the debian package, it succeeds.  However, when it attempts to install it, it fails.  Here is the error in the log...any ideas on how to fix this?

Also, I'm doing this in Kubuntu.
```

(Reading database ... 113109 files and directories currently installed.)
Unpacking pidgin (from .../pidgin_2.0.0-1_i386.deb) ...
dpkg: pidgin: warning - conffile `etc/gconf' is not a plain file or symlink (= `/etc/gconf')
dpkg: pidgin: warning - conffile `etc/gconf/gconf.xml.defaults' is not a plain file or symlink (= `/etc/gconf/gconf.xml.defaults')
dpkg: error processing /home/caleb/Downloads/Pidgin/pidgin-2.0.0/pidgin_2.0.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/gcc/i486-linux-gnu/4.1.2/collect2', which is also in package gcc-4.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/caleb/Downloads/Pidgin/pidgin-2.0.0/pidgin_2.0.0-1_i386.deb

```

---

### Post by berserker on 2007-05-07
I have a similar error except mine says

```
 trying to overwrite '/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'
```

I couldn't figure out how to fix it so I just ended up downloading and installing one of the debs that you can find on this forum.

---

### Post by Qew on 2007-05-07
The latest Checkinstall has a problem with adding system files to the .deb file. If you use a previous version, like 1.6.0-1 or 1.6.0-2 (which I've used in Dapper with little issue), then the problem should go away. However, be aware that there are other issues with the package that I suggest, although not that serious.

---

### Post by fakie_flip on 2007-05-08
How do you get the previous version of checkinstall in Feisty?

---

### Post by phinn on 2007-05-10
Thats odd I had no problems compiling and installing it from source with my Kubuntu 7.04 box

Sure wish Ubuntu would just freakin put Pidgin 2.0 in their repos already and save 100s of people all this trouble

---

