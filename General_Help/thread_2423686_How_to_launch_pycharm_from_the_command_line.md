---
title: "How to launch pycharm from the command line?"
date: 2019-07-27
forum: General Help
---

### Post by phanthaiduong22 on 2019-07-27
How to launch pycharm from the command line?

---

### Post by dragonfly41 on 2019-07-27
Although I installed PyCharm Educational to look at it I opted to use [Atom]("http://atom.io") with Atom python-debugger package.

But to answer your question I went to edit Menus (right click on Ubuntu top bar), selected Programming > PyCharm Edu
and looked at properties:

COMMAND: env BAMF_DESKTOP_FILE_HINT=/var/lib/snapd/desktop/applications/pycharm-educational_pycharm-educational.desktop /snap/bin/pycharm-educational %f

If I run that long command PyCharm launches.

---

