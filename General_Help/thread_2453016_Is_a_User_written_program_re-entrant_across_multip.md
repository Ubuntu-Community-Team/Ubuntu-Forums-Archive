---
title: "Is a User written program re-entrant across multiple users in linux"
date: 2020-11-01
forum: General Help
---

### Post by Ralph L on 2020-11-01
I am just trying to understand linux a little better and could use a little help.  If I create a program in C, save it in MY user mass storage, give permission to another user of my computer (my wife) to execute the program, how many copies of the program code will end up in memory, when we are both logged in.  (We each log out of the computer using ctrl-alt-del leaving the programs for each of us still active.)
If I look at System Monitor I see that, for example, that 2 processes for Firefox are listed--one for me and one for my wife.  However, I understand that only 1 copy of Firefox code exists in memory (its re-entrant across users), but with two sets of "data"--one for me and one for my wife.  My question is "Will an application that I write, and permit to my wife, be re-entrant across users, having one copy of code in memory for the two of us (like Firefox), or be non re-entrant across users with two copies in memory (one for each of us)".

Thanks for any help..........

---

### Post by spjackson on 2020-11-01
There would be only one copy of the code segment in memory. However, I'm not sure what you mean by reentrant. What I understand by that is: [https://en.wikipedia.org/wiki/Reentrancy_(computing)](https://en.wikipedia.org/wiki/Reentrancy_(computing))
> 
In computing, a computer program or subroutine is called reentrant if multiple invocations can safely run concurrently on a single processor system, where a reentrant procedure can be interrupted in the middle of its execution and then safely be called again ("re-entered") before its previous invocations complete execution.

Whether your code is reentrant by that definition depends essentially on what (writable) resources they might share, e.g. whether they write to the same file.

---

### Post by TheFu on 2020-11-01
Code Segment, Data Segment, heap.
Code segments can be shared, data segments and heap are not.  Basic POSIX stuff ... er ... except in Windows where some DS can be shared based on other settings. In Windows, IPC can be performed using a shared DS.

Reentrant code means something different.

---

### Post by Ralph L on 2020-11-01
I guess I am using the term re-entrant incorrectly.  My real computing experience was in the 60's pre Unix (i'm old), and pre virtual memory.  If my program's code segment is shared with my wife, will it execute in memory assigned to me, memory assigned to my wife, or some other memory.  Or is memory in linux systems not assigned to individual users, but in some other manner.

Thanks for the input......

---

### Post by TheFu on 2020-11-01
There isn't just 1 sort of memory.

Code segments are system-wide for code loaded from the same inode.  But the programmer can override this using compiler settings, to the 100% accurate answer is "it depends."  But the almost always answer is CS are shared system-wide.  Self-modifying code isn't generally allowed on Unix systems.  Code segments are marked as read-only just after they are loaded.  Of course, if you make a copy of the program (new inode) and run it, the there will be 2 separate files seen by the system and 2 copies of the CS in RAM. There isn't any automatic deduplication for RAM CS loads.  

Shared libraries work the same way. There is 1 CS, marked as read-only based on the file inode at load time.  This is why Unix systems can have 1, 5, 100, 1000 users on the same systems without having to use 1000x more RAM. If everyone is running all the same programs, there's only 1 copy of the code in RAM, shared by everyone running that same program ... er ... until the last person closes the program down.

An Advanced Unix Programming book would probably explain this better.  Look for the Rochkind book. There are probably older copies at used books stores for $1.50.

I programmed on TSO/ISPF for years and IBM-360 DOS just a little, not the PC-DOS or MS-DOS or DR-DOS that we all used too, but they were all legacy systems by the time I touched them.

---

### Post by Ralph L on 2020-11-02
Thank you very much for the informative writeups.  It helps me understand modern systems.  I was a Control Data 6600 operating systems programmer in the 60s, when they were considered the "big iron" for number crunching.  Those systems did not have virtual memory (too slow) nor hardware support for re-entrant coding, but did do time sharing with some mullti-computer systems supporting more than a hundred simultaneous users.  Only a few programs such as time sharing editors and compilers were made (what we called) "multi-user re-entrant".  All remaining programs were "one copy for each user".  

Thanks again for the info and I will look into the literature you recommend.

Ralph

---

### Post by TheFu on 2020-11-02
At University, I used a CDC 750/170 (whatever that means) for FORTRAN coding. Only knew enough to edit code, compile, link and save a few assignments. Storage was tight, always. Admins would clean out old object and program files as they liked, but would try to avoid deleting source code. We were supposed to keep copies on our own media, which is hard when using vt100 terminals. It isn't like they had floppies.

---

### Post by The Cog on 2020-11-02
As I understand it, there would be one copy of the code in memory, but two processes executing that code. One process running with your ID, and one with your wife's ID. Each process would have its own data in memory, but they would share the read-only code image.

---

