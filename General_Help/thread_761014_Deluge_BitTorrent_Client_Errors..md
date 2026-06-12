---
title: "Deluge BitTorrent Client Errors."
date: 2008-04-20
forum: General Help
---

### Post by dcast on 2008-04-20
Hi, just installed Kubuntu 8.04 X86-64 and I installed my BitTorrent client of choice- Deluge, however when I click to open it just hangs and never opens. Starting it from the terminal spits out:

david@thinkpad:~$ deluge
Traceback (most recent call last):
  File "/usr/bin/deluge", line 123, in <module>
    subprocess.Popen(["dbus-launch", "deluge"] + sys.argv[1:])
  File "/usr/lib/python2.5/subprocess.py", line 594, in __init__
    errread, errwrite)
  File "/usr/lib/python2.5/subprocess.py", line 1147, in _execute_child
    raise child_exception
OSError: [Errno 2] No such file or directory


Anyone have a clue? Thanks for your help.

DCast.

---

### Post by ZNeoDark on 2008-04-26
I had the same problem. I simply installed the package named dbus-x11 and now deluge works.

---

### Post by dcast on 2008-04-26
I also came to that conclusion after spending some time with Google. Thanks for the reply.

---

