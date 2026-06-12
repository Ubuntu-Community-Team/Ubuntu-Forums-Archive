---
title: "Deluge Bittorrent"
date: 2007-12-16
forum: General Help
---

### Post by BBin on 2007-12-16
When I start deluge it just dosn't start. It worked until a few days ago, but I cannot remember changing anything important.
When I start it in the terminal it says:
```

no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 53, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 237, in __init__
    self.config = pref.Preferences(os.path.join(self.base_dir, PREFS_FILENAME))
  File "/var/lib/python-support/python2.5/deluge/pref.py", line 142, in __init__
    self.load(self.config_file)
  File "/var/lib/python-support/python2.5/deluge/pref.py", line 180, in load
    self.dump = pickle.load(pkl_file)
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
KeyError: 'D'

```

---

### Post by toastytaco on 2007-12-16
Try going to your home folder and press 'Ctrl + H' and deleting your '.deluge' folder then restart the program. >>[COLOR="Red"]Warning[/COLOR]<< (All program settings and  info for Deluge will be deleted) This should take it back to default settings again.

---

### Post by BBin on 2007-12-16
There is no hidden file or folder called .deluge

---

### Post by t-bone510 on 2007-12-16
reinstall it...?

---

### Post by c-shadow on 2007-12-16
> **BBin said:**
> There is no hidden file or folder called .deluge

Because it's in  .config in your home folder. Delete it (~/.config/deluge, not the whole .config) and start Deluge again. This worked for me.

---

### Post by toastytaco on 2007-12-16
My mistake..lol...I never used that program and usually makes a hidden folder with the program name  with a '.'  in front of it. I did not know that program put it's settings somewhere else. But that is a little hint on how to quick fix problems with some programs..

---

### Post by BBin on 2007-12-16
Removing that folder worked fine! thanks :)

---

### Post by silviutp on 2008-03-19
Is there another solution for this ?
These removes all previous settings :( and I had to do it few times ( I think this happens after some system updates ).

---

