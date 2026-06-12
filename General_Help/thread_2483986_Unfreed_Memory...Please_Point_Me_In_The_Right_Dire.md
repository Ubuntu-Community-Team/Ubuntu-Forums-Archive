---
title: "Unfreed Memory...Please Point Me In The Right Direction"
date: 2023-02-14
forum: General Help
---

### Post by wyattwhiteeagle on 2023-02-14
What is the best way to clean/clear unfreed memory?

I use Blender software.
With the age of my pc laptop, I'm needing to use it as a stand-alone executable.

In testing different versions of Blender, I now have an error message about unfreed memory...

```
Error: Not freed memory blocks: 14561, total unfreed memory 5.375668 MB
```

So, I tried running the Memory cleaner from within BleachBit, which returns it's own error message...

```
The function wipe_memory() with process ID 1040 is waiting for child process ID 1223.
The child memory-wiping process returned code 9.

```

---

### Post by TheFu on 2023-02-14
> **wyattwhiteeagle said:**
> What is the best way to clean/clear unfreed memory? 

In the code, use the free() C method.  Is this a trick question?  Expert programmers may also set the pointer holding the now-free'd memory back to NULL, to prevent other parts of their code from accessing memory that has been freed, but isn't necessarily zero'ed.  There are programming tools and techniques to catch memory leaks that have been around for decades.  Back when I was coding, we used "Purify" when running out code to find any memory leaks that good coding methods failed to handle.  Often, especially with GUI programs, the underlying display code had leaks that nobody could/would fix.  X/Windows is well known to have leaked memory, for example.  

When a program ends, the OS (any Unix-based OS) will free all the memory (stack and heap and DS/CS areas) automatically.  That includes any leaks that the program caused.  Since every Unix process has a specific amount of RAM pages that are connected to that process, the OS keeps track and knows which process owns which pages of RAM and virtual memory.

If a program doesn't completely die when closed or terminated, we call that a "zombie process" and perhaps some RAM is retained.  The only way to clean up zombie processes that I know is to reboot the OS.

For end-users, the only real answer to deal with memory leaks are to 
* close down processes
* Run processes that leak a bunch inside a sandbox, like firejail, and use the sandbox to limit how much RAM the process can see.  

