---
title: "Update Manager Issue"
date: 2008-02-25
forum: General Help
---

### Post by Paul Vega on 2008-02-25
I have had this error message display when I tried to open Update Manager;

[COLOR="Red"]Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Malformed line 46 in source list /etc/apt/sources.list (dist parse), E:The list of sources could not be read.'

Can anyone tell me how to fix it?
[/COLOR]
Paul Vega

---

### Post by Jussi Kukkonen on 2008-02-25
That error message tells you the problem: /etc/apt/sources.list is broken somehow on line 46. Paste the file contents here if it looks indecipherable to you.

---

### Post by Paul Vega on 2008-02-25
Thanks Jussi
I would like to fix this myself but do need a pointer or three. How do I locate the corrupt file and in what editor should I open or edit it from?
Paul V

---

### Post by plucky on 2008-02-25
> How do I locate the corrupt file and in what editor should I open or edit it from?

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

This makes a backup copy of your sources list using super user privileges.

```
gksudo gedit /etc/apt/sources.list
```

This uses **gedit** editor with **sudo** privileges so be careful.

Checkout line 46

Good luck

---

### Post by Paul Vega on 2008-02-28
Thank You Plucky

I have found the issue after viewing the file. I made some changes to my software sources. The changes were recommended to fix an issue I was having with ClamAV. The changes didn't seem to help with those issues and have obviously created this latest problem. I have reversed thos changes and will re-read the various posts and suggestions on the ClamAV issue. Thank you for your help.

Paul V

---

