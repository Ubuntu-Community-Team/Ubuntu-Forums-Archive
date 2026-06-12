---
title: "applications menu show"
date: 2008-05-25
forum: General Help
---

### Post by s-lime on 2008-05-25
I accidentally ran out of free disk space.

So, when I rebooted, Places and System menus worked, just when I click Applications it just colors to blue and nothing expands.

Even if it is almost invisible, but there apperars 1px*1px white dot below the menu. It is just like if someone would uncheck all programs in System -> Preferences -> Main menu.

If I go to System -> Preferences -> Main menu, nothing happens.

What is wrong?

---

### Post by s-lime on 2008-05-25
Is there a cl command for System -> Preferences -> Main menu, so I could see debug data?

---

### Post by s-lime on 2008-05-25
[http://shrani.si/f/30/LO/4FmddwUI/0034.jpg](http://shrani.si/f/30/LO/4FmddwUI/0034.jpg)

This is how it looks. IT'S URGENT!!!!!!!
[SIZE="5"]Ubuntu ought to be a reliable OS, but such things doesn't even happen on windows.[/SIZE]

---

### Post by jimbob on 2008-05-25
What happens when you enter ***[COLOR="Blue"]sudo alacarte[/COLOR]*** from a terminal?

---

### Post by s-lime on 2008-05-25
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



And I got message from Apport: Sorry, Main menu closed unexpectedly.

---

### Post by s-lime on 2008-05-25
I reinstalled the package, and now i get:
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

ANYONE?

---

### Post by jimbob on 2008-05-25
Tell us how you "accidentally" ran out of free disk space.  What did you do to remedy the problem?

---

### Post by s-lime on 2008-05-25
I was downloading something, and before I realised I had 0% free space on /dev/hda1

---

### Post by s-lime on 2008-05-25
How can I fix this bug?

---

### Post by jimbob on 2008-05-25
Boot in recovery mode and run fsck -y and see if it can repair your file system.

---

### Post by s-lime on 2008-05-25
What filesystem... It is nothing wrong with filesystem.
It is a problem with files.

---

### Post by s-lime on 2008-05-25
> **jimbob said:**
> Boot in recovery mode and run fsck -y and see if it can repair your file system.

Did you really expect me to mess with filesystem for nothing????
The problem is probably that menu file hasn't been witten on disk because of lack of space. Where is this file?

---

### Post by jimbob on 2008-05-25
> Did you really expect me to mess with filesystem for nothing????


I don't really expect you to  do anything. Fsck won't "mess" with your file system - if anything it might give some information on what may have happened when you ran out of space.  It appears that something may have become corrupted.

Did you check the output of the system logs when this happened?  How about the output of dmesg?

You can try creating another user and logging in to see if it works for him.  That would would isolate it to something in your own profile.

---

