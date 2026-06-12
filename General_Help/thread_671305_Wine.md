---
title: "Wine"
date: 2008-01-18
forum: General Help
---

### Post by aLlamaWithARifle on 2008-01-18
Well I'm having a small problem with WINE, it keeps thinking that my windows installation is on C drive when in fact its on my H drive but I can't seem to get it to open my H Drive when I want it to.

How do I go about making WINE open my H drive when I click the "Browse C:/ Drive" button?
Thankyou

---

### Post by jeffus_il on 2008-01-18
Run a program called "Wine Configuration Editor", Use it to set your drive mappings.

or ```
wineconfig
```  in a terminal.

---

### Post by aLlamaWithARifle on 2008-01-19
When I do that I get a message saying that I don't have a windows drive set up and it will do it for me, then if I try typing wineconfig again it just does the same thing.

Also when in the Applications/Wine/Configure Wine section under drives everything seems to be correct c: points to my H:/Windows and so does H drive. But yet I cant seem to access my actual H drive. I've also tried entering H:/ whilst in my home folder but it just says it isn't a valid place.

---

### Post by jeffus_il on 2008-01-19
If you have no important stuff in wine maybe you could delete  your .wine directory and run it with a fresh setup, I am assuming that something there got messed up since wine seems to be behaving badly with it's own config files.

---

### Post by aLlamaWithARifle on 2008-01-19
Well deleting the wine folder launched the wineconfig but still under drive settings it says my Desktop, My docs, my pics, my music and my videos all point into C drive and there doesn't seem to be away to change that to point to my H drive

---

### Post by jeffus_il on 2008-01-19
Can you get to this screen in wineconfig where you can set your drive mappings?

---

### Post by aLlamaWithARifle on 2008-01-19
Yep, I'm in there.

---

### Post by jeffus_il on 2008-01-19
You need to mount you Windows partitions first.

e.g. ```
mount /dev/hda2 /home/me/.wine/doze
```

and use that settings dialog to do the mapping.

---

### Post by aLlamaWithARifle on 2008-01-20
Where abouts in the dialog would I need to type that?

---

### Post by jeffus_il on 2008-01-20
In the screenshot that I posted earlier of wineconfig, the "Drives & Directories" tab it maps C: to ../drive_c by default, in the path box below you can type your new mountpoint and that will now map to C:

---

### Post by aLlamaWithARifle on 2008-01-22
Well I've tried that however the terminal just says...

> Warning: the specified Windows directory L"c:\\windows" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 387, in slotApply
    self.save()
  File "/usr/bin/wineconfig", line 372, in save
    self.drivespage.applyChanges()
  File "/usr/bin/wineconfig", line 622, in applyChanges
    winewrite.SetDriveMappings(self.drives)
  File "/var/lib/python-support/python2.5/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/var/lib/python-support/python2.5/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/rob/.wine/dosdevices/c:/windows/profiles/rob'
Error in sys.excepthook:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/apport_python_hook.py", line 42, in apport_excepthook
    binary = os.path.realpath(os.path.join(os.getcwdu(), sys.argv[0]))
IndexError: list index out of range

Original exception was:
Traceback (most recent call last):
  File "/usr/bin/wineconfig", line 387, in slotApply
    self.save()
  File "/usr/bin/wineconfig", line 372, in save
    self.drivespage.applyChanges()
  File "/usr/bin/wineconfig", line 622, in applyChanges
    winewrite.SetDriveMappings(self.drives)
  File "/var/lib/python-support/python2.5/winewrite.py", line 60, in SetDriveMappings
    SetShellLinks(drives[26:])
  File "/var/lib/python-support/python2.5/winewrite.py", line 63, in SetShellLinks
    existingshelllinks = os.listdir(wineread.winepath + "/dosdevices/c:/windows/profiles/" + os.environ['USER'])
OSError: [Errno 2] No such file or directory: '/home/rob/.wine/dosdevices/c:/windows/profiles/rob'


Not sure how relevant that is but best to be safe then sorry and type the whole lot.
Also I tried...

mount /dev/hda /home/me/.wine/doze

Because the drive with Windows on is the first one however this gives the same error message.

---

