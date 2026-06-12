---
title: "Monitor &amp; Display (in System Settings) not working"
date: 2006-10-26
forum: General Help
---

### Post by jasutton on 2006-10-26
Strange problem here...

I just upgraded to Kubuntu edgy from dapper (switched my sources.list to point to the edgy repos, and did apt-get dist-upgrade).  Before the upgrade I had been running two 17" monitors with one running at 1152x864 and the other at 1024x768 (I wanted both running 1152x864, but I couldn't get it working quickly, so I just gave up).  So, I figured I'd try to get both running at 1152x864 now.  However, I cannot get into the System Settings -> Monitor & Display.  It displays the following error:

```
The module Monitor & Display could not be loaded.


The diagnostics is[sic]:

Possible reasons:

  * An error occurred during your last KDE upgrade leaving an orphaned control module
  * You have old third party modules lying around.

Check these points carefully and try to remove the module mentioned in the error message.  If this fails, consider contacting your distributor or packager.
```

I did a little searching around on the forums and elsewhere, and I found someone requested that I do 'kcmshell displayconfig' and post the terminal output, so I'll do that here:

```
jasutton@cs13217:/usr/share/apps/guidance$ kcmshell displayconfig


Pythonize constructor -- pid = 7926
Python interpreter initialized!



Pythonize constructor -- pid = 7926
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.4/displayconfig.py", line 1685, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.4/displayconfig.py", line 441, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 387, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 392, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 1101, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 1554, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.4/xf86misc.py", line 62, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range
error: *** runFunction failure
;
```

Anyone else having this problem, or is it just me?

While I've got this thread open, anyone know how to actually make Xorg do a resolution change?  I mean, if I edit /etc/X11/xorg.conf manually, and add a resolution in for the monitor in question, the resolution will not change.  How do I force Xorg to run a particular monitor at a particular resolution given my Xinerama setup?

---

### Post by gnumbo on 2006-10-28
Exact same problem. Otherwise, smooth upgrade.

any ideas, huh?

---

### Post by jasutton on 2006-10-29
I did see somewhere that it could be some options in my xorg.conf that was messing it up.  I may just do a clean install to see if that solves the problem (rather than an upgrade)...

---

### Post by jasutton on 2006-10-30
There's a bug report [here]("https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/32915") about this issue.  I've added a comment noting that it's still an issue with Edgy.

---

### Post by vidak on 2006-11-15
> **jasutton said:**
> There's a bug report [here]("https://launchpad.net/distros/ubuntu/+source/kde-guidance/+bug/32915") about this issue.  I've added a comment noting that it's still an issue with Edgy.

I tried all the listed workaround on that page, but none helped. Posted another comment to the bug.
Any further ideas?

The posted comment to the page:
---------------------------
I'm using the same (kde-guidance 0.7.0-0ubuntu4) package, and still having problems with my i915 card. Tried to edit /usr/share/apps/guidance/pcitable, but my card was correctly on the list, so there was nothing to do... The xorg.conf-workaround didn't help, either.

The module dies with these words:


Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.4/displayconfig.py", line 1685, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/python-support/python2.4/displayconfig.py", line 478, in __init__
    self._loadConfig()
  File "/var/lib/python-support/python2.4/displayconfig.py", line 1029, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list
error: *** runFunction failure
;

---

### Post by squix on 2006-11-17
exactly the same as vidak. i tried workarounds with no success.
using edgy with the same (kde-guidance 0.7.0-0ubuntu4) package and nVidia GF Go 7300.

---

### Post by plcdfa on 2006-11-18
I have the exact same problem here. I didn't upgrade though, I did a clean install. None of the aformentioned workarounds solved it either. But: (!) I am curious about one thing: do any of you use the US English language in Regional & Settings? Cos I experience this strange thing: when I set the system language to English the module is working perfectly, while when KDE's in Hungarian it's the same as in your case.

---

### Post by vidak on 2006-11-18
> **plcdfa said:**
> I have the exact same problem here. I didn't upgrade though, I did a clean install. None of the aformentioned workarounds solved it either. But: (!) I am curious about one thing: do any of you use the US English language in Regional & Settings? Cos I experience this strange thing: when I set the system language to English the module is working perfectly, while when KDE's in Hungarian it's the same as in your case.

