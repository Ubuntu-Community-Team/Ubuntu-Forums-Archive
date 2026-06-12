---
title: "[SOLVED] Gdesklets no longer works!"
date: 2007-11-13
forum: General Help
---

### Post by mahasmb on 2007-11-13
Gdesklets was working fine about a month or so ago. But since then it's simply stopped working. I've tried completely removing it and installing again, I even compiled and installed from a .tar.bz2 file. Nothing gives.

Whenever I open gdesklets an empty gdesklet window pops up and then disappears again.

When I run gdesklets from the terminal, this is what I get:
```

maha@maha-dlu:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: connection timeout
The log file might help in solving the problem.
```

-----------------------
Log file 1
-----------------------
Log messages of /home/maha/.gdesklets/logs/gdesklets%3A0.0.log

==========================================================[11/14/07-18:10:02]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]db type could not be determined
in /usr/local/lib/gdesklets/gdesklets-daemon: line 129 <module>
in /usr/local/lib/gdesklets/gdesklets-daemon: line 110 _gdesklets_main
in /usr/local/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/local/lib/gdesklets/main/Starter.py: line 2 <module>
in /usr/local/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/local/lib/gdesklets/config/DaemonConfigger.py: line 1 <module>
in /usr/local/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/local/lib/gdesklets/config/StateSaver.py: line 128 <module>
in /usr/local/lib/gdesklets/config/StateSaver.py: line 30 __init__
in /usr/local/lib/gdesklets/config/Backend.py: line 68 Backend
in shelve.py: line 225 open
in shelve.py: line 209 __init__
in anydbm.py: line 80 open
[EXC]/usr/lib/python2.5/anydbm.py

[---]   75             mod = _defaultmod
[---]   76         else:
[---]   77             raise error, "need 'c' or 'n' flag to open new db"
[---]   78     elif result == "":
[---]   79         # db type cannot be determined
[ERR]>  80         raise error, "db type could not be determined"
[---]   81     else:
[---]   82         mod = __import__(result)
[---]   83     return mod.open(file, flag, mode)


-----------------------
Log file 2
-----------------------
Log messages of /home/maha/.gdesklets/logs/gdesklets%3A1.0.log
/usr/lib/gdesklets/main/__init__.py:118: GtkDeprecationWarning: gtk.threads_init is deprecated, use gtk.gdk.threads_init instead
  gtk.threads_init()

==========================================================[11/12/07-15:16:15]===
=== Unhandled error! Something bad and unexpected happened. ===

[EXC]db type could not be determined
in /usr/lib/gdesklets/gdesklets-daemon: line 127 <module>
in /usr/lib/gdesklets/gdesklets-daemon: line 114 _gdesklets_main
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/main/Starter.py: line 2 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/DaemonConfigger.py: line 1 <module>
in /usr/lib/gdesklets/utils/ErrorFormatter.py: line 118 _new_imp
in /usr/lib/gdesklets/config/StateSaver.py: line 128 <module>
in /usr/lib/gdesklets/config/StateSaver.py: line 30 __init__
in /usr/lib/gdesklets/config/Backend.py: line 68 Backend
in shelve.py: line 225 open
in shelve.py: line 209 __init__
in anydbm.py: line 80 open
[EXC]/usr/lib/python2.5/anydbm.py

[---]   75             mod = _defaultmod
[---]   76         else:
[---]   77             raise error, "need 'c' or 'n' flag to open new db"
[---]   78     elif result == "":
[---]   79         # db type cannot be determined
[ERR]>  80         raise error, "db type could not be determined"
[---]   81     else:
[---]   82         mod = __import__(result)
[---]   83     return mod.open(file, flag, mode)




Can someone PLEASE help me out with this? Please?

---

### Post by mahasmb on 2007-11-14
How about alternatives?

I've tried SuperKaramba and adesklets but neither seems to work.
[B][SIZE="5"]
[COLOR="Red"]THIS IS ANNOYING AND INFURIATING![/COLOR][/SIZE][/B]

---

### Post by mahasmb on 2007-11-18
I decided to delete the following with the following commands. 

[COLOR="Red"]**BE VERY CAREFUL WHEN DOING THIS! YOU DON'T WANT TO DELETE ANYTHING YOU'LL NEED BY MISTAKE!**[/COLOR]

> 

$ sudo rm -r /home/<YOUR USER NAME>/.gdesklets
$ sudo rm -r /usr/local/lib/gdesklets




Then I re-installed gdesklets from Synaptic and after ***MONTHS*** of pulling my hair out, it finally works. Thank goodness!

---

### Post by fjf on 2007-11-20
Hey, thanks!.  That worked for me too!.

---

