---
title: "Edit menus no workie"
date: 2007-10-22
forum: General Help
---

### Post by pwrstick on 2007-10-22
Right clicking on Applications, selecting Edit Menus results in a "Starting Main Menu" trying to open, but it never goes all the way.

Is there a place to manually edit the menus?  Or does anyone know of a fix?

---

### Post by ofb on 2007-10-22
Just for kicks, try System > Preferences > Main Menu first to see if that works. It shouldn't be any different, but you shouldn't be having a problem either.

The Edit Menu application is Alacarte. I was about to suggest removing and reinstalling, but I see it's one of the apps that removes ubuntu-desktop as well, so can't do that. 

So, try this: enter 'alacarte' in a terminal to see if that results in useful error messages.

I find Alacarte to be horribly buggy and slow myself. If you do find out how to edit the menus manually, please post it back here.

EDIT: You can "mark for reinstallation" in Synaptic. Clearly it's time for me to get some sleep.

---

### Post by forestpixie on 2007-10-22
there's not a problem with removing ubuntu-desktop it's just a meta package - if you take out something that's 'in' the package it removes ubuntu-desktop because you haven't got it all any more

---

### Post by ofb on 2007-10-22
The description for ubuntu-desktop includes: "It is also used to help ensure proper upgrades, so it is recommended that it not be removed." Hence my hesitation to mess with it.

Although in this hypothetical case you'd be putting Alacarte right back in, so as long as you also reinstalled ubuntu-desktop as well then I wouldn't expect a problem.

---

### Post by forestpixie on 2007-10-22
yes - exactly what I do - in Feisty i replaced the standard openoffice - just replaced it when I needed to

---

### Post by pwrstick on 2007-10-22
So running alacarte in a console resulted in:
```
philip@philip-desktop:~$ alacarte
/usr/lib/python2.5/site-packages/apt/progress.py: inconsistent use of tabs and spaces in indentation
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.5/site-packages/Alacarte/MainWindow.py", line 49, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 36, in __init__
    self.__loadMenus()
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 59, in __loadMenus
    self.save(True)
  File "/usr/lib/python2.5/site-packages/Alacarte/MenuEditor.py", line 63, in save
    fd = open(getattr(self, menu).path, 'w')
IOError: [Errno 13] Permission denied: '/home/philip/.config/menus/applications.menu'

```

So am I next going to reinstall ubuntu-desktop?

---

### Post by ofb on 2007-10-22
> **pwrstick said:**
> So am I next going to reinstall ubuntu-desktop?

No. You haven't removed it. And your problem seems to be something else.

There's a related bug report over here.
[https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97460](https://bugs.launchpad.net/ubuntu/+source/alacarte/+bug/97460)

---

### Post by pwrstick on 2007-10-24
> 

OK

I have an update

i changed ownership of files in my home directory in hidden

.local/share/applications and .config/menus

changed ownership to myself rather than root .

Works fine now . Is that how its supposed to be??

regards

rajeev


Thanks for the link!  Works just fine now.

---