I use firejail with Firefox, Thunderbird and other bloated programs.  Unfortunately, snap packages refuse to run under firejail because they use some of the same methods to provide constraints in the runtime environment.  So, if you want to control the constraints of a program that is delivered as a snap package, you'll need to swap out the snap package for the old-school debian packages from trusted sources.  The firejail manpages are pretty good.  My main system has 32GB of RAM, but that doesn't mean I want firefox to allocate 48GB (which I've seen).  To combat that accounting/reporting issue, I run firefox inside a jail with RAM limited. I started with 4GB and firefox crashed, raised it 2G at a time, until it didn't crash for at least 7 days of my typical use.  --rlimit-as=10200000000 is the current RAM limitation I'm using.  I did run with 8GB for many months.  

When it comes to dynamic memory allocations, the Linux kernel team decided that the performance hit was too large to bother checking that RAM is actually available, so all memory allocations appear to succeed until there's no more memory available.  When Unix systems run out of RAM and virtual memory, the OS will crash.  Anyway, when using top or glances or htop, you might see huge memory amounts under "VIRT" ... but really we need to be concerned with the numbers under the "RES" column more. For example:
```
CPU%  MEM%  VIRT   RES   PID USER        NI S     TIME+   R/s   W/s Command 
2.9   1.7 4.01G  539M 27953 tf           0 S   7:54.35     0     0 /usr/lib/firefox/firefox

```
the 4.01G isn't very important. It is the 539M that matters.  Well, there's more to it that the simple answer above. Interested people to research Linux memory management for themselves to get the real story.

---

### Post by wyattwhiteeagle on 2023-02-15
No, This isn't a trick question.
This is something I've never really dealt with in my *buntu experiences.


What is the standard for closing down processes within Unix/Linux/Ubuntu?


Is Firejail for use only on servers?


Which file and where within that file would I use the "--rlimit:" line?


Fortunately, I don't use any snap packages.

---

### Post by TheFu on 2023-02-15
> **TheFu said:**
>  
When a program ends, the OS (any Unix-based OS) will free all the memory (stack and heap and DS/CS areas) automatically.  That includes any leaks that the program caused.  

Perhaps you missed this.
If a program is closed, all the memory it used is freed.

If you want to know more about firejail, I'll stay out of it, and perhaps someone else will make the attempt.   My passed attempts to help have always failed.  [https://firejail.wordpress.com/](https://firejail.wordpress.com/) is the project page.  firejail is an advanced tool.  Only you can decide if that's something which fits into your use patterns.

---

### Post by Holger_Gehrke on 2023-02-15
The memory cleaner of bleachbit can't help you. It's purpose is to remove any content a process might have left behind in RAM by making itself the primary target for the OOM-Killer then simply allocating all memory and writing nonsense to it until it gets killed because the system is out of memory. It's meant to enhance privacy on a machine with multiple users.

The message from Blender looks like a debug message from a garbage collector or something like that to me. It's trying to free up memory but isn't able to free up as much as it calculated should be possible.

'firejail' was originally written to run firefox in a restricted environment, so no, it's not for use only on servers. And the '--rlimit-as' is an option for firejail, so you'd do something like 'firejail --rlimit-as=6G blender' to limit blender to not see more than 6GiB.

Holger

---

### Post by #&amp;thj^% on 2023-02-15
> **wyattwhiteeagle said:**
> No, This isn't a trick question.
This is something I've never really dealt with in my *buntu experiences.


What is the standard for closing down processes within Unix/Linux/Ubuntu?
For Blender when you need to close it use key combo <Ctrl+Q> that should help your memory leak,
This has been a very long outstanding Bug: [https://www.startpage.com/do/dsearch?query=Linux+blender+Error%3A+Not+freed+memory+blocks%3A+14561%2C+total+unfreed+memory+5.375668+MB&cat=web&pl=ext-ff&language=english&extVersion=1.3.0](https://www.startpage.com/do/dsearch?query=Linux+blender+Error%3A+Not+freed+memory+blocks%3A+14561%2C+total+unfreed+memory+5.375668+MB&cat=web&pl=ext-ff&language=english&extVersion=1.3.0)
I'm very surprised you've not hit it yet.
> **wyattwhiteeagle said:**
> 
Is Firejail for use only on servers?
Nope for all usage DE's Servers so on.
```
apt policy firejail
firejail:
  Installed: 0.9.72-2
  Candidate: 0.9.72-2
  Version table:
 *** 0.9.72-2 990
        990 http://deb.debian.org/debian testing/main amd64 Packages
        500 https://deb.kaisenlinux.org kaisen-rolling/main amd64 Packages
        100 /var/lib/dpkg/status
     0.9.72-2~bpo11+1 100
        100 http://deb.debian.org/debian bullseye-backports/main amd64 Packages


```

---

### Post by wyattwhiteeagle on 2023-02-15
> **TheFu said:**
> Perhaps you missed this.
If a program is closed, all the memory it used is freed.

If you want to know more about firejail, I'll stay out of it, and perhaps someone else will make the attempt.   My passed attempts to help have always failed.  [https://firejail.wordpress.com/](https://firejail.wordpress.com/) is the project page.  firejail is an advanced tool.  Only you can decide if that's something which fits into your use patterns.

Perhaps, the reason I missed that is what you say about end-users and "zombied" in that message.

I'm an end-user, and I recall seeing "zombied processes" in top and htop.

---

### Post by TheFu on 2023-02-15
> **wyattwhiteeagle said:**
> Perhaps, the reason I missed that is what you say about end-users and "zombied" in that message.

I'm an end-user, and I recall seeing "zombied processes" in top and htop.

Out of curiosity, I'll check all my systems for zombie processes now .... none of them have any zombie processes.  I can't remember the last time I saw one - perhaps 6 months ago. IDK.
[https://www.howtogeek.com/119815/htg-explains-what-is-a-zombie-process-on-linux/](https://www.howtogeek.com/119815/htg-explains-what-is-a-zombie-process-on-linux/)
That link says we can send a signal to the parent process to have it kill children.
```
$ kill -s SIGCHLD pid
```
It also says zombies don't use much RAM.

---

### Post by wyattwhiteeagle on 2023-02-15
> **TheFu said:**
> Out of curiosity, I'll check all my systems for zombie processes now .... none of them have any zombie processes.  I can't remember the last time I saw one - perhaps 6 months ago. IDK.
[https://www.howtogeek.com/119815/htg-explains-what-is-a-zombie-process-on-linux/](https://www.howtogeek.com/119815/htg-explains-what-is-a-zombie-process-on-linux/)
That link says we can send a signal to the parent process to have it kill children.
```
$ kill -s SIGCHLD pid
```
It also says zombies don't use much RAM.

One would think that the accumulation of zombied processes would add up the RAM usage totalling more than 1b, 1kb, 1mb etc.

Anyway, with all the awesome replies here, I'll take a break here and report back when I'm ready to take my next steps.

---

### Post by Impavidus on 2023-02-16
There's some nice information on closing processes in the manual:```
man -s3 exit
man -s2 _exit
man -s2 wait
```Most processes don't last more than a few milliseconds as a zombie, but they may if their parent got stuck somehow.

---

### Post by MAFoElffen on 2023-02-16
Using the same toolset to look for zombie processes:
```

top -b1 -n1 | grep Z

```
Should return null, except if a zombie process is left there. Haven't seen one "in years" on my hardware...

---

