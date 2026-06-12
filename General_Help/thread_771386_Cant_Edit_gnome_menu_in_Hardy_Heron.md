---
title: "Cant Edit gnome menu in Hardy Heron"
date: 2008-04-27
forum: General Help
---

### Post by bigbrovar on 2008-04-27
I just installed Hardy and i must say its pretty awesome.. the only problem i seem to be having is that i cant seem to edit items displayed in gnome menu .. on gutsy all i have to do is right click on the gnome menu bar apple and choose edit and i would be able to edit edit items in my main menu .. removing programs i don't often use so things dont get clustered ... on Hardy i have found this impossible ... when i try to run the process in terminal by running "alacarte"

/u[PHP]sr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 78, in apport_excepthook
    report_file = open(pr_filename, 'wt')
IOError: [Errno 13] Permission denied: '/var/crash/_usr_bin_alacarte.1000.crash'

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG[/PHP]

dont know if anybody would be able to help me on that .. but i would sure be glad if u can .. thanks

---

### Post by bigbrovar on 2008-04-27
bump!

---

### Post by pravin03 on 2008-08-06
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.5/locale.py", line 443, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.5/locale.py", line 375, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: ml_IN




[COLOR="Magenta"]This is my problem TOO...[/COLOR]

---

### Post by iaculallad on 2008-08-06
You might want to try the gconf-editor. Press Alt+F2 and input "gconf-editor" (that's w/o quote) and press Enter.

---

### Post by pravin03 on 2008-08-06
I solved the problem by enabling language support.But the problem re-appeared now.i don't know why.Any body help me too.

---

### Post by pravin03 on 2008-08-07
what shouls I edit in gconf-editor?

---

### Post by ramjet_1953 on 2008-08-07
What's wrong with navigating to [COLOR="Blue"]System>Preferences>Main Menu[/COLOR]?

You can edit any menu item using this, including, the icon and boot command.

Regards,
Roger :cool:

---

### Post by pravin03 on 2008-08-07
What's wrong with navigating to System>Preferences>Main Menu?




This is also not working

---

### Post by tuxxy on 2008-08-07
Because right clicking your menu and selecting edit brings you to the same main menu eidtor

---

### Post by LowSky on 2008-08-07
I know you guys want to help but the original post was from April

---

### Post by pravin03 on 2008-08-07
so what should i do now?

---

### Post by pravin03 on 2008-08-08
bump

---

### Post by blackswamper on 2008-08-19
I have the same issue (sort of)
I **don't** have a "main menu" option in system...anywhere...(or control panel)
I **can** open the "edit menu" by right clicking and choosing "edit menus"
there isn't an option to add (like there used to be)
I've tried reinstalling gnome-panel and (er...gnome-something else) because I saw that in another thread, but it ended up the same.

---

### Post by blackswamper on 2008-08-19
so, installing "gnome-main-menu"...didn't change a thing, lol

---

### Post by cariboo on 2008-08-19
The easiest way to fix this problem is to create a new user and move all you files but the hidden files and directories  to the new user, then rename your old home directory something like <user>.bak and rename the new directory to your user name. You will have to change ownership of the new directory to your username. 

Jim

---

### Post by SEMW on 2008-08-19
Try:```
sudo apt-get purge alacarte && sudo apt-get install alacarte
```

---

### Post by Bucky Ball on 2008-09-03
[QUOTE=SEMW]sudo apt-get purge alacarte && sudo apt-get install alacarte[/QUOTE]

I had this very problem and have posted about 3 times about it and searched until the tips of me fingers were raw - couldn't change anything in main menu. This fixed everything up just nice, thanx SEMW (I think! Find out in the morning when I am awake!). Was ticking the box for anything in System in the Main Menu and it would just disappear after about a second. Not now. :)

---

