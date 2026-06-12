---
title: "Keyboard input disabled in ?X?"
date: 2008-01-30
forum: General Help
---

### Post by coquinho61 on 2008-01-30
Hello all,

I have a laptop with an USB 2.0 microsoft Natural 4000 keyboard attached. Today, miraculously both the input from my laptop's integrated keyboard and my usb keyboard stopped working.

Now here's the REALLY interesting bit: it only stops working AFTER logging in, and only on my normal user. I added another user in a terminal console and logged into X with that, that's where I'm typing from right now. 

There seemed to have been a very short flash of an error window. Not sure if it was really there, but I think it was. Then keyboard input stopped. Couldn't find the error window. Tried rebooting, no effect. Looked in dmesg, nothing that raised a flag. Booted windows (got dual boot), keyboards working fine. Switched users: keyboards working fine. I have an up-to-date kubuntu install.

Anyone can give me a nudge in the general right direction?

Thanks,

Coquinho

---

### Post by seventhc on 2008-01-30
I'm not sure, but I would try booting into the account where it doesn't work, once it stops responding try unplugging it for a while(15 seconds or so)
then plug it back in, maybe it will reassociate with it.

---

### Post by coquinho61 on 2008-01-30
Thanks for the reply. I tried it and it didn't work. 

The thing is, it is not the usb. My internal laptop-keyboard doesn't function either. And it seems to be user-specific because when I log in as a different user, both keyboards work fine. 

Is there any way I can view error logs, for the problematic user, without needing to type passwords in X?

Coquinho

---

### Post by seventhc on 2008-01-30
Click on System>Administration>System logs
you can view the logs and it shouldn't ask for a password.

---

### Post by coquinho61 on 2008-01-30
Unfortunately, I DO need to type in a password to view my logs. That is, for the user who uses KDE. I use KDE as my default window manager. I know how to find the startup logs using dmesg, but are there any other logs I could view using a terminal login?

---

### Post by seventhc on 2008-01-30
OH, on mine it didn't ask for a password..
I am not to sure which log you need try this
```
gedit /var/log/Xorg.0.log

```or you can do this to list more
```

cd /var/log
ls

```then to read any other log just type gedit in front of the name. like so
gedit Xorg.0.log.old
....you might want to look at those 2

---

### Post by coquinho61 on 2008-01-31
Well, it's definately the window manager. I switched to gnome for my problematic user and no problems there. Also, I managed to get my xsession-errors file from a faulty session in kde. Here is its output. Notice the xmodmap error. Is that it? I don't know for sure how to use xmodmap. The file mentioned, .Xmodmap, does not exist in my home directory....

