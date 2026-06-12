---
title: "SMEG stopped working"
date: 2005-07-22
forum: General Help
---

### Post by Ferio on 2005-07-22
I was adding several games to my Games menu, and in order for them to show up, I had to close it, and when I wanted to add another, re-open it, but after adding adonthell and closing it, it can't be opened again; I've tried to reinstall, but still doesn't work. If I launch it from command line, this is what I get:

 ```
None
Traceback (most recent call last):
  File "/usr/bin/smeg", line 559, in ?
	main()
  File "/usr/bin/smeg", line 555, in main
	smeg = Smeg()
  File "/usr/bin/smeg", line 61, in __init__
	self.handler = MenuHandler(self, self.options)
  File "/usr/lib/smeg/MenuHandler.py", line 57, in __init__
	xdg.MenuEditor.MenuEditor.__init__(self, menu_path, root=options.root_mode)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 27, in __init__
	self.parse(menu, filename, root)
  File "/usr/lib/python2.4/site-packages/xdg/MenuEditor.py", line 41, in parse
	self.menu = parse()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 516, in parse
	__parse(doc, filename, tmp["Root"])
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
	__parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
	__parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 537, in __parse
	__parseMenu(child, filename, parent)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 691, in __parseMenu
	__parse(child, filename, m)
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 571, in __parse
	parent.Rules.append(Rule(child.tagName, child))
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 284, in __init__
	self.compile()
  File "/usr/lib/python2.4/site-packages/xdg/Menu.py", line 290, in compile
	exec("""
  File "<string>", line 6
	elif menuentry.DesktopFileID == 'Waste's Edge.desktop':
										   ^
SyntaxError: invalid syntax
``` 

Any idea? I'd still want to add several games...

---

### Post by Ferio on 2005-07-22
I got it; SMEG seems to have some problems with apostrophes, so I sudo-gedited my /home/my_user/.config/menus/applications.menu and I deleted the Waste's Edge entry, and voila! It works again.

---

