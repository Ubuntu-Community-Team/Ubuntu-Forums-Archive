---
title: "Linux equivalent of Windows Process Explorer"
date: 2008-05-28
forum: General Help
---

### Post by inselaffe on 2008-05-28
There is a very useful utility for Windows, [Process Monitor]("http://technet.microsoft.com/en-us/sysinternals/bb896645.aspx"), which logs all file and registry activity. This logs, for example, all attempts to read or write a file by each process, whether it is a success or failure. This can be extremely useful for troubleshooting.

Is there a comparable utility for Linux?

---

### Post by NikoC on 2008-05-28
Hmmz maybe when you are in a terminal you can type:
top

Or

ps 

For a list of options type:
man top
Or
man ps

I'm not sure if these give you all the info you need...

---

### Post by bingoUV on 2008-05-28
install htop from the repositories. In the terminal, type htop. Now, press s to trace a given process, giving all the system calls it makes (of course, this includes the attempts to write files)

Press F1 to explore its other features.

EDIT : If you only want to trace a process' system calls, use just strace. It is already installed. 
```

strace -p <pid>

```

Above command will trace system calls of process with pid <pid>.

---

### Post by Scruffynerf on 2008-05-28
System >> Administration >> System Monitor (GUI method)

---

### Post by bobpaul on 2008-12-21
It's my understanding that there is no decent equivalent to process explorer for unix systems. Here are some examples of things I can do with Systernals Process explorer that I can't do with top, htop, gnome-system-monitor, etc. If someone knows the unix way to do the same, please inform. I'm not afraid of the terminal.

Flash plugin is taking up 100% CPU.
  ex: In Linux: top, htop, etc show firefox as 100% cpu. Thanks/not helpful. (Note that if you're using nsplugin wrapper for flash32 on a 64bit system, it will show that instead, which you can kill independently.)
  ex: Windows with Process Explorer: Shows firefox is taking up 100% cpu. Right click on firefox.exe on the list, choose properties. Go to the threads tab. See that firefox has spawned a thread using libflash.dll and that is taking up 100% cpu. Note the thread ID for further inspection with process monitor (another systinternals app) or kill the thread without killing firefox.

Windows specific:
  recently a vista machine I was working on had a problem where explorer.exe would take up 100% cpu right after login. Explorer.exe is like gnome's nautilus application, so it handles the desktop, start menu, file browser, etc. Using process explorer I found the specific library (dll) that explorer had launched into a thread and did further research on google until I found a fix.

Linux specific:
  often X takes up very high CPU, causing my laptop to run at full speed (1.8ghz) rather than low speed (800mhz). This makes my laptop hot, consumes battery, and makes the fan spin rather loudly. Using gnome-system-monitor, htop, top, etc I can find out that X is consuming high CPU. I know nothing else about the problem. This is ridiculously unhelpful. What do I do, kill X? There must be some debugging tools I can use for more info, but I don't know them. I tried "sudo strace -p [X's PId]" and some info was dumped to the terminal before the system hard locked, so hard that even Alt+SysReq failed to function, and I had to pull the power.

---

### Post by scorp123 on 2008-12-21
> **bobpaul said:**
> It's my understanding that there is no decent equivalent to process explorer for unix systems.  Good joke :lolflag:

What do you think where they got their ideas from? LOL.

> **bobpaul said:**
>   Flash plugin is taking up 100% CPU.
  ex: In Linux: top, htop, etc show firefox as 100% cpu. In **"htop"**:
[LIST]
[*]press F2 and go into the setup
[*]in the left-most column, go to "Display Options" and hit the 'Enter' key
[*]My setup looks like this:[/LIST]
[X] Tree view
[ ] Shadow other user's processes
[ ] Hide kernel threads
[ ] Hide userland threads
[X] Display threads in a different color
[X] Highlight program basename
[X] Highlight megabytes in memory counters
[X] Leave a margin around header
[ ] Detailed CPU time

Result ... you see the threads now, and they're even highlighted so you get to see the difference between them and their main program that spawned them.

The command line method for killing flash, e.g. ```
lsof | grep flash
```
The result would be something like this:
```
firefox    **7890**        sysadm  mem       REG        8,6 10022452   10461470 /usr/lib/flashplugin-nonfree/libflashplayer.so
```

See the number I highlighted? That's the PID of the process that opened the flash library. So depending on the signals you send to the process you can kill it, renice it, or whatever pleases you.

Chances are that you're still killing all firefox instances. And that's perfectly normal here. If a thread goes so wrong that admin has to kill it manually then often enough the parent processes will kill themselves too. I might be wrong though, so you'd have to play with the kill signals.

