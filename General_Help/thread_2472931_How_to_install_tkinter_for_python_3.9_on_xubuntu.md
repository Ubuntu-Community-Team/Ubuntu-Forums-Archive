---
title: "How to install tkinter for python 3.9 on xubuntu"
date: 2022-03-17
forum: General Help
---

### Post by saulspatz on 2022-03-17
I have installed python 3.9 with "sudo apt install python3.9" but it didn't come with tkinter.  When I try "sudo apt install python3-tk" I get the message

python3-tk is already the newest version (3.8.10-0ubuntu1~20.04).    0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

When I try "sudo apt install python3.9-tk" I get "Note, selecting 'python3-tk' instead of 'python3.9-tk'" and then then the same message as before.

I have a python3.9 directory under both /lib and /usr/lib, but neither contains a tkinter subdirectory.  Both /lib and /usr/lib contain a tcltk directory.  Under python 3.8, tkinter works fine.  

I've seen various posts on the web that say that both "sudo apt install python3-tk" and "sudo apt install python3.9-tk" should work, so I think there must be something wrong on my system, but I don't know how to troubleshoot it.

You can see a discussion of this problem at [https://askubuntu.com/questions/1397737/how-to-install-tkinter-for-python-3-9-on-xubuntu-20-04?noredirect=1#comment2421558_1397737](https://askubuntu.com/questions/1397737/how-to-install-tkinter-for-python-3-9-on-xubuntu-20-04?noredirect=1#comment2421558_1397737)

---

### Post by dragonfly41 on 2022-03-17
Troubleshooting. Try running command

pip3 list

to see what is installed

and .. python3
>>> import tkinter

---

### Post by saulspatz on 2022-03-17
I know that tkinter is not installed.  My question is about how to fix the installation.

---

### Post by ActionParsnip on 2022-03-17
[https://askubuntu.com/questions/1224230/how-to-install-tkinter-for-python-3-8](https://askubuntu.com/questions/1224230/how-to-install-tkinter-for-python-3-8)

Has a PPA for python 3.8. The deadsnakes PPA has lots of python versions. Use at your own risk

---

