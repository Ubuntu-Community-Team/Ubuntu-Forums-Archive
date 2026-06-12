---
title: "amarok freezes every first time I open it"
date: 2008-02-25
forum: General Help
---

### Post by geo909 on 2008-02-25
Hello everybody,

I have a rather strange problem here:
Every time I open amarok for the first time since the booting of my computer it freezes when I press 'play' or double-click a song from the playlist. 
Then I got a "not responding"' message and I choose 'force quit'.

After that, when I open amarok again, it has no such problems, plays everything, no freezes at all..

Always like that. First time freeze,then I force quit, then amarok acts normally the second time

It's really frustrating! Could you please tell me what I should do to fix that?!
Thanks in advance..

---

### Post by danwood76 on 2008-02-25
If when you fresh boot, run amarok from the terminal and see if any errors are outputted to the terminal.
THis might help us debug what causes it.

To run amarok from the terminal just type:
```

amarok

```

and press enter.

---

### Post by geo909 on 2008-02-26
Hello!
Thanks a lot for taking the time to answer!
Ok, I start amarok from the terminal and here's what i get:

```
jorge@jorge-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097e90 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097e90 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
jorge@jorge-desktop:~$ 

```

Now, as always, amarok is freezed, so I force quit and get those lines:

```
jorge@jorge-desktop:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x240009a
DCOP aborting call from 'kded' to 'klauncher'
kded: ERROR: : couldn't create slave : Cannot talk to klauncher

```

I'm not familiar with these messages..
does anyone knows what should I do?!

---

### Post by geo909 on 2008-02-26
By the way, if this helps, here's the output after the second try (when as always amarok succeeds to act normal):

```
jorge@jorge-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097e90 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8097e90 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
jorge@jorge-desktop:~$ 

```

As the lines above appear on the terminal, amarok plays a song normally..

---

### Post by danwood76 on 2008-02-26
Right I just ran mine from the terminal and you have a few extra errors than mine that dont appear in your second run:
```

DCOPClient::attachInternal. Attach failed Could not open network socket
DCOP Cleaning up dead connections.

```

So I think its an issue with the dcop server.
I found this thread which I was redirected to from another thread:
[http://ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver](http://ubuntuforums.org/showthread.php?t=107269&highlight=dcopserver)

One thing you could test to see if this fix would work for you is running amarok for the first time using sudo:
```

sudo amarok

```

if this runs fine then follow the directions in that thread I linked to to fix it.

---

### Post by geo909 on 2008-02-26
thanks again, but unfortunately this one didn't work out for me :(

First of all , rebooting and opening amarok as root didn't fix the problem.
Well, anyway (although I had lost hope) I did:
```
sudo chown -R jorge:jorge /home/jorge/.*

```

(jorge is my username), but it didn't fix that, as I was expecting.
Here's the output again:

```
jorge@jorge-desktop:~$ sudo chown -R jorge:jorge /home/jorge/.*
[sudo] password for jorge:
jorge@jorge-desktop:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8268988 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8268988 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
QColor::setRgb: RGB parameter(s) out of range
jorge@jorge-desktop:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x240009a
DCOP aborting call from 'kded' to 'klauncher'
kded: ERROR: : couldn't create slave : Cannot talk to klauncher
```

Any ideas, now?:confused:

---

### Post by geo909 on 2008-03-08
Anybody?
Please! This still continues..

---

### Post by geo909 on 2008-03-09
Anybody?
Any additional info needed?

---

### Post by Elktro on 2008-06-20
I have the same problem. I can start amarok, but when I start playing weather I click the play button or double-click a song name amarok freezes.

Using amarok 1.4.9.1
Engine: Xine

```

ipoh****@sienipilvi:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bc18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x809bc18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
	StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
ipoh****@sienipilvi:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x360126e
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x360126e
QWidget::setMinimumSize: The smallest allowed size is (0,0)
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3601527
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x3601527

ipoh****@sienipilvi:~$ killall amarok
amarok: no process killed
ipoh****@sienipilvi:~$ killall amarokapp
ipoh****@sienipilvi:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x360009a

```

---

### Post by geo909 on 2008-06-20
Sorry I can't help you on this, I didn't manage to fix it in my case. I don't even have ubuntu now..

---

### Post by danwood76 on 2008-06-21
You might try completely reinstalling amarok.

Open up synaptic and search amarok and right click select completely remove.
Then apply, search again and reinstall it.

---

