---
title: "pyRenamer Not Responding - Troubleshooting"
date: 2014-07-01
forum: General Help
---

### Post by uRock on 2014-07-01
When I open pyRenamer it opens with a blank screen and stays that way until I force it to quit.
[ATTACH=CONFIG]254378[/ATTACH]

When opened via terminal I get```
ubuntu@ubuntu:~$ pyrenamer
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:120: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade_tree = gtk.glade.XML(pyrenamerglob.gladefile, "main_window")

```I have tried reinstalling, but that did no good. **sudo pyrenamer** has the same results. Does anyone have any ideas to help me with troubleshooting this issue?

For the record, I am using ubuntu 14.04 64bit.

Thanks for any and all help!

---

### Post by ibjsb4 on 2014-07-01
Running 32bit and get the same output (warning) from terminal, but mine works.

Edit
When you reinstalled, did you wipe ~/.pyrenamer?

---

### Post by uRock on 2014-07-02
If I open pyRenamer via terminal, then hit Ctrl+c, then the application will open properly with the following output,```
ubuntu@ubuntu:~$ pyrenamer
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:120: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade_tree = gtk.glade.XML(pyrenamerglob.gladefile, "main_window")
^CTraceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/pyrenamer/treefilebrowser.py", line 159, in row_expanded
    self.get_file_list(model, iter, model.get_value(iter,2))
  File "/usr/lib/pymodules/python2.7/pyrenamer/treefilebrowser.py", line 355, in get_file_list
    if ospath.isdir(ospath.join(path,i)) or not self.show_only_dirs:
  File "/usr/lib/python2.7/genericpath.py", line 41, in isdir
    st = os.stat(s)
KeyboardInterrupt
Using hachoir for music renaming.
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:1390: Warning: Source ID 211 was not found when attempting to remove it
  removed = gobject.source_remove(i)

``` Otherwise, it still does the "not responding" thing when opened. ](*,) This time, while it was uninstalled, I went through and deleted any and all of the directories and files related to pyRenamer.

Edit: I ran it again and hit Ctrl+C at the right time and got the following, though it did work for renaming some files.```
ubuntu@ubuntu:~$ pyrenamer
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:120: GtkWarning: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
  self.glade_tree = gtk.glade.XML(pyrenamerglob.gladefile, "main_window")
^CTraceback (most recent call last):
  File "/usr/lib/pymodules/python2.7/pyrenamer/treefilebrowser.py", line 159, in row_expanded
    self.get_file_list(model, iter, model.get_value(iter,2))
  File "/usr/lib/pymodules/python2.7/pyrenamer/treefilebrowser.py", line 355, in get_file_list
    if ospath.isdir(ospath.join(path,i)) or not self.show_only_dirs:
  File "/usr/lib/python2.7/posixpath.py", line 80, in join
    path += '/' + b
KeyboardInterrupt
Using hachoir for music renaming.
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:1390: Warning: Source ID 208 was not found when attempting to remove it
  removed = gobject.source_remove(i)
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:1390: Warning: Source ID 1092 was not found when attempting to remove it
  removed = gobject.source_remove(i)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 1551 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 1930 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 2736 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 3996 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 4717 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 4950 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 5056 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/TreeViewTooltips.py:241: Warning: Source ID 5988 was not found when attempting to remove it
  gobject.source_remove(self.__next)
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:1390: Warning: Source ID 1193 was not found when attempting to remove it
  removed = gobject.source_remove(i)
/usr/lib/pymodules/python2.7/pyrenamer/pyrenamer.py:1390: Warning: Source ID 6328 was not found when attempting to remove it
  removed = gobject.source_remove(i)

```

---

