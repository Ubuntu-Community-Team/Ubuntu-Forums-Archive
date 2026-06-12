---
title: "Nicotine just stopped working. Please Help Me."
date: 2008-02-26
forum: General Help
---

### Post by xOrangeFirex on 2008-02-26
I have been using Ubuntu for a few months now and have yet to come across a problem that I could not fix with a little searching on the forum, but I cannot solve this problem. Nicotine has been working perfectly fine since I started using Ubuntu and now it refuses to start up. All I get is a screen that says Nicotine+ 1.2.8 at the title bar and the screen remains blank. This is what I get when I launch from the terminal (I don't know what much of it means, but perhaps it will help you):

:~$ nicotine
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at [http://sourceforge.net/projects/psyco/](http://sourceforge.net/projects/psyco/)
You do not have Python Vorbis bindings installed. 
Others will not be able to see the lengths and the bitrates 
of Ogg Vorbis files that you share. You can get the from
[http://www.andrewchatham.com/pyogg/](http://www.andrewchatham.com/pyogg/). 
If you're using Debian, install the python-pyvorbis package.

Nicotine supports a country code blocker but that
        requires a (GPL'ed) library called GeoIP. You can find it here:
        C library:       [http://www.maxmind.com/app/c](http://www.maxmind.com/app/c)
        Python bindings: [http://www.maxmind.com/app/python](http://www.maxmind.com/app/python)
        (the python bindings require the C library)

Traceback (most recent call last):
  File "/usr/bin/nicotine", line 156, in <module>
    app = frame.MainApp(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 2230, in __init__
    self.frame = NicotineFrame(config, trayicon)
  File "/var/lib/python-support/python2.5/pynicotine/gtkgui/frame.py", line 412, in __init__
    ConfigUnset = self.np.config.needConfig()
  File "/var/lib/python-support/python2.5/pynicotine/config.py", line 112, in needConfig
    if self.sections[i][j] is None or self.sections[i][j] == '' and i not in ("userinfo", "ui", "ticker", "players") and j not in ("incompletedir", "autoreply", 'afterfinish','afterfolder', 'geoblockcc', 'downloadregexp'):
  File "/usr/lib/python2.5/UserDict.py", line 173, in __cmp__
    return cmp(dict(self.iteritems()), other)
  File "/usr/lib/python2.5/UserDict.py", line 105, in iteritems
    for k in self:
  File "/usr/lib/python2.5/UserDict.py", line 92, in __iter__
    for k in self.keys():
  File "/usr/lib/python2.5/shelve.py", line 92, in keys
    return self.dict.keys()
  File "bsddb/__init__.py", line 252, in keys
  File "bsddb/dbutils.py", line 62, in DeadlockWrap
bsddb.db.DBPageNotFoundError: (-30987, 'DB_PAGE_NOTFOUND: Requested page not found')
Killed

---

### Post by videocheez on 2008-03-29
I read somewhere that if you go to the nicotine directory in your home folder and delete all of the files with the *.db suffix and then load the program again your problems will be solved.  This worked for me about a month ago.  I'm trying to find the post again where I read it just to make sure that I'm not steering you in the wrong direction.  Remember to hit control h when you look in the home folder the nicotine directory is hidden.

Try the link below:
[http://ubuntuforums.org/showthread.php?t=363541&highlight=nicotine+fix](http://ubuntuforums.org/showthread.php?t=363541&highlight=nicotine+fix)

---

