---
title: "displayconfig module won't load. ( unsupported locale error )"
date: 2007-01-26
forum: General Help
---

### Post by shadyzay on 2007-01-26
I'm running Kubuntu edgy ( fresh install ),
the Display module refuse to launch, saying: "The module Monitor & Display could not be loaded.... etc"
I checked the shell output of displaysettings, kcontrol, and kcmshell:
```
Pythonize constructor -- pid = 20944
Python interpreter initialized!

Pythonize constructor -- pid = 20944
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_displayconfig
  File "/var/lib/python-support/python2.4/displayconfig.py", line 1685, in create_displayconfig
    return DisplayApp(parent, name)
  File "/var/lib/pyth
on-support/python2.4/displayconfig.py", line 441, in __init__
    self.xsetup = XSetup(self.xconfigpath)
  File "/var/lib/python-support/python2.4/displayconfigabstraction.py", line 72, in __init__
    self.xorg_config = xorgconfig.readConfig(xorg_config_
filename)
  File "/var/lib/python-support/python2.4/xorgconfig.py", line 641, in readConfig
    for row in XorgconfCVSReader(filename=filename).readlines():
  File "/var/lib/python-support/python2.4/xorgconfig.py", line 696, in __init__
    fhandle = code
cs.open(filename,'r',locale.getpreferredencoding(),'replace')
  File "/usr/lib/python2.4/locale.py", line 417, in getpreferredencoding
    setlocale(LC_CTYPE, "")
  File "/usr/lib/python2.4/locale.py", line 381, in setlocale
    return _setlocale(category
, locale)
locale.Error: unsupported locale setting
error: *** runFunction failure
;

```

I've been using Linux for a year (SUSE 10.0) and I have a good background in programming (not python) .. I tried debugging the scripts mentioned in the error trace, but I couldn't go anywhere.
$LANG was set to en_SY, I tried a few things from the web, but nothing changed:
1. changed $LANG to en_US
2. put $LANG back to en_SY , added en_SY to /usr/share/il8n/SUPPORTED and /var/lib/locales/supported.d/en and did a sudo dpkg-reconfigure --force locales
3. added a link: 
  en_SY.utf8 -> en_US.utf8 in /usr/lib/locales

now somehow:
$LANG == en_US.ISO-8859-15 ( I remember choosing UTF-8 sometime during installation ??)
$LANGUAGE == en_US

I didn't exactly know what I was doing, I hope I didn't make a big mess ( I have no idea what's dpkg-reconfigure )

What did I do exactly and how can I get back to utf-8, where can I learn more about locale settings and what can I do to get displayconfig running?

I'm really interested in learning these stuff, I'd appreciate links to tutorials or books.

---

### Post by shadyzay on 2007-01-26
Other modules that refuse to start: 

userconfig
mountconfig

they all give the same error in getpreferredencoding()

---

### Post by lvanderree on 2007-01-28
I have this same error since updated to kde 3.5.6, when trying to go to advanced system settings -> disk and file systems (sorry have dutch translation, so this is my translation back to english which probably isn't exactly what is says in the english control panel).

```


Pythonize constructor -- pid = 21545
Traceback (most recent call last):
  File "<string>", line 8, in kcontrol_bridge_create_mountconfig
  File "/var/lib/python-support/python2.5/mountconfig.py", line 3277, in create_mountconfig
    return MountConfigApp(parent, name)
  File "/var/lib/python-support/python2.5/mountconfig.py", line 2869, in __init__
    self.mounttable = MountTable('/etc/fstab','/etc/mtab')
  File "/var/lib/python-support/python2.5/mountconfig.py", line 1228, in __init__
    fhandle = codecs.open(self.fstab_filename,'r',locale.getpreferredencoding())
  File "/usr/lib/python2.5/locale.py", line 512, in getpreferredencoding
    setlocale(LC_CTYPE, "")
  File "/usr/lib/python2.5/locale.py", line 476, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting
error: *** runFunction failure
;


```


KDE looks a lot faster though, or is that just me...

---

### Post by shadyzay on 2007-01-28
The error just dissapeared!
and somehow now $LANG == en_US.UTF-8 and $LANGUAGE == en_US:en.

@lvanderree: I just migrated from SUSE 10.0 ... everything looks faster not just KDE!

---

### Post by lvanderree on 2007-01-29
I also updated on my laptop and this worked out fine, but the disk and filesystem control panel on my desktop still fails to show up.

If someone knows how to solve this, I would like to hear from him/her.

---

### Post by lvanderree on 2007-01-29
Got it fixed to, 

I had broken my python libraries when experimenting with getting openoffice 2.1, which apparantly didn't sho up until now...

aptitude install update-manager 

fixed it, because this also depended on the other python.

---

