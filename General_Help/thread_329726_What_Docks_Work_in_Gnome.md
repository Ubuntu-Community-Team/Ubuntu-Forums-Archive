---
title: "What Docks Work in Gnome?"
date: 2007-01-02
forum: General Help
---

### Post by Afteraffekt on 2007-01-02
I would appreciate a walk through or how to on how to get a OSX Dock on my Ubuntu 6.10 Installation, how ever if there isn't a stable version I'm not interested, lol

---

### Post by maxamillion on 2007-01-02
[http://www.taimila.com/ubuntuosx.php](http://www.taimila.com/ubuntuosx.php)

---

### Post by Stochastic on 2007-01-02
the two ways I've done it are:

1. Use the Gnome Panel, right click it, select properties.  From within this panel, increase the size to about 45 or so, uncheck the expand option, and if you feel like it go to the background tab and select a transparent background.  After this is done, fill the dock with launchers to suit your needs.  This doesn't look terribly like the mac os launcher but it's the most stable and gnome standards compliant.

2. Install gdesklets and in the configuration menu (should be in the programs>accessories menu) select the "toolbars/launchers" category and double click the starter bar.  This one is more animated and stylish.

on a final note, I'm pretty sure I've read many posts on here asking the same question, you might try searching the forums for further options/solutions.

---

### Post by Afteraffekt on 2007-01-02
I have Kiba Dock installed but i cant get compiz or xcompmgr to work

---

### Post by Afteraffekt on 2007-01-06
any tutorials on how to get these working? compiz, beryl or xgcompx?


In done the Kxdocker tutorial, but after a ways through compiling i get

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

i get this even when running my KDE session of Kubuntu, WTF?

iv tried 

./configure --disable-debug --prefix=$KDEDIR
./configure
./configure --prefix=/home/travis/Desktop/kxdocker-1.1.4a
and 
./configure --prefix=/usr

whats going on?


I AM running Ubuntu but have installed the Kubuntu-Desktop( sudo apt-get kubuntu-desktop)

---

### Post by Afteraffekt on 2007-01-06
i finally got that working...and kxdocker works, but how do i add to it?

---

### Post by Afteraffekt on 2007-01-07
Kxdocker doesnt seem to be working right, when I start it up by typing kxdocker this scrolls, then it launches:

```
Link points to "/tmp/ksocket-travis"
Link points to "/tmp/kde-travis"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
Error: KXDocker cannot find Composite Extensions
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources
kxdocker: WARNING: loading xml...
kxdocker: WARNING: saving xml configuration to backup configuration...
kxdocker: WARNING: loading plugins...
/opt/kde/share/apps/kxdocker/plugins/liblibKXDesignPanther.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDesignPanther.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXDesignPanther.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xMatrix)
/opt/kde/share/apps/kxdocker/plugins/liblibKXDockerFake.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXDockerFake.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXDockerFake.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDockerFake.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXDockerFake.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXDockerFake.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xGDocker)
Hello, KXDocker is going to use FAKE Transparency
/opt/kde/share/apps/kxdocker/plugins/liblibKXCommand.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXCommand.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXCommand.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXCommand.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXCommand.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXCommand.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xCommand)
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXARPManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXTaskManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMountManager.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXAnimator.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXAnimator.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXAnimator.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXAnimator.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xAnimator)
/opt/kde/share/apps/kxdocker/plugins/liblibKXMouse.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibKXMouse.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibKXMouse.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMouse.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibKXMouse.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibKXMouse.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: xeplugin_register(xMouse)
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/opt/kde/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/liblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
/usr/share/apps/kxdocker/plugins/libliblibXEPlugin_DCOP.so.so: cannot open shared object file: No such file or directory
kxdocker: WARNING: Plugins loaded:
kxdocker: WARNING: [0] xMatrix
kxdocker: WARNING: [1] xGDocker
kxdocker: WARNING: [2] xCommand
kxdocker: WARNING: [3] xAnimator
kxdocker: WARNING: [4] xMouse
kxdocker: WARNING: [5] xPillow
kxdocker: WARNING: Going to background...

```

Whats happening here?

---

### Post by blackmh on 2007-01-07
Kxdocker from repositories is broken. You'll have to compile it by yourself. I wrote how to so you might check it out.

---

### Post by Afteraffekt on 2007-01-07
this is downloaded from the site actually

---

### Post by ajmorris on 2007-01-12
kxdocker
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
KXDocker Will use Composite Extensions!
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kxdocker: WARNING: Cannot find updated resources: you may need to update or reinstall KXDocker resources, checkout [http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources](http://www.xiaprojects.com/www/prodotti/kxdocker/main.php?action=download#resources)
kxdocker: WARNING: loading xml...
kxdocker: WARNING: Warning user kxdocker_conf.xml may be corrupt: loading last backup!
kxdocker: WARNING: Warning user, and backup configurations are corrupt! I'm going to load system kxdocker_conf.xml !!!
kxdocker: WARNING: Warning user, backup, system configurations are corrupt! please install right kxdocker_conf.xml
DCOP aborting call from 'anonymous-17643' to 'kxdocker'
ERROR: Communication problem with kxdocker, it probably crashed.


This is what happens when i run kxdocker.

Also when i try to compile kxdocker from the source i get this : 

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Any ideas?

---

### Post by ajmorris on 2007-01-12
don't worry i am now running kool dock. It is quite good but has a few bugs.

---

### Post by Quillz on 2007-01-12
GDesklets has a simple dock that's quite stable.

---

### Post by ajmorris on 2007-01-12
is there a mac osx dock in the desklets? I found the gnome replacement bar but that is not quite what im looking for.

---

### Post by spockrock on 2007-01-12
gnome dock

---

### Post by ajmorris on 2007-01-12
> **spockrock said:**
> gnome dock

that's not a gdesklet though is it?

---

### Post by spockrock on 2007-01-13
nope it was macslows cairo dock, that now gnome-dock....

---

