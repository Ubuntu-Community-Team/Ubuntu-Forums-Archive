---
title: "Unable to install wxPython through PIP or PIP3"
date: 2016-03-18
forum: General Help
---

### Post by Ravi_Raj on 2016-03-18
Hello there, 

I am using Ubuntu 14.04 and trying to install wxPython-Phoenix with the following commands:

```
sudo pip3 install -U --pre --trusted-host wxpython.org -f http://wxpython.org/Phoenix/snapshot-builds/ wxPython_Phoenix
```

and

```
sudo pip install -U --pre --trusted-host wxpython.org -f http://wxpython.org/Phoenix/snapshot-builds/ wxPython_Phoenix
```

but every time its showing lots of deprecated warnings and exiting with error code 1.

here is the complete error code:
```
Command "/usr/bin/python3.4 -u -c "import setuptools, tokenize;__file__='/tmp/pip-build-k07d6fqk/wxPython-Phoenix/setup.py';exec(compile(getattr(tokenize, 'open', open)(__file__).read().replace('\r\n', '\n'), __file__, 'exec'))" install --record /tmp/pip-1dpj1d10-record/install-record.txt --single-version-externally-managed --compile" failed with error code 1 in /tmp/pip-build-k07d6fqk/wxPython-Phoenix/
```

Please help.

---

### Post by Ravi_Raj on 2016-03-19
Please anybody there to help...

---

### Post by jemanente on 2016-07-25
You must install all previous requeriments in Ubuntu with sudo apt-get install ...... Sorry for my bad English

[LIST]
[*]dpkg-dev
[*]build-essential
[*]python3.4-dev     # use appropriate Python version
[*]libwebkitgtk-dev
[*]libjpeg-dev
[*]libtiff-dev
[*]libgtk2.0-dev
[*]libsdl1.2-dev
[*]libgstreamer-plugins-base0.10-dev
[*]libnotify-dev
[*]freeglut3
[*]freeglut3-dev
[/LIST]

---

