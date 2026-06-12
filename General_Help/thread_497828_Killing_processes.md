---
title: "Killing processes"
date: 2007-07-10
forum: General Help
---

### Post by Skerit on 2007-07-10
The way I learned it, killing a process with signal 9 is "the computer death ray of all death rays" for programs, but lately some programs have started failing, albeit in Gutsy (which is completely normal), I still can't kill them! And that's **not** normal, is it? I thought nothing could escape "kill 9 nnnn"? 

Seems kind of silly to completely reset the computer for a media player gone bad ..

---

### Post by ryantmer on 2007-07-10
Are you remembering the dash before the 9?

```
kill -9 pid
```

---

### Post by Skerit on 2007-07-11
Well, euhm, no ... Though, adding it didn't really help either, programs that are truly stuck won't close, like banshee and some vmware subprogram, vmware-vmx ...

---

### Post by Mr. C. on 2007-07-11
Any process still in I/O wait cannot be killed until the I/O request returns.

The kill command simply posts a signal; the process must be runnable to accept the signal, and handle it.

Poorly written programs, or some device drivers, may not work correctly, but this is typically very rare in Unix/Linux.

You can look at the STAT column in either **ps** or **top** and see what status the process is in.  Also note that you have to be the process owner to kill it.

Finally, a process becomes a zombie (Z STAT), when its parent hasn't yet cleaned up after it.  It is no longer running, its memory is free, is generally not of concern.

MrC

---

### Post by rillip on 2007-07-11
As Mr. C stated, you have to be the owner to kill it.  Try

```
sudo kill -9 nnn
```

This should let you kill anything that it is possible to kill, but as Mr. C. said, if it's not able to be sent a signal, it won't die.  Additionally, if it's very poorly written, it could be that it's simply not running.  Yes, it may show up as running, but it may have been preempted for something else, and is too "nice" to take back the CPU.  Doubtful, but possible.

---

### Post by Espreon on 2007-07-11
Dude, are you using Gutsy as your main OS? Wait until the Beta is released before using Gutsy for your main. If ya wanna still test Gutsy, use it under a VM or dual-boot.

---

