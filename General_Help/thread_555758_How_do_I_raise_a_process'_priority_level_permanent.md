---
title: "How do I raise a process' priority level permanently?"
date: 2007-09-20
forum: General Help
---

### Post by orangey on 2007-09-20
Hi,
I'm experiencing laggy multimedia playback when I watch rmvb files.  Its likely my pc is fairly slow (P3-700Mhz w/ 768MB or ram + Nvidia Ti4400).  I want to increase the priority of realplayer just slightly and see if that helps.  I know you can do that with the nice command.  But is there a way to do that permanently so that I (my dad), doesn't have to sudo it?  Ty.

---

### Post by kidders on 2007-09-21
Hi there,

> **orangey said:**
> is there a way to do that permanently so that I (my dad), doesn't have to sudo it?Yes and no. Unprivileged users can't manipulate process priority (obviously), so you *have* to involve sudo, but I suppose you could replace realplayer's binary with a shell script, to make life a bit easier. Maybe something like this would work...
[LIST=1]
[*]Rename realplayer's binary & create an empty file called "realplayer" in its place. Alternatively, you could leave realplayer the way it is, call the empty file something different, and get into the habit of launching realplayer using the new name instead.
[*]Make sure the empty file is "chown root:" and "chmod 755".
[*]Put something along the lines of the following into the empty file...[/LIST]```
#!/bin/bash
/path/to/*REAL*/realplayer &
sudo renice -n -5 $!
```

Something like that *should* do the trick. You'd get a slight process priority bump. Be cautious about making the niceness too big (small?!) though...
[LIST]
[*]If realplayer were to misbehave while its priority were too elevated, it could cripple your system.
[*]Prioritising realplayer too far above the processes that handle I/O or window management, for example, would *degrade* performance, rather than improving it.[/LIST]Now, sudo (or perhaps kdesu or gksudo, depending on what you choose) will be invoked automatically every time you launch realplayer. If you really wanted to, you could run "visudo" and configure your box to allow sudo to be used passwordlessly for the specific command used in the shell script, but I strongly advise against doing so without reading about /etc/sudoers, and the risks involved in loosening the restrictions on the acquisition of root privileges. Whatever you do though, it's important to _absolutely never_ run realplayer as root (ie using sudo). It would be totally insane.

I hope that helps.

---

