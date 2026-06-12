---
title: "Python modules installed using easy_install have incorrect permissions"
date: 2014-02-02
forum: General Help
---

### Post by forbjok2 on 2014-02-02
On one of my servers running Ubuntu Server, any packages installed using easy_install or pip fail to work.
After some research, I found that the reason for this is that its folder in "/usr/local/lib/python2.7/dist-packages" gets created with incorrect permissions.
On a different server running the same version of Ubuntu, on which things are working, the "dist-packages" folder as well as any subfolders had "rws" permissions for group (which was staff) and r-x permissions for other.
On the problematic server, the "dist-packages" folder originally had "r-x" permissions for group (which was root), and no permissions at all for other.
So I manually changed the group permissions to r-s, the group to staff, and other permissions to "r-x" on my dist-packages folder.
Now, if I manually set these permissions on a package's directory, it works, however every time I install something using easy_install or pip, it gets the wrong permissions by default and I have to change them manually.

What could be the cause of this, and is there any way to fix it?
What exactly is it that determines which permissions installed package directories get?

ADDITIONAL INFO:
I have tried "apt-get purge python-setuptools" and reinstalling it several times, and even manually deleted the /usr/local/lib/python* directories before reinstalling it, but nothing changes. The directories keep getting recreated with incorrect permissions, and even if I fix them, every package installed gets wrong permissions.

---

### Post by christophchamp on 2014-03-20
I have the same problem with one of my boxes running Ubuntu 13.04 (64-bit; kernel: 3.8.0-35-generic #50-Ubuntu SMP). It happens with `pip install` (or `pip install --upgrade`) as well.

Every time I install something with `pip` I have to run: [FONT=Courier New]sudo find /usr/local/lib/python2.7/dist-packages -type f -exec chmod 644 {} \;[/FONT] (and 755 for -type d)

---

