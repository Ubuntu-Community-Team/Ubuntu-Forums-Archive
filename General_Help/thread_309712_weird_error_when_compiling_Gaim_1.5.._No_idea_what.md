---
title: "weird error when compiling Gaim 1.5.. No idea what it wants!"
date: 2006-11-30
forum: General Help
---

### Post by studiophi on 2006-11-30
I'm probably an intermediate-level linux user, and this one really has me stumped. When using the **make** command to complie gaim, I get the following output mid-way through the process

[FONT="Courier New"][SIZE="1"]/bin/bash ../libtool --silent --tag=CC --mode=link gcc  -g -O2 -Wall -g3   -o gaim -export-dynamic account.o accountopt.o blist.o buddyicon.o cmds.o connection.o conversation.o core.o debug.o eventloop.o ft.o imgstore.o log.o md5.o network.o notify.o plugin.o pluginpref.o pounce.o prefix.o prefs.o privacy.o proxy.o prpl.o request.o roomlist.o server.o sha.o signals.o status.o stringref.o sound.o sslconn.o util.o value.o xmlnode.o away.o dnd-hints.o gaim-disclosure.o gtkaccount.o gtkcellrendererprogress.o gtkblist.o gtkconn.o gtkconv.o gtkdebug.o gtkdialogs.o gtkeventloop.o gtkft.o gtkimhtml.o gtkimhtmltoolbar.o gtklog.o gtknotify.o gtkplugin.o gtkpluginpref.o gtkprefs.o gtkprivacy.o gtkpounce.o gtkrequest.o gtkroomlist.o gtksound.o gtksourceiter.o gtkutils.o idle.o main.o session.o stock.o themes.o -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lgdk_pixbuf-2.0 -lm -lpangocairo-1.0 -lfontconfig -lXext -lXrender -lXinerama -lXi -lXrandr -lXcursor -lXfixes -lpango-1.0 -lcairo -lX11 -lgobject-2.0 -lgmodule-2.0 -ldl -lglib-2.0      -LNONE -lSM -lICE    -lnsl
../libtool: line 1799: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
make[3]: *** [gaim] Error 1
make[3]: Leaving directory `/home/steve/Downloads/gaim-1.5.0/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/steve/Downloads/gaim-1.5.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/steve/Downloads/gaim-1.5.0'
make: *** [all] Error 2
steve@steve-laptop:~/Downloads/gaim-1.5.0$     [/SIZE][/FONT]

I did a **sudo apt-get install libtool**, but the results were the same

Any help or advice is greatly appreciated!

---

### Post by po0f on 2006-11-30
studiophi,

Any specific reason you're compiling Gaim from source?  1.5 is the default for Dapper, and 2.0beta is the default for Edgy/Dapper backports.

---

### Post by studiophi on 2006-11-30
Yes there is. I'd like to use the qrc plugin, which is not gaim 2.0 compatible.

---

### Post by studiophi on 2006-12-04
Am I to understand by this that nobody can successfully compile gaim?

---

