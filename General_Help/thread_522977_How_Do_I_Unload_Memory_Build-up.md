---
title: "How Do I Unload Memory Build-up?"
date: 2007-08-11
forum: General Help
---

### Post by Gotou on 2007-08-11
Hullo!

I running Fluxbox 9.15 on Dapper Drake.

I've recently loaded wmmemload to observe how my system is using the memory.

When first boot up the computer the memory load is at 28%.

I fired up Thunar and the memory load shot up to 43%.

As I was working with my computer the memory load steadily increased.

Finally, when I was all done I shutdown all the programs I was using but the memory load was still high.

I restarted Fluxbox and the memory load dropped to 46%.

The only way I could get the memory load back down to 28% was to reboot my computer.

Is there a command or program that will flush out the memory build up?


Update:

Kept a closer eye on the wmmemload display and the memory load dropped to 15% while I was deleting some old junk through Thunar.

What's going on with the memory usage?

---

### Post by lloyd_b on 2007-08-11
Note: I'm completely unfamiliar with wmmemload, so ignore me if I'm entirely off base.

Does wmmemload just display total memory used, or does it separate it into categories (used, buffers, cache)?  The situation you've described could be a result of the system using substantial amounts of memory for buffers/cache (and then freeing it when you did that clean-up via Thunar).

Rather than just rely on wmmemload, try opening a terminal window, and running the "free" command.  This command does separate memory usage into it's different categories, so you can see if the memory is being used for buffers/cache.

And if that is the case, don't worry about it.  Linux will automatically cache just about everything (since this will improve performance), but if you run a program that actually requires more memory,a chunk of that cache will automatically be freed. 

Lloyd B.

---

### Post by tgalati4 on 2007-08-11
Memory usage will end up around 90% over the long term.  This is how Linux works.  It keeps old pages in memory because you might need them in the future.  There is active and inactive pages.  Inactive pages are flushed when more memory is needed (as when a new application is loaded).  You need more ram (512 MB to 1 GB) when your swap file starts to fill up and your machine slows to a crawl.  This is normal behavior.

Rebooting will flush the memory.  Logging out and logging in will sometimes clear the memory.  Normally you don't need to worry about it because Linux is quite capable of managing memory.

---

### Post by ddrichardson on 2007-08-11
tgalati4 is absolutely right - the UNIX philosophy has always been that unused RAM is wasted RAM.

---

### Post by kerry_s on 2007-08-11
unused memory is wasted memory.

---

### Post by oldos2er on 2007-08-11
>What's going on with the memory usage?

 How much physical RAM do you have? Like others have said, it sounds to me like Linux is doing what it's supposed to; using your memory to its fullest. There are some helpful links to be found if you google "linux memory usage."

---

