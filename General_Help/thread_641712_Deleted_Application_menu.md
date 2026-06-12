---
title: "Deleted Application menu"
date: 2007-12-15
forum: General Help
---

### Post by notanoob on 2007-12-15
hi,
Im on ubuntu gutsy, i think i deleted everything in the applications menu.  I went to system, preferences, main menu, and i tried to delete an app from the menu, but instead i think i deleted everything in it. I tried to add a new menu bar, but it didnt work. i still have the menu bar, thks for any help.

---

### Post by lonniehenry on 2007-12-15
open a terminal (applications, applications, terminal) and type alacarte. it will open a gui that you can check the items that you want to appear in the menus.

---

### Post by notanoob on 2007-12-15
thks, but will i be able to open the terminal?

---

### Post by notanoob on 2007-12-15
wait, i tried opening the app, main menu, from preferances, but it wont start,

---

### Post by lonniehenry on 2007-12-15
try up in the corner Applications, accessories, terminal,  should open the terminal window that should have a prompt.~$   type the word alacarte and enter.  this should bring up a gui that should have  all of the choices for the menus that appear in the top bar.  check the ones that you want.

---

### Post by notanoob on 2007-12-15
but the accerrories and other stuff r gone, i lost the lauchers 4 tha stuff,like my games, sound and video, and all other things in tha applications men. thks, tho

Its all empty when i try 2 open it, 2, except 4 a white square

---

### Post by t-bone510 on 2007-12-15
can you run things by pressing alt+f2?

push alt+f2 and then type ```
gnome-terminal
```

---

### Post by lonniehenry on 2007-12-15
Sorry, you have something I haven't happened across.  Maybe there is someone else out there that can help.

---

### Post by notanoob on 2007-12-15
thks t-bone i got tha terminal, but when i typed alacarte i got this
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
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

---

### Post by t-bone510 on 2007-12-15
hmmm


try 

```
sudo apt-get install alacarte
```

---

### Post by notanoob on 2007-12-15
ty but it says "Reading package lists... Done
Building dependency tree       
Reading state information... Done
alacarte is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."

---

### Post by t-bone510 on 2007-12-15
then its already installed. 

we could try removing and putting it back

```
sudo apt-get remove alacarte
```

```
sudo apt-get install alacarte
```

```
alacarte
```


see if it works then

---

### Post by notanoob on 2007-12-15
same error

---

### Post by t-bone510 on 2007-12-15
This can help. [http://ubuntuforums.org/showthread.php?t=633385](http://ubuntuforums.org/showthread.php?t=633385)

---

### Post by notanoob on 2007-12-15
just in case heres wat it said
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
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/minidom.py", line 1915, in parse
    return expatbuilder.parse(file)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 926, in parse
    result = builder.parseFile(fp)
  File "/usr/lib/python2.5/site-packages/_xmlplus/dom/expatbuilder.py", line 211, in parseFile
    parser.Parse("", True)
xml.parsers.expat.ExpatError: no element found: line 1, column 0

---

