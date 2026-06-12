---
title: "Limit CPU usage of process"
date: 2006-08-15
forum: General Help
---

### Post by Lunar_Lamp on 2006-08-15
I wrote a script to convert a few thousand music files from one file to another, and have started it going and don't want to stop it now really.  However, after leaving it running for a while I realise that I forgot to start it with the 'nice' command, to make it have a low priority on CPU usage.  Is there a way to lower a processes priority once it has started?

The script uses lots of sequential ffmpeg instances, and each one has a different PID, so I suspect this may not be possible.  Also, would the 'nice' command have done what I wanted it to do seeing as the script itself doesn't do much, other that tell ffmpeg which files to convert.  That is, it's ffmpeg that is using the resources.  Or does 'nice' make all the children of a script have the same priority as the parent process?

---

### Post by David Corrales on 2006-08-15
You can use the command **renice** to dinamically assign a new nice value to a running process.
You can define process groups to alter a whole bunch of processes at the same time. Check the docs typing **man renice** :)

---

### Post by brundles on 2006-08-15
I think (but don't quote me!) that if you assign a nice value to a process any child processes from that are given the same nice value. i.e. If you renice the original script process then everytime that starts off the next ffmpeg instance that should have the same nice value.

---

### Post by Lunar_Lamp on 2006-08-15
Thanks a lot! :D

---

### Post by metroplex on 2007-10-02
I'd suggest using the utility 'cpulimit'.

sudo apt-get install cpulimit
man cpulimit

---

