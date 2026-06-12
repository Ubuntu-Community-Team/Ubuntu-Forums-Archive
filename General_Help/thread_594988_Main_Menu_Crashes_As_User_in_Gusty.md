---
title: "Main Menu Crashes As User in Gusty"
date: 2007-10-28
forum: General Help
---

### Post by jlh on 2007-10-28
I just installed Gusty as a clean install.  If I try to launch Main Menu as a user, it crashes.  That's the result whether I right click Application>edit menus, or click on System>Preferences>Main Menu.

If I log in as root, Main Menu works fine.

Going back to user, I can launch the Main Menu interface from the command line using sudo alacarte.  But if I make changes using the interface, they aren't saved - or are ineffective.

If I try to launch main menu as user, with alacarte, I get this message:

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
IOError: [Errno 13] Permission denied: '/home/jay/.config/menus/applications.menu'

I see from other posts that this was a bug in Feisty earlier this year.  Anyone else experiencing this in Gusty?

Thanks.

---

### Post by jlh on 2007-10-29
Adding to my initial post, it occurred to me that maybe I could edit Main Menu by opening a terminal and logging in as root.  When I do that, I get this output:

(alacarte:7120): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

The Main Menu interface launches.  However, if I make any changes, there is no effect.  This is the same experience that I have using the terminal as sudo.

---

### Post by jlh on 2007-10-31
Answering my own post, in case anyone else encounters this.  

There were a bunch of screwed up permissions in my home directory.  Hidden folders, such as .config and .local (and sub-directories) were owned by root.  Upon changing the owner to me as user, I have access, and Main Menu edits fine.:)

---

