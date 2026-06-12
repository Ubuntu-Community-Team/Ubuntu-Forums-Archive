---
title: "using xinput over ssh"
date: 2013-04-12
forum: General Help
---

### Post by manthony121 on 2013-04-12
I had to set up a wireless mouse on another computer for middle button emulation.  I eventually found the "xinput" command, which provides the necessary capability.  However, I discovered that if I connect to the target computer from my usual computer, using "ssh -Y <target>", when I type "xinput list", I get a listing for my local machine.  If I try "ssh <target>", I get a "Cannot connect to X server" error.  Is there any way to get information regarding the *remote* X server when using "xinput" over the network?

---

### Post by TheFu on 2013-04-12
The X-Server is running on your local machine.  The remote machine is an "X-Client."  Wikipedia explains nicely. [https://en.wikipedia.org/wiki/X_Window_System](https://en.wikipedia.org/wiki/X_Window_System)

If you want to see the X-Server actually running on a remote machine, you need to sit behind it, login, get a console, startx, and run the GUI there.

You might be able to trick a remote system into reporting on a remote X-server by changing the DISPLAY environment variable, iff the X-server has been started, but this technique often doesn't work as a normal user. Running it as root can have unexpected results and will change file permissions unless you are very careful that could break the remote X-server working under a normal account too. 

Have you tried ssh -X?  I doubt there will be any difference, since it reports based on the X-server. Just a thought.

---

### Post by steeldriver on 2013-04-12
Try giving it the DISPLAY value of the remote server e.g.

```
$ echo $DISPLAY
localhost:10.0
$ xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=10    [slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 IBM TrackPoint                       id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=9    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=12    [slave  keyboard (3)]
$ 
```

(which is the local X server info) but if I do

```
$ DISPLAY=:0 xinput
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Logitech Unifying Device. Wireless PID:4024    id=8    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Power Button                                id=7    [slave  keyboard (3)]
    &#8627; Eee PC WMI hotkeys                          id=9    [slave  keyboard (3)]
$ 
```

---