Xsession: X session started for foo at Thu Jan 31 10:39:45 GMT 2008
startkde: Starting up...
kbuildsycoca running...
*** attempt to put segment in horiz list twice
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
kdecore (KProcess): WARNING: _attachPty() 11
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
kdecore (KProcess): WARNING: _attachPty() 13
kdecore (KProcess): WARNING: _attachPty() 15
kdecore (KProcess): WARNING: _attachPty() 17
kdecore (KProcess): WARNING: _attachPty() 11
kdecore (KProcess): WARNING: _attachPty() 13
kdecore (KProcess): WARNING: _attachPty() 15
kdecore (KProcess): WARNING: _attachPty() 17
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
kdecore (KProcess): WARNING: _attachPty() 11
kdecore (KProcess): WARNING: _attachPty() 13
kdecore (KProcess): WARNING: _attachPty() 15
konsole: WARNING: Unable to use /usr/share/apps/konsole/mc.desktop
konsole: WARNING: Unable to use /usr/share/apps/konsole/sumc.desktop
kdecore (KProcess): WARNING: _attachPty() 11
Could not find 'guidance-power-manager.py' executable.
Ignored duplicate item: Kontact
Ignored duplicate item: KDE Groupware Wizard
Ignored duplicate item: Software Sources
Ignored duplicate item: Printing
Ignored duplicate item: Shared Folders
Ignored duplicate item: Time and Date
Ignored duplicate item: Keyring Manager
Ignored duplicate item: System Monitor
Ignored duplicate item: Services
Ignored duplicate item: Users and Groups
Ignored duplicate item: Network Tools
Ignored duplicate item: KArm
Ignored duplicate item: KDE Groupware Wizard
Ignored duplicate item: KNotes
Ignored duplicate item: Keyring Manager
Ignored duplicate item: Strigi
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809b678 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809b678 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
[COLOR="Red"]STARTUP
/usr/bin/xmodmap:  unable to open file '/home/foo/.Xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.[/COLOR]
kbuildsycoca running...
Reusing existing ksycoca
kdecore (KProcess): WARNING: _attachPty() 13
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80d7b58 ): KAccel object already contains an action name "file_quit"
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80d7b58 ): KAccel object already contains an action name "file_quit"
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
No BT device found
waiting for bt device (un)plug events ...
ksmserver: WARNING: SmsDie timeout, client kwin(10dbc87974000120029754900000054820000)
ksmserver: WARNING: SmsDie timeout, client knotify(10dbc87974000120177602700000067340018)
ksmserver: WARNING: SmsDie WM timeout
ICE default IO error handler doing an exit(), pid = 6868, errno = 0
startkde: Shutting down...
klauncher: Exiting on signal 1
startkde: Running shutdown scripts...
startkde: Done.

---

### Post by seventhc on 2008-01-31
thats definitely the problem
> ... The *xmodmap* program is used to edit and display the  keyboard *modifier map* and *keymap table* that are used by client  applications to convert event keycodes into keysyms.  It is usually run from  the user's session startup script to configure the keyboard according to  personal tastes.heres the link where that came from [http://www.xfree86.org/4.2.0/xmodmap.1.html](http://www.xfree86.org/4.2.0/xmodmap.1.html)

[I]I would search the forums for xmodmap..here a link to a thread with a keyboard error, a little different from yours but dealing with xmodmap.
[/I][http://ubuntuforums.org/showthread.php?t=489454](http://ubuntuforums.org/showthread.php?t=489454)

---

### Post by coquinho61 on 2008-01-31
Found the error. It's freakin' slow keys! Never understood why this is implemented anyway.

Here is the solution, found in [this thread]("http://ubuntuforums.org/showthread.php?t=458036&highlight=kde+lost+keyboard"):

> It sounds as if you may have accidentally switched on an accessibility feature called 'slow keys' by pressing on the shift key for a few seconds. This is a showstopper that has been reported in numerous bug reports and has caused many, many users who've never heard of 'slow keys' to believe that their installation is completely broken.

eg [https://bugs.launchpad.net/ubuntu/+bug/41427](https://bugs.launchpad.net/ubuntu/+bug/41427)

Fortunately you can turn it off with just the mouse by going to the K menu -> Control Centre -> Regional & Accessibility -> Accessibility -> Activation Gestures, and untick the first box ('Use gestures for activating slow keys and sticky keys'). Also go to the Keyboard Filters tab and untick the 'Use slow keys' box if it is ticked. Press apply and you should be OK.

Thanks for the advice!

---

### Post by seventhc on 2008-01-31
wow, I never would have thought of that. Thinking about it, I can't seem to understand a situation where slow keys would be helpful, i mean why have it as an option, who would benefit from that???  Anyway glad you got it fixed. :)

---

### Post by coquinho61 on 2008-01-31
Just to wrap things up for people who will read this post later on, the error on xmodmap is still there, in my .xsession-errors log. So that wasn't it.

---

### Post by seventhc on 2008-01-31
> **coquinho61 said:**
> Just to wrap things up for people who will read this post later on, the error on xmodmap is still there, in my .xsession-errors log. So that wasn't it.
Are you sure you're not reading an old error msg?
It is working now, right?

---

### Post by coquinho61 on 2008-01-31
It is working, yes. The two issues are just unrelated.

---

