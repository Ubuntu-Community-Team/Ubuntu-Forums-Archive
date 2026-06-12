---
title: "Bad harddisk: strange behaviour accessing directory and contents"
date: 2015-01-20
forum: General Help
---

### Post by hvn2 on 2015-01-20
Hi,

Due to bad parts, some of the data (inside a directory) on a harddisk seems no longer fully accessible. Strange is, that via a terminal using ls or cd the message "File or directory does not exist" is given, while it is clearly present. With the content being pdf files, it is stranger that with Evince (Document Viewer) these pdf files can be accessed and viewed without a problem. Is there any explanation for this ?

Thanks.

---

### Post by kpatz on 2015-01-20
Maybe the directory or file name has unprintable characters in it, so typing the name by hand doesn't work.  If you use the tab key to complete the file or directory name in the shell, can you access it then?

For example, type cd followed by the first few characters of the directory name and then hit the tab key.  If that does nothing (if there are multiple directories that start with the letters you typed), hit the tab key twice and you'll get a list.

Another possibility is there is a leading space in the name.  Try **cd "** (that's a double quote) and then hit the tab key a couple times and see what you get.

---

### Post by Holger_Gehrke on 2015-01-20
The filenames inside the directory could be damaged and contain non-printing control-characters. You don't see them, you don't know what they are, so you can't type in the right file name. The filemanager and the 'open'-dialog in a GUI program don't have a problem with it, so they work.

You can make 'ls' show '?' instead of invisible characters by giving the option '--hide-control-chars'. Or you might try using 'debug-fs' to try and correct things. Be warned, though: this is a complex tool and reading the manual thoroughly before use and keeping it at hand during use are very much advised.

---