BTW, killing all firefox instances is no issue if you set firefox to remember the last pages it had open. In case it crashes you simply reopen it again and you will be back right where you were. I just tested that. Firefox even came back with my posting here that I had not sent yet.

> **bobpaul said:**
>  Note the thread ID for further inspection  On UNIX-like OS such as Linux everything is a "process", so threads too get PID's = process ID's just like ordinary processes. And you'd therefore also use the same commands against misbehaving threads (kill, pkill, killall, and so on) as you would against misbehaving processes.

> **bobpaul said:**
>  kill the thread without killing firefox.  ... Which creates large memory leaks and potentially "funny behaviour" :D  No thanks to that. If a thread has to be killed then he main process that spawned it has no business of remaining either, so it should die as well so the RAM that was occupied can be reclaimed by the system.

> **bobpaul said:**
>  often X takes up very high CPU  Did you enable desktop effects? That will make a laptop go hot. Especially on laptops with ATI chips it seems (a coworker just had this problem last week). My own laptops run on Intel GMA9xx chips and they too get quite warm when desktop effects are enabled. So turning those effects off might help.

> **bobpaul said:**
>  This is ridiculously unhelpful. Talking of which: For starters, you could tell us your laptop model? And maybe give us the details, e.g. what graphics chip it has, and so on? Maybe your laptop is one of those models which has known issues (e.g. some laptops have a weird BIOS and their ACPI implementation is not 100% according to the standards, so the laptop might act strange, get very hot, and so on).


> **bobpaul said:**
>  There must be some debugging tools I can use for more info, but I don't know them.  You maybe are a Windows guru. But that knowledge does not necessarily translate into the Linux world. Linux is not Windows. Never wants to be. Never was. Never will be.

May I ask why you are using Linux? It seems obvious that Linux is not what you really want ...

---

### Post by bobpaul on 2008-12-22
> **scorp123 said:**
> 
Good joke


Not a joke. If you Google "process explorer linux" you'll see many pages of threads where people just say, "gnome-system-monitor", "top", "htop" and nothing further. Generally the OP says, "none of those appear to do what I want :(" and nobody provides a better answer. You might be the first. It's much appreciated.

> **scorp123 said:**
> 
Result ... you see the threads now, and they're even highlighted so you get to see the difference between them and their main program that spawned them.


I'll have to play with this some more, but this looks very promising. Thanks.

> **scorp123 said:**
> 
See the number I highlighted? That's the PID of the process that opened the flash library. So depending on the signals you send to the process you can kill it, renice it, or whatever pleases you.


Looks useful. This PID should refer to the thread that spawned flash then, eh, and not the main parent thread? One problem here is that you assume I *know* that flash is the problem. I don't. But with your htop settings, I would actually know the PID that's behaving badly and need the lsof output to find the files it's owning and determine which plugin it is. That's really not too much of a problem, since I'll probably just want to kill the thread anyway, but it's worth noting.

> **scorp123 said:**
> 
Chances are that you're still killing all firefox instances.


I'm not sure I'd assume that. I've frequently killed the nsplugin process on 64 bit systems where flash had run a muck and all the flash applets that were displayed disappeared, but the pages that contained them remained rendered and viewable even. (Granted, that was an nspluginwrapper process and not the firefox process that executed it, but I should think the process owning libflash would be a process very much like nspluginwrapper in how it interacts with the rest of FX.)

> **scorp123 said:**
> 
BTW, killing all firefox instances is no issue if you set firefox to remember the last pages it had open.

This is true for firefox, yet still not fully desirable. If it was a "bad" flashapplet that caused flash to run-a-muck, re-opening firefox would just cause that page to load and lock things up again. This isn't normally the case, but anything to prevent editing sessionstore.js by hand is always nice to have around. If I can kill the single thread without bringing down all of firefox, I can close that tab before reloading a saved session without that page. Also, it's nice to have a technique that can apply to other processes besides firefox; not everything saves it's state automagically. 

> **scorp123 said:**
> 
 ... Which creates large memory leaks and potentially "funny behaviour" :D  

Nobody said leave it as a permanent solution. Killing that thread might be worth the lost memory and funny behavior for the few minutes you need to clean up before restarting the parent process. Or would killing the parent process later still not allow the system to reclaim the memory? If that's the case, than maybe not...

> **scorp123 said:**
> 
 Did you enable desktop effects? That will make a laptop go hot. Especially on laptops with ATI chips it seems (a coworker just had this problem last week).

No, I have that disabled, but this is a topic for another thread. I don't want to hijack this to discuss some possible bug in X, my graphics drivers, or other stuff unrelated to troubleshooting stuck and poorly behaving processes. IF it can be used as an example, then I may bring it back up again. I'll wait until it happens again and see what I can find out.

