---
title: "python idle 2.7 problem on xubuntu 13.10"
date: 2013-10-22
forum: General Help
---

### Post by opodaniel-x on 2013-10-22
I just install fresh xubuntu 13.10 
Linux V 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
and got some problem with IDLE: when I try to open an existing module the window open blank and cannot close. Got the following errors ( reported when started in terminal):

 idle-python2.7 
Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.7/lib-tk/Tkinter.py", line 1473, in __call__
    return self.func(*args)
  File "/usr/lib/python2.7/idlelib/EditorWindow.py", line 937, in open_recent_file
    self.io.open(editFile=fn_closure)
  File "/usr/lib/python2.7/idlelib/IOBinding.py", line 222, in open
    flist.open(filename)
  File "/usr/lib/python2.7/idlelib/FileList.py", line 36, in open
    return self.EditorWindow(self, filename, key)
  File "/usr/lib/python2.7/idlelib/PyShell.py", line 131, in __init__
    EditorWindow.__init__(self, *args)
  File "/usr/lib/python2.7/idlelib/EditorWindow.py", line 323, in __init__
    io.loadfile(filename)
  File "/usr/lib/python2.7/idlelib/IOBinding.py", line 258, in loadfile
    chars = self.decode(chars)
  File "/usr/lib/python2.7/idlelib/IOBinding.py", line 296, in decode
    enc = coding_spec(chars)
  File "/usr/lib/python2.7/idlelib/IOBinding.py", line 129, in coding_spec
    for line in lst:
NameError: global name 'lst' is not defined
Exception in Tkinter callback
Traceback (most recent call last):
  File "/usr/lib/python2.7/lib-tk/Tkinter.py", line 1473, in __call__
    return self.func(*args)
  File "/usr/lib/python2.7/idlelib/EditorWindow.py", line 1025, in close
    self._close()
  File "/usr/lib/python2.7/idlelib/PyShell.py", line 302, in _close
    EditorWindow._close(self)
  File "/usr/lib/python2.7/idlelib/EditorWindow.py", line 1032, in _close
    self.unload_extensions()
  File "/usr/lib/python2.7/idlelib/EditorWindow.py", line 1053, in unload_extensions
    for ins in self.extensions.values():
AttributeError: 'PyShellEditorWindow' object has no attribute 'extensions'

$python -V
Python 2.7.5+

How can I fix this?

---

### Post by ssam on 2013-10-22
You should use launchpad to report bugs [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by cariboo on 2013-10-22
Moved to General Help.

---

### Post by randel on 2013-10-26
Same problem here.  Our whole team is shut-out of IDLE 2.7 development since we upgraded from 13.04 to 13.10.  Right click to open .py files fails.  Opening .py files from within IDLE 2.7 shows an empty file and that same window fails to respond to quits.  Have reinstalled IDLE 2.7 and most Python 2.7.5 files to no avail.

I noticed this in the 13.10 release notes: "We eventually intend to ship only [Python 3]("http://docs.python.org/py3k/whatsnew/3.0.html") with the Ubuntu desktop image, not Python 2." - which means that the 90% of the Python world still using the highly portable 2.7.5 is low priority to the Ubuntu staff.  Which unfortunately might mean that any break they inadvertantly make to 2.7.5 may not get fixed.

[**[COLOR=#000000]opodaniel-x[/COLOR]**]("http://ubuntuforums.org/member.php?u=1860775"), please let us know if you find a work around and we will do the same.

---

### Post by suicide_penguin on 2013-10-27
Edit the file ```
[FONT=Verdana]/usr/lib/python2.7/idlelib/IOBinding.py[/FONT]
``` [FONT=Verdana] and replace this line in [/FONT]coding_spec[FONT=Verdana] function:

[/FONT]```

[FONT=Verdana]str = str.split("\n", 2)[:2]
[/FONT]
```
[FONT=Verdana]
with:

[/FONT]```
[FONT=Verdana]lst = str.split("\n", 2)[:2][/FONT]
```

---

### Post by randel on 2013-10-27
[**[COLOR=#000000]suicide_penguin[/COLOR]**]("http://ubuntuforums.org/member.php?u=1376078"), that worked, that worked!!!

[**[COLOR=#000000]opodaniel-x[/COLOR]**]("http://ubuntuforums.org/member.php?u=1860775"), SOLVED!

[**[COLOR=#000000]suicide_penguin[/COLOR]**]("http://ubuntuforums.org/member.php?u=1376078"), if you have any spare time, I, and I'm sure others, would love a quick comment on what that change did.

---

### Post by suicide_penguin on 2013-10-27
It was a typo in the source code. ;-)

They were using a variable named **lst **in the source code to iterate over the first list returned by **str.split("\n", 2)[:2], **but they never defined any such variable.

---

### Post by jakereich on 2013-12-20
Sorry if this a silly question, but I'm new to Ububtu and IDLE. How do I change the permissions to be able to fix the code outlined above? I tried with chmod but I get a message telling me that I don't have permission to change the permission. Thanks for any help.

---

### Post by kaustubh.cool on 2013-12-25
Use sudo to edit the file.

---

### Post by PopsTheSailor on 2014-01-18
jakereich,
you never responded back so I'm assuming you are good to go now but just in case, you would use: sudo gedit IOBinding.py to edit the file. Issue the command from the directly where the file exists ([FONT=Verdana]/usr/lib/python2.7/idlelib).
[/FONT]
 Putting sudo in front of commands gives you higher access rights. Sudo stands for "super user do" and is a standard way of doing stuff that your normal user rights don't have. Just understand that along with more power comes the ability to do more damage to your install!

Oh yea, and this fix worked for me as well so thanks S-Penguin!

---