Geez... Indeed, when switching language from Hungarian to English, the problem is solved... ](*,) This place must be doomed for some reason :)
Btw. as fas as I remember when I installed Kubuntu on a new PC, the menu worked correctly with Hungarian language settings (it was however a 64bit pc)

Any ideas how to get this work correctly?

---

### Post by plcdfa on 2006-11-18
Was that edgy too? Cos I just tried 64-bit edgy a few days ago and the problem was definitely present there as well. I would vote for a broken translation file causing the problem, but I doubt that the other posters in this thread were all Hungarian too. :)

Anyhow, should I find a workaround I will post it here.

---

### Post by vidak on 2006-11-18
> **plcdfa said:**
> Was that edgy too? Cos I just tried 64-bit edgy a few days ago and the problem was definitely present there as well. I would vote for a broken translation file causing the problem, but I doubt that the other posters in this thread were all Hungarian too. :)

Yes, it was edgy. how well do you understand python? What could 

Traceback (most recent call last):
  File "/usr/bin/displayconfig", line 1707, in ?
    displayapp = DisplayApp()
  File "/usr/bin/displayconfig", line 478, in __init__
    self._loadConfig()
  File "/usr/bin/displayconfig", line 1029, in _loadConfig
    self.targetgamma = self.availabletargetgammas.index(t)
ValueError: list.index(x): x not in list

(the output of displayconfig) mean?

---

### Post by plcdfa on 2006-11-18
> **vidak said:**
> Yes, it was edgy. how well do you understand python? 
Not at all. I wish it were C or Java, but apparently it isn't. :evil: 
I commented out the line which causes the error, but that produceded other errors. (The targetgamma attribute was left uninitialised. Then I tried commenting out all the lines referencing the attribute, but that didn't seem to have any effect. :confused: ) I fear that without any knowledge of the language I can't do anything else. Maybe someone with deeper python knowledge will come to our help.

---

### Post by vidak on 2006-11-18
> **plcdfa said:**
> Not at all. I wish it were C or Java, but apparently it isn't. :evil: 
I commented out the line which causes the error, but that produceded other errors. (The targetgamma attribute was left uninitialised. Then I tried commenting out all the lines referencing the attribute, but that didn't seem to have any effect. :confused: ) I fear that without any knowledge of the language I can't do anything else. Maybe someone with deeper python knowledge will come to our help.

Got it. Copy your displayconfig.py somewhere, and change a part of it around line 1024 just to see the problem:
```

    def _loadConfig(self):
        self.config.setGroup("General")
        t = self.config.readEntry("targetgamma","2.0")
#        if t in self.availabletargetgammas:
#            t = '2.0'
#        self.targetgamma = self.availabletargetgammas.index(t)
        print self.availabletargetgammas
        if t in self.availabletargetgammas:
            t = '2.0'
        print "DEBUG " + t + str(type(t))
        self.targetgamma = self.availabletargetgammas.index(t)
#       self.targetgamma=2

```

Now run the script, take a big breath and look what 
```

print self.availabletargetgammas

```
does:
[u'1,4', u'1,6', u'1,8', u'2,0', u'2,2', u'2,4']

Which is a list of the available gamma values - as I see, there should be dots... ](*,) Sure you can scream...
I just don't understand, why we have to do any internationalization with a number...

Now let's find line 431 where this list is made and delete the i18n parts, to get
```

self.availabletargetgammas = [unicode(('1.4')),unicode(('1.6')),unicode(('1.8')),unicode(('2.0')),unicode(('2.2')),unicode(('2.4'))]

```
](*,)  ](*,) ](*,) !
The problem is solved (after ~half a year...)

(Another way to debug the script is eg. to put unicode(i18n()) into lines 1028 and 1034 'around' 2.0 values to change the dots to commas)

---

### Post by plcdfa on 2006-11-18
So that's it. Thank you for the solution. =D> I hope I won't run into any more annoying bugs like this, I've had enough of them for now. Edgy seems to be the most buggy Ubuntu release so far. (I haven't tried Warty tough.) Maybe the shorter development/testing time...

---

### Post by vidak on 2006-11-18
> **plcdfa said:**
> So that's it. Thank you for the solution. =D> I hope I won't run into any more annoying bugs like this, I've had enough of them for now. Edgy seems to be the most buggy Ubuntu release so far. (I haven't tried Warty tough.) Maybe the shorter development/testing time...

I could never make it if you don't tell that bug doesn't exist with the English language settings... :)

---

