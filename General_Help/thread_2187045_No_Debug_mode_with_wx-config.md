---
title: "No Debug mode with wx-config"
date: 2013-11-10
forum: General Help
---

### Post by matthieu.brunet on 2013-11-10
Hello,

I have an Ubuntu 12.04 LTS.

I have a problem when developing using wxWidgets (the IDE I use is CodeLite).

Indeed, wx-config tools seems not to know the option --debug=yes

```
$ wx-config --cxxflags --unicode=yes --debug=yes

  Warning: No config found to match: /usr/bin/wx-config --cxxflags --unicode=yes --debug=yes
           in /usr/lib/i386-linux-gnu/wx/config
  If you require this configuration, please install the desired
  library build.  If this is part of an automated configuration
  test and no other errors occur, you may safely ignore it.
  You may use wx-config --list to see all configs available in
  the default prefix.

```

If I replace --debug=yes by --debug=no, everything goes smoothly (although it prevents me from debugging my program:

```
$ wx-config --cxxflags --unicode=yes --debug=no
-I/usr/lib/i386-linux-gnu/wx/include/gtk2-unicode-release-2.8 -I/usr/include/wx-2.8 -D_FILE_OFFSET_BITS=64 -D_LARGE_FILES -D__WXGTK__ -pthread

```

As I have libwxgtk2.8-dev installed, this problem seems odd to me.

```
$ dpkg --get-selections |grep wx
libalien-wxwidgets-perl                install
libwx-perl                    install
libwx-perl-processstream-perl            install
libwxbase2.6-0                    install
libwxbase2.8-0                    install
libwxbase2.8-dev                install
libwxgtk2.8-0                    install
libwxgtk2.8-dev                    install
libwxsmithlib0                    install
libwxsqlite3-2.8-0                install
wx-common                    install
wx2.8-doc                    install
wx2.8-examples                    install
wx2.8-headers                    install
wxformbuilder                    install
```

Thanks in advance for any help.

---

### Post by oldos2er on 2013-11-10
Moved to General Help.

---

### Post by danh-h on 2013-11-12
Matthieu, have you tried installing libwxgtk2.8-dbg?

I ran into a wx-config problem with lack of debug and that helped.

[Note: i'm responding on this page because this is the page google sent me to --- not quite sure how to move to General Help, per oldos2er, elsewhere in this thread.]

---

### Post by matthieu.brunet on 2013-11-14
Thanks. That solved my problem (Ubuntu admins: it may be good to include the dependency for newbies like me).

---

