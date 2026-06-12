---
title: "Rebooting kubuntu 14.04"
date: 2018-03-10
forum: General Help
---

### Post by anon_private on 2018-03-10
Hello,

I tend to keep my pc on all the time (suspended over night), except when upgrades need a reboot.

Should I make a habit of occasionally rebooting? I am thinking of the possible need to clear caches and memory.

Let me know what you think

Regards

---

### Post by TheFu on 2018-03-10
No. I never reboot unless there is a libc or kernel update.  And I only patch during maintenance windows. If you don't go crazy with loading all sorts of funky GUI programs, systems will stay up indefinitely.  Rebooted most of my machines last weekend, but one of them has been up 24 days.  In the old days, before all the security patching, having uptimes of 120 days was common.

As for memory - whenever a process finishes, the memory for it is returned to the OS to be used.  Any process can be restarted, though it really isn't necessary anymore.  Updates will restart a process as part of the update process, so all new versions of that process are running the new code. This doesn't usually happen for GUIs, though updating something like firefox will likely cause problems since the underlying files will have changed. Manually restarting the GUI programs ... or just logout and log back in will solve it for end-user GUI programs too.  System daemons are handled already.

Cache and buffer management is also handled automatically.  You can see the disk buffers with **free -hm**.  However, some programs might have their own cache management. Things that pull data from the internet are likely to keep 500M somewhere. New stuff should remove the older things.  There are Ubuntu cleanup tools for these things if you want more control.  I don't bother, since disk space is pretty cheap for a longtime. I simply avoid backing up the cache files.

---

### Post by Melano Chole on 2018-03-10
> **TheFu said:**
> As for memory - whenever a process finishes, the memory for it is returned to the OS to be used.  Any process can be restarted, though it really isn't necessary anymore. 
TheFu, what if some buggy software causes memory leaks? Is it possible to hand over the stolen memory to the OS without a reboot?

---

### Post by TheFu on 2018-03-10
Each process has assigned memory. The OS keeps up with it.  When the process ends, the memory is returned to the OS.  No exceptions.

There is no such thing as a memory leak by a program that escapes cleanup when the process is ended. Linux isn't MS-DOS.  Every OS since OS/2/WinNT that was pre-emptively multi-tasked running on  x86 systems worked this way.  Unix has ALWAYS worked this way.

If the process keeps running and keeps allocating memory, without freeing all of it, then it will be retained. Killing a process will free all memory allocated by that process.  PERIOD.  There isn't much more to it, but we can talk DS, CS, heap and stack if you are able.  I'm an old C/C++ developer.

---

### Post by Melano Chole on 2018-03-10
Thank you, TheFu. I just heard something of the memory leaks and thought rebooting is the way to get the leaked memory back. Not a developer, just a user )

---

### Post by TheFu on 2018-03-10
Memory leaks are terrible bugs within a program. They are caused when the programmer (or a library programmer) looses track of a pointer to allocated memory.  Many languages make this almost impossible to happen because the object that is allocated keeps a "reference count" - when the reference count drops to 0(zero), it deletes/frees the memory for itself. This is called a destructor.  GUI libraries have a long history of having memory leaks due to the complexity of their code and the need to have multiple different parts of the library to have access to the memory.  X/Windows and the Windows GUI libraries are known to leak memory, though the size of their leaks have been reduced over the decades and the amount of RAM in our computers has grown exponentially so as to make those 4k leaks every month negligible.

There are tools which have been around since the early 1990s which can trace and pinpoint memory leaks in running processes. A professional programmer will consider all memory leaks an embarrassment to their team and strive NEVER to have any in their code.  I've seen this.  

Other places with less professional devs just don't care.  They are too busy trying to get things working to worry about leaks and the security problems that a lost pointer can cause inside a process.  Memory leaks are per-process, not per-thread, BTW.

---

