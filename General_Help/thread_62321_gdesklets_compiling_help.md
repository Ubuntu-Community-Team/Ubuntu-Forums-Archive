---
title: "gdesklets compiling help"
date: 2005-09-04
forum: General Help
---

### Post by Linux_Noob on 2005-09-04
checking for pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0... Package ORBit-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `ORBit-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'ORBit-2.0', required by 'PyORBit', not found

configure: error: Library requirements (pygtk-2.0 >= 2.4.0 pyorbit-2 >= 2.0.1 gnome-python-2.0 >= 2.6.0) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.



This is the error msg i get when i try to compile gdesklets -0.35.2.
HELP!!!!!

---

### Post by ZaherM on 2005-09-04
Hi there,
no need to compile it by yourself, here I'll quote from another message at the forum:
[QUOTE=Seth]Here it is backported in the manner of official Backports, so it's not "Use at Your Own Risk" :P

[http://sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.2-1~5.04ubp1_i386.deb](http://sethkinast.com/ubuntu/hoary/backports/gdesklets_0.35.2-1~5.04ubp1_i386.deb)

EDIT: And here's -data.
[http://sethkinast.com/ubuntu/hoary/backports/gdesklets-data_0.35.2-3_all.deb](http://sethkinast.com/ubuntu/hoary/backports/gdesklets-data_0.35.2-3_all.deb)[/QUOTE]

Now,
Download the two packages.
After it
```

sudo dpkg -i gdesklets_0.35.2-1~5.04ubp1_i386.deb
sudo dpkg -i gdesklets-data_0.35.2-3_all.deb

```

And you got it running within dealing with Compiling :)

Have a good day.

---

