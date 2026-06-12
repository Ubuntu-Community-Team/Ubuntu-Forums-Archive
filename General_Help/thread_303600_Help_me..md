---
title: "Help me."
date: 2006-11-20
forum: General Help
---

### Post by Draknats on 2006-11-20
I was using Mirrordir to sync my Documents folder with a partition on a separate disk.  It seems that I accidentally "inverted" the direction I wanted the data to sync,

mirrordir -v /media/sda3/Backup /home/draknats/Documents/

, so suddenly my terminal started flooding with lines that read "removing...".  I reflexively exited the Terminal, as quickly as I could.  I'm pretty sure that data has been lost, but I cannot properly survey the damage.  I'm far too distressed to do that.  It'd be wonderful if there were some way to "undo" this, but I would at least be able to rest in peace if I could find a log of the output from the terminal.  I'm looking around in /var/log, but can't find anytthing.  ANy ideas?  At the very least, if I want to be able to pick myself back up in life again, I need to know exactly what data I've lost.  Please help me.

This is the shittiest I've felt in a long time.  Like, it blows blows both romantic and existential qualms out of the water.

---

### Post by strabes on 2006-11-20
sorry about your mix up. it always goes <command> <source> <destination>. I like the window$ drag and drop method for backing up stuff cuz then there's no way you can mess it up like that =\ sorry.

---

### Post by Draknats on 2006-11-20
Yeah, I can still hardly believe how foolish I was.

Any idea of finding a system log of the terminal output?  I need to know the extent of the damage before I can make amends with my mistake.

---

### Post by koenn on 2006-11-20
you may try to undelete the files that were removed during the sync.
I've found some links in google that look promising ; I've posted them in other thread of yet an other poor soul with lost files.
[http://www.ubuntuforums.org/showthread.php?t=303187](http://www.ubuntuforums.org/showthread.php?t=303187)

As for the output/log of your terminal, I have no idea, and i couldn't find any info, except that for xterm (another terminal) "Normally logging is not supported, due to security concerns. Some versions of xterm may have logging enabled. The logfile is written to the directory from which xterm is invoked. The filename is generated, of the form XtermLog.XXXXXX"
If you used the standard ubuntu terminal, you used gnome-terminal. Its man page does not mention any logging, so I'm afraid tyou're out of luck there. 


I'd try and see if the undelete tools bring up anything, if no recovery, then maybe at least a list names of deleted files, so you know the extend of the damage.

---