> **scorp123 said:**
> 
 You maybe are a Windows guru. That's somewhat correct, but years of disuse has left me with fewer and fewer tricks up my sleeve. I still find my way around, though, yes.

> **scorp123 said:**
> May I ask why you are using Linux? It seems obvious that Linux is not what you really want ...

Ouch. There's no need to get vulgar! :lolflag: Point out one thing that windows does well (and even then only with third-party tools) and suddenly people start taking away your GNU license. :( Thanks for the help. I'll give that some practice and come back if I need more assistance.

**Edit:** I saw [this on reddit today](http://bash.org/?152037). It appears very applicable to our conversation =D

---

### Post by Alvinius on 2008-12-22
:popcorn:

---

### Post by bobpaul on 2008-12-22
> **Alvinius said:**
> OK so you are a troll, readers please ignore....

What? I think you missed something or read too much into that bash.org post I included in my edit. This is the first time this has been acceptably answered, as near as I can tell.

---

### Post by scorp123 on 2008-12-22
> **bobpaul said:**
>  You might be the first. It's much appreciated.  Thanks :)

> **bobpaul said:**
>  Or would killing the parent process later still not allow the system to reclaim the memory?  Uhhhmmm ... hard to tell. You know - "zombie" processes are not unheard of here. Depending on how things got killed they will creep around as zombies in your system's memory. Just if anyone cares to read more about "zombie processes":
[http://ubuntuforums.org/showpost.php?p=6198154&postcount=4](http://ubuntuforums.org/showpost.php?p=6198154&postcount=4)

> **bobpaul said:**
>   Point out one thing that windows does well ...  Windows doing things "well"??? :D  Now you're being vulgar ... sort of. You're hurting my religious Linux zealot feelings ... or something like that ... ;)  (uhhhhm, can I make up a better reason and then come back, yes? :)  ...)

---

### Post by dacne on 2009-08-14
Hi, I come to these forums via search engine. I'm resurecting this thread to ask bobpaul for an update. This thread was the second result for my search query.

Were you able to find any software with similar functionality (process trouble shooting) to Process Explorer?

Where you able to figure out a work flow via command line?

Can anybody recommend a book that covers in detail how to troubleshoot hung or 100% cpu processes using command line tools like htop, strace, lsof and others?

---

### Post by serpantman on 2009-08-14
press alt-f2

then run 
gnome-system-monitor
:) enjoy

---

### Post by AmerNewbieInDE on 2009-08-14
> **scorp123 said:**
> Thanks :)

 Uhhhmmm ... hard to tell. You know - "zombie" processes are not unheard of here. Depending on how things got killed they will creep around as zombies in your system's memory. Just if anyone cares to read more about "zombie processes":
[http://ubuntuforums.org/showpost.php?p=6198154&postcount=4](http://ubuntuforums.org/showpost.php?p=6198154&postcount=4)

 Windows doing things "well"??? :D  Now you're being vulgar ... sort of. You're hurting my religious Linux zealot feelings ... or something like that ... ;)  (uhhhhm, can I make up a better reason and then come back, yes? :)  ...)

OMG.. look at the original post date...how many pages did you look through.. :)

---

### Post by serpantman on 2009-08-14
Zombie thread rises from the dead!!!

---

### Post by AmerNewbieInDE on 2009-08-14
lol.. OMG, sorry, didnt even look at origal post date..

---

### Post by mazz0 on 2009-08-15
Well, I'm glad this thread was recently resurrected, otherwise I was about to resurect it myself.

Has their been any change on the GUI front?  I /am/ afraid of the terminal, I want a nice visual, powerful programme like Process Explorer.  I know there's System Monitor, but that's equivalent to Task Manager in Windows, Process Explorer is much more powerful - it's like a GUI for all the command line tools people have spoken of in this thread, which is what I'd like.

---

### Post by charonn0 on 2010-07-09
Well, to re-resurrect this previously resurrected thread, I found this: 

[http://sourceforge.net/projects/procexp/](http://sourceforge.net/projects/procexp/)

It's not quite there yet, but the project's stated goal is to "mimic Windows process explorer from sysinternals, and aims to be more usable than top and ps."

They offer source tarballs or RPM packages. To run it from the tarball just extract and execute the procexp.sh script.

---

### Post by bullium on 2010-12-09
> **bingoUV said:**
> install htop from the repositories. In the terminal, type htop. Now, press s to trace a given process, giving all the system calls it makes (of course, this includes the attempts to write files)

Press F1 to explore its other features.



Thanks for the information on htop. I've been using it for years and I had never stumbled upon the trace function; you learn something new every day. Also, thanks for the strace command, I'll ad that to my notes for troubleshooting.

---

