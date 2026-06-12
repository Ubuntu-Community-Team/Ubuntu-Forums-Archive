---
title: "Deluge does not start after rebooting (Xubuntu 13.04)"
date: 2013-10-11
forum: General Help
---

### Post by gianfranco2 on 2013-10-11
After installing and running Conky Manager, I had to force-reboot using the *sudo reboot* command while Deluge was still running because the panel had disappeared making the DE almost unusable; however, after rebooting I could no longer start the application. I ran Deluge via terminal, and the message I got was something about the program not being able to acquire a lock; I deleted the two files in the */home/.config/deluge/ipc *directory (just as somebody else suggested), and the program worked until I rebooted. Now I can no longer launch the program either using the shortcut I have assigned to it or the panel launcher...neither have I been able to launch it using the applications menu; launching it from the terminal, gives the following message:
Traceback (most recent call last):
```
  File "/usr/bin/deluge", line 9, in <module>
    load_entry_point('deluge==1.3.6', 'gui_scripts', 'deluge')()
  File "/usr/lib/python2.7/dist-packages/deluge/main.py", line 132, in start_ui
    UI(options, args, options.args)
  File "/usr/lib/python2.7/dist-packages/deluge/ui/ui.py", line 150, in __init__
    ui = GtkUI(args)
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/gtkui.py", line 225, in __init__
    self.ipcinterface = IPCInterface(args)
  File "/usr/lib/python2.7/dist-packages/deluge/ui/gtkui/ipcinterface.py", line 142, in __init__
    reactor.listenUNIX(socket, self.factory, wantPID=True)
  File "/usr/lib/python2.7/dist-packages/twisted/internet/posixbase.py", line 413, in listenUNIX
    p.startListening()
  File "/usr/lib/python2.7/dist-packages/twisted/internet/unix.py", line 273, in startListening
    if not self.lockFile.lock():
  File "/usr/lib/python2.7/dist-packages/twisted/python/lockfile.py", line 127, in lock
    symlink(str(os.getpid()), self.name)
OSError: [Errno 13] Permission denied

```
However, when I use *sudo deluge* to launch the application, it does work and start as it normally would.
It also refuses to add a torrent when I double-click on the torrent file or use the context (right click) menu to select the application, even if it's already running.
Is there a way to solve this problem, preferably without having to reinstall the program or use the terminal every time? Because now I have a totally useless panel launcher and cannot launch it from the menu or using the keyboard shortcut.
**Update:** Now, even using the *sudo deluge* command does not work, and I can no longer delete the ipc folder for some reason (Error: permission denied). Here is what I get when I type in the command:
```
  [ERROR   ] 21:34:05 ipcinterface:156 Deluge restart failed: Couldn't listen on any:/home/arcturus/.config/deluge/ipc/deluge-gtk: Cannot acquire lock.  
```

---

