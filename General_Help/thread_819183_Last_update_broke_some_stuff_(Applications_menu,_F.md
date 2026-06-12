---
title: "Last update broke some stuff (Applications menu, Firefox,..)"
date: 2008-06-05
forum: General Help
---

### Post by perelin on 2008-06-05
Hi everybody,
seems that the last update somehow messed up parts of my applications. I haven't looked at everything but the most disturbing problems are:

Applications menu: everything is gone. Not one single entry left. When i try to System->Preferences->MainMenu nothing happens. When try to start the the Main Menu manager application with "alacarte" from console I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
```

when I go with "sudo alacarte":

```
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 46, in __loadMenus
    self.applications.dom = xml.dom.minidom.parse(self.applications.path)
  File "/usr/lib/python2.5/xml/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 924, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/xml/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0
```

Firefox: history and bookmarks are completly gone. Even the history of the current session is not shown. Bookmarking seems to be disabled too: I cannot bookmark any page, when I try nothing happens, no dialogs, nothing. Plus: the loading indicator on every tab is allways active like the pages never stop loading.

Places menu: my bookmarked network connections are gone.

Amarok and Pidgin seem to work fine. So do most of the gnome applications I could find without Applications menu.

Any ideas anybody? is there someway to rollback an update?

greets from germany

Sebastian

---

### Post by Tom--d on 2008-06-05
Strange.

What update was it?

---

### Post by perelin on 2008-06-05
Hi,
I live in germany and I believe that there were a bunch of updates on tuesday (08.06.03). Believe a kernel update was in there somewhere. I never had problems with bad updates and therefore am not very careful about which update I roll in :) Is there an apt-get history somewhere?

---

### Post by ohiomoto on 2008-06-05
I had the same issue with yesterday's kernel update: [http://ubuntuforums.org/showthread.php?t=818241](http://ubuntuforums.org/showthread.php?t=818241)

Good Luck!

---

### Post by zingo on 2008-09-25
I also have this issue on 8.04.  I have had it for some time but not since june more like begining of September, I don't know if there was an update around the time the application menu dissapered, anyone have a clue on how to get the Application menu back?

There seem to be more people having this problem recently
[http://ge.ubuntuforums.com/showthread.php?t=901401]("http://ge.ubuntuforums.com/showthread.php?t=901401")

Edit 2008-09-25:
Found it in launcepad
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/274077]("https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/274077")

---

