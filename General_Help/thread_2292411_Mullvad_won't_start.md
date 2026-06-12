---
title: "Mullvad won't start"
date: 2015-08-27
forum: General Help
---

### Post by g9534924 on 2015-08-27
after I run sudo mullvad (and clicking on the mullvad icon does nothing)   Setting logging directory to /home/standard/.cache/mullvad/log CRITICAL: An uncaught exception occured: Traceback (most recent call last):   File "/usr/bin/mullvad", line 9, in      load_entry_point('mullvad==51', 'gui_scripts', 'mullvad')()   File "/usr/lib/python2.7/dist-packages/mullvad/mullvad.py", line 1890, in main     settings = config.Settings()   File "/usr/lib/python2.7/dist-packages/mullvad/config.py", line 48, in __init__     self._init_file()   File "/usr/lib/python2.7/dist-packages/mullvad/config.py", line 112, in _init_file     self._sync_file(True)   File "/usr/lib/python2.7/dist-packages/mullvad/config.py", line 126, in _sync_file     self.parser.read(self.path)   File "/usr/lib/python2.7/ConfigParser.py", line 305, in read     self._read(fp, filename)   File "/usr/lib/python2.7/ConfigParser.py", line 512, in _read     raise MissingSectionHeaderError(fpname, lineno, line) MissingSectionHeaderError: File contains no section headers. file: /home/standard/.config/mullvad/settings.ini, line: 1 '&\x95\xe95\xd8\x10\x07\xcd&R\xfb\r\xe5,3h1\x9f1=|\t\xec\xf17\x1d\xbb\x89\xd4\xd2d{\x13\xdd\x91=o\xd5\x9f?\x1cK4fa\xab\xe7,\xe9\xf6\x97\x8f\xdd\xa6E\x1eq\x9a\xa4\xd6}\xb3\x90S\x92D m\xf7\x85\xdd\xfaK\xd9B\xf3\xc0\x1a\x9eW\xd8*\x13\xa9\xd0\xd4\xca\xd4i\xc9I\x963\x121\xcbar\x1a{\xce\xef\xc5A\xe5\xa9\x9e\x9bB\xfc\xeb"\xdf!\x16\x85x\x8e\x88k\xde\xc1\xd4\xad\xba\xe1\xed\xca\x18\xda\xb9*\x11dk\x15\xa71v]fJ\x97\xb6o\x94\xad\x19\x14\xaa\xdf\x866|*\x1e\xa0:#\xc0\xe4\x1b\xec@\x06\xe1\x8e\xab\xe2O\xa5w\x11\xcd\xaf\xd3\xaa*\xbeh\x19\x1dm\x7f\x97$\x1c\xc5_\xb5\xa6\xbcI\xe9]\t\xd1\\g \x8b\xa4^\xc5\xdb\x01\x95\x9a\xe7\x7f\xf7L\x0c\xdf_\xa6og\xfbMb\xe5\xeb6\x00\']P\xc5P\xf1^\xce\xa1\x88G\xcf\x84\xa7\xd6_\x12E\xb8\\\xc3a

---

### Post by g9534924 on 2015-08-30
bump. Have no idea how to fix this

---

