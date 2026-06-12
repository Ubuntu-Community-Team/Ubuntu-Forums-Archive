---
title: "[Python] Strange behavior in help&gt; prompt"
date: 2013-04-05
forum: General Help
---

### Post by ramidavis on 2013-04-05
I am running on ubuntu 11.04, python 2.7.1+, and i have also installed kde with sudo apt-get install kde-standard kde-full basket.
I chose gdm as defualt display manager during kde install when it was setting up kdm. I am running in ubuntu classic, and am running the proprietary ATI driver.
Linux kernel 2.6.38-16-generic-pae.

I seem to be having a error with python, specifically when i try to use the built in help.
Upon entering " modules " at the help> prompt, i get this:
```

	help> modules

	Please wait a moment while I gather a list of all available modules...

	 * Detected Session: gnome
	 * Searching for installed applications...
	Backend     : gconf
	Integration : true
	Profile     : default
	Initializing decor options...done
	 * Starting Metacity


```It just sits there like that, and i have to press ctrl+c. When i do that, i get this:
```

	^CTraceback (most recent call last):
	  File "<stdin>", line 1, in <module>
	  File "/usr/lib/python2.7/site.py", line 469, in __call__
	    return pydoc.help(*args, **kwds)
	  File "/usr/lib/python2.7/pydoc.py", line 1727, in __call__
	    self.interact()
	  File "/usr/lib/python2.7/pydoc.py", line 1745, in interact
	    self.help(request)
	  File "/usr/lib/python2.7/pydoc.py", line 1763, in help
	    elif request == 'modules': self.listmodules()
	  File "/usr/lib/python2.7/pydoc.py", line 1884, in listmodules
	    ModuleScanner().run(callback, onerror=onerror)
	  File "/usr/lib/python2.7/pydoc.py", line 1935, in run
	    for importer, modname, ispkg in pkgutil.walk_packages(onerror=onerror):
	  File "/usr/lib/python2.7/pkgutil.py", line 125, in walk_packages
	    for item in walk_packages(path, name+'.', onerror):
	  File "/usr/lib/python2.7/pkgutil.py", line 110, in walk_packages
	    __import__(name)
	  File "/usr/lib/python2.7/dist-packages/FusionIcon/interface_gtk/__init__.py", line 3, in <module>
	    import main
	  File "/usr/lib/python2.7/dist-packages/FusionIcon/interface_gtk/main.py", line 213, in <module>
	    gtk.main()
	KeyboardInterrupt
	>>> 


```It seems the window manager reloads during this, and leaves me unable to type in the terminal, and without window borders.
Thankfully, i have a launcher set up in my panel that runs 'compiz --replace', which gets me back to being able to type again and my window borders back.
I removed fusion-icon, then tried again... Now when i enter " modules " at the help> prompt, kwallet comes up! ???:
```

	Python 2.7.1+ (r271:86832, Sep 27 2012, 21:16:52) 
	[GCC 4.5.2] on linux2
	Type "help", "copyright", "credits" or "license" for more information.
	>>> help()

	Welcome to Python 2.7!  This is the online help utility.

	If this is your first time using Python, you should definitely check out
	the tutorial on the Internet at http://docs.python.org/tutorial/.

	Enter the name of any module, keyword, or topic to get help on writing
	Python programs and using Python modules.  To quit this help utility and
	return to the interpreter, just type "quit".

	To get a list of available modules, keywords, or topics, type "modules",
	"keywords", or "topics".  Each module also comes with a one-line summary
	of what it does; to list the modules whose summaries contain a given word
	such as "spam", type "modules spam".

	help> modules

	Please wait a moment while I gather a list of all available modules...
```

	Kwallet window comes up now. After i close it, the next screen of text comes up:```


	/usr/lib/python2.7/dist-packages/zope/__init__.py:3: UserWarning: Module test was already imported from /usr/lib/python2.7/test/__init__.pyc, but /usr/lib/pymodules/python2.7 is being added to sys.path
	  import pkg_resources
	/usr/lib/python2.7/dist-packages/twisted/words/im/__init__.py:8: UserWarning: twisted.im will be undergoing a rewrite at some point in the future.
	  warnings.warn("twisted.im will be undergoing a rewrite at some point in the future.")

	< module list snipped out to save space >

	Enter any module name to get more help.  Or, type "modules spam" to search
	for modules whose descriptions contain the word "spam".

	help>


```And, this is what i get if i try and run it under ubuntu (safe mode):
```

	Python 2.7.1+ (r271:86832, Sep 27 2012, 21:16:52) 
	[GCC 4.5.2] on linux2
	Type "help", "copyright", "credits" or "license" for more information.
	>>> help()

	Welcome to Python 2.7!  This is the online help utility.

	If this is your first time using Python, you should definitely check out
	the tutorial on the Internet at http://docs.python.org/tutorial/.

	Enter the name of any module, keyword, or topic to get help on writing
	Python programs and using Python modules.  To quit this help utility and
	return to the interpreter, just type "quit".

	To get a list of available modules, keywords, or topics, type "modules",
	"keywords", or "topics".  Each module also comes with a one-line summary
	of what it does; to list the modules whose summaries contain a given word
	such as "spam", type "modules spam".

	help> modules

	Please wait a moment while I gather a list of all available modules...

	Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
	kbuildsycoca4 running...
	Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)
	QDBusConnection: name 'org.kde.kwalletd' had owner '' but we thought it was ':1.86'
```

Kwallet window comes up now. After i close it, the next screen of text comes up:```


	/usr/lib/python2.7/dist-packages/zope/__init__.py:3: UserWarning: Module test was already imported from /usr/lib/python2.7/test/__init__.pyc, but /usr/lib/pymodules/python2.7 is being added to sys.path
	  import pkg_resources
	/usr/lib/python2.7/dist-packages/twisted/words/im/__init__.py:8: UserWarning: twisted.im will be undergoing a rewrite at some point in the future.
	  warnings.warn("twisted.im will be undergoing a rewrite at some point in the future.")

	< module list snipped out to save space >

	Enter any module name to get more help.  Or, type "modules spam" to search
	for modules whose descriptions contain the word "spam".

	help> 


```I even did a reinstall of the python2.7 package from synaptic.

...I give up...:confused:

UPDATE: I installed python3 (3.2) and now it (well, python3 at least) works. python 2.7.1+ is still acting up though...

---

