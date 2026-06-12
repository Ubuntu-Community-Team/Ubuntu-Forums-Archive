---
title: "Unknown issue keeps eating up drive space until there's no space left"
date: 2016-12-02
forum: General Help
---

### Post by elvis6 on 2016-12-02
This is the 2nd time this has happened. The first time, my Ubuntu basically shut down completely due to full disc space. Eventually I was able to get it running, and checked disc space and it was almost 100% full. So I started deleting large files until eventually I had a full Gig left.

I have carefully kept a watch on the disc space, and everything stayed normal for a full weeks, then suddenly I started having strange performance issues. So I checked disc space, and it was virtually 100% full again. And this all happened during a span of time, where I downloaded virtually no files, and certainly no large files. And did not install any new programs. Yet during this time, nearly a full Gig of space was eaten up.

How can I find out what is eating up such large chunks of space on its own ?
And at the same time, how can I free up the space ?

 I've already gotten rid of as many files and programs that I can. There's really nothing much in my own power that I can remove or delete, to free up the space. Whatever has eaten it up thus far, seems to have basically eaten up everything except the OS itself. The issue is even keeping me from being able to open my Anti-Virus program, to run a scan and see if a virus is causing this.

---

### Post by TheFu on 2016-12-02
look for new files. use whatever tool for that you like. I'd use 'find'.
1G isn't really much space. A new kernel could need 300MB alone for working space.  If you want to protect the system from this issue, split up the storage into different partitions so assorted files don't cause a full OS disk.

BTW, I'd look at browser caches too.  If you want flash/html5 videos ... those aren't small.

---

### Post by elvis6 on 2016-12-02
> **TheFu said:**
> 1G isn't really much space. A new kernel could need 300MB along for working space.

Thank you the help. And just to clarify, since I'm basically a novice level, the above action you reference, would occur as part of "System Updates" through Update Manager, is that correct ?

> **TheFu said:**
> look for new files. use whatever tool for that you like. I'd use 'find'.

Will "Desktop Search" program work ?
Or does this involve a manual command in Terminal ?

---

### Post by TheFu on 2016-12-02
I'm not much of a GUI user, so I simply don't know about those things. Sorry, it isn't how I work and Linux servers don't have a GUI, so learning the GUI way isn't useful to me.

You can use whatever method you want to find new files.  Again, I would use 'find' ... [http://www.tecmint.com/35-practical-examples-of-linux-find-command/](http://www.tecmint.com/35-practical-examples-of-linux-find-command/) might help. Look at examples #26 and a few after that one.  It is one of those extremely powerful commands that can accomplish amazing feats. It is also one of those commands which can seem highly complex to the uninitiated because there are so very many options which can be mixed and matched as desired.

---

### Post by elvis6 on 2016-12-02
Thank you for the help, again.
This issue is more serious than I thought. I was able to free up 99 Megs of space. And still felt I needed more, in order to get the system running well enough to troubleshoot and repair. So, then I totally removed Mozilla Firefox Browser - thinking I didn't need it while I was attempting to resolve the issues, and also it should free up a lot of space while I troubleshoot.

BUT, after I un-installed Firefox, the complete opposite happened. Instead of freeing up space, it went from 99Megs available, to zero available.
There's so little space I cannot even get the system to uninstall anything else.
What could have happened during that time, that ate up the last remaining 99 Megs, PLUS the space that should have freed up, when I removed Firefox (obviously I'm able to get online now using an alternate PC). I hadn't performed any updates or done anything whatsoever, that could explain all that space eaten up, in a short amount of time.

---

### Post by &amp;KyT$0P# on 2016-12-02
How big a disk do you have?

[This thread]("https://ubuntuforums.org/showthread.php?t=2331523") shows how to troubleshoot these type issues.  So, step 1, please post the output of this command -
```
cd /;sudo du -sxh $(ls -A) | sort -h
```

---

### Post by elvis6 on 2016-12-02
> **halogen2 said:**
> How big a disk do you have?

[This thread]("https://ubuntuforums.org/showthread.php?t=2331523") shows how to troubleshoot these type issues.  So, step 1, please post the output of this command -
```
cd /;sudo du -sx $(ls -A) | sort -n
```

I get this response :

du: cannot access 'home/joe/.gvfs' : Permission denied

(as for disk size, it's 17G)

---

### Post by TheFu on 2016-12-02
That's a good link.  Only thing I'd alter is using **du -sh /*|sort -h** (corrected).  The -h options are for "human readable" on both tools. Much easier to quickly see big areas.

Appears that bleachbit could be the root cause.  Never use that tool myself.  Also, beware running GUI apps with root permissions.  Unexpected things happen.

---

### Post by yetimon_64 on 2016-12-02
> **elvis6 said:**
> I get this response :

du: cannot access 'home/joe/.gvfs' : Permission denied

(as for disk size, it's 17G)

You may need to wait for quite a bit for it to fully print out, that is wait till the terminal returns a full terminal prompt. That command takes quite a while to complete here when initially run.

You do not show any printout of what the command is actually looking for, for example that command run here (adjusted for TheFu's human readable switches) reads like ...
```
yetiman:~ $ cd /;sudo du -sxh $(ls -A) | sort -h
[sudo] password for yetiman:               
<snipped my example results to prevent confusion for other helpers>                                      
yetiman:/ $
``` Note, your prompt will look different to my custom prompt which only shows my username. Yours will likely also show the hostname as well (standard display is "<user>@<hostname>:~ $").

You can see my prompt returned at the bottom of the output in the root directory (from the "cd /" part of the command), the output in bold text is what halogen2 was looking for, this part of the output shows what section of the file system is using up the most space. The errors up the top, like you reported as output of the command, can be ignored for the purpose of this thread.

OP, please try again and post back the full output. I would suggest you use the "human readable" switches as I have done in the above code box as suggested by TheFu.

@ TheFu, that was a very good idea putting human readable switches into the command, makes it very easy to read the actual sizes now.

---

### Post by &amp;KyT$0P# on 2016-12-02
> **TheFu said:**
> That's a good link.  Only thing I'd alter is 
Thanks! :KS  Edited above.

---

### Post by oldfred on 2016-12-02
What brand/model system?

We have seen run away log files in some systems that need a boot parameter.
             
 Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)
[http://ubuntuforums.org/showthread.php?t=2327570](http://ubuntuforums.org/showthread.php?t=2327570)

---

### Post by TheFu on 2016-12-03
It takes a long time because all the output from 'du' has to be completed before it can be 'sort'ed.  Cannot sort until all the du data is known.  du only needs to be run as root so that files your normal userid can't see are included.  Normally, du is run looking in your HOME and sudo isn't needed at all.

17G is an odd size for storage.  Also, I'd run **sudo du -sh /* |sort -h**. Need the asterisk to get summaries for all the directories under /. Corrected above.  Then basically I'd work below / as larger than expected directories jump out in the list.  Actually, I'd probably start with a 'find' looking for files over 500MB.  Something like **sudo find / -type f -size +1G** to start and making the size smaller as I clean up huge files.

---

### Post by &amp;KyT$0P# on 2016-12-03
> **TheFu said:**
> Also, I'd run **sudo du -sh /* |sort -h**. Need the asterisk to get summaries for all the directories under /. Corrected above.  
I used [FONT=Courier New]$(ls -A)[/FONT] above to pick up hidden (dot) files and folders.  Don't want to make assumptions.

---

### Post by TheFu on 2016-12-03
Using **ls** as an input into other commands has some dangers, I was taught.  Sometimes there isn't a better, quick, answer, just beware that sometimes it lies. [https://unix.stackexchange.com/questions/128985/why-not-parse-ls](https://unix.stackexchange.com/questions/128985/why-not-parse-ls) makes arguments for each side.  Probably beyond the OP.  In short, if it works, use it, but know that sometimes it breaks.

---

### Post by elvis6 on 2016-12-03
Hey, thanks you all, for all the suggestions.
Just a quick question. In the past, when I had generalized system problems, it was suggested that I reinstall the desktop interface - not a complete Ubuntu re-install, but just the desktop interface, if I'm remembering the term correctly. And it's fixed a couple diverse problems.
Would that work, for a situation like this ?

---

### Post by yetimon_64 on 2016-12-04
> **elvis6 said:**
> ...
Would that work, for a situation like this ?
You may be extremely lucky and jag it, but _*I highly doubt it*_ will help much in this case. 

_*Please post back actual terminal output from either of the commands offered by halogen2 or TheFu.*_ 

Seeing what part of your system is filling up will likely give someone a better idea of what is actually happening instead of taking "wild shots" at the problem by uninstalling/reinstalling packages.

Also a staff member (oldfred) asked a question of you about the brand/model of your system you still should answer as there may be a link to run away log files (which will likely show up in the terminal output that has been requested by the other 2 helpers already mentioned). It may be possible to fix your problem with a simple boot parameter change if it is related to such a situation.

Please post back the requested terminal output and answer questions helpers ask you.

Regards, yeti.

---

### Post by elvis6 on 2016-12-05
> **halogen2 said:**
>  So, step 1, please post the output of this command -
```
cd /;sudo du -sxh $(ls -A) | sort -h
```

> **yetimon_64 said:**
> You may need to wait for quite a bit for it  to fully print out, that is wait till the terminal returns a full  terminal prompt. That command takes quite a while to complete here when  initially run.

Ok, so here it is, after waiting the full length of time to process.

```

du: cannot access `home/joe/.gvfs': Permission denied
du: cannot access `proc/2997/task/2997/fd/3': No such file or directory
du: cannot access `proc/2997/task/2997/fdinfo/3': No such file or directory
du: cannot access `proc/2997/fd/3': No such file or directory
du: cannot access `proc/2997/fdinfo/3': No such file or directory
0    initrd.img
0    initrd.img.old
0    proc
0    sys
0    vmlinuz
0    vmlinuz.old
1.0K    lib64
1.0K    media
1.0K    mnt
1.0K    opt
1.0K    selinux
1.0K    srv
4.0K    dev
12K    lost+found
17K    tmp
454K    root
796K    run
8.3M    sbin
8.7M    bin
9.3M    etc
70M    boot
449M    lib
709M    var
2.2G    usr
11G    home
27G    host

``` 

> **oldfred said:**
> What brand/model system?

Dell Optiplex GX620

> **TheFu said:**
> 17G is an odd size for storage. 

Perhaps I should have mentioned that I am running a Dual OS system, and maybe that's the reason for that odd number ?

Thanks again, for all your previous and future help, and your patience with my slow response to retrieve all the information.

---

### Post by TheFu on 2016-12-05
First time, 4G was used in /home.
Now, 11G is used in /home.

Something you are running is doing this. It isn't the OS.  Start looking there.  
The 2.2G in /usr seems normal to me.
Previously it was 7.7G?  Guess you cleaned up a bunch of GUI programs?  GUI tools each space, but not as much as videos.

If you look closely, you can see that all the other locations are pretty small in relation.  I'd start looking for large files in /home/ using the **find** command already posted.  Or you can **cd** into each subdirectory and run **du -sh .** over and over looking for where all the big files are.  

Only you can figure this out.

---

### Post by elvis6 on 2016-12-05
> **TheFu said:**
> First time, 4G was used in /home.
Now, 11G is used in /home..

Are you looking at Yetimon's sample post, for the 4G ?
Because I don't see that in my posts.

> **TheFu said:**
> Previously it was 7.7G?  Guess you cleaned up a bunch of GUI programs?  GUI tools each space, but not as much as videos.
.

I was able to remove about 3G on my own, yes.

---

### Post by yetimon_64 on 2016-12-05
> **elvis6 said:**
> Are you looking at Yetimon's sample post, for the 4G ?
Because I don't see that in my posts...

I've now removed my example results, since you have posted terminal output, to prevent any confusion. Looks like TheFu may have been reading my example output. Cheers, yeti.

@ TheFu, sorry for the confusion. The OP has only posted one lot of terminal output. Yeti.

---

### Post by TheFu on 2016-12-05
Yep. My fault. Too much multi-tasking and not paying close attention before a deadline.

Wherever the extra files are, you need to find them.  Above are a few different ways to find them - by size or by date or by manually running 'du' on subdirectory after subdirectory.  

There are probably GUI tools for this stuff ... I don't use those so cannot recommend any.  Plus explaining how to use GUI stuff in a forum like this is just too hard. Regardless ... [http://www.makeuseof.com/tag/how-to-analyze-your-disk-usage-pattern-in-linux/](http://www.makeuseof.com/tag/how-to-analyze-your-disk-usage-pattern-in-linux/) might be useful. If you are limited on storage, **xdiskusage** is the smallest. Just dbl click on the blocks to work down and up. Simple graphics, so pretty much the same speed as the **du** cmds.

---

### Post by HermanAB on 2016-12-05
BTW, a disk filling up used to be due to a bad /etc/logrotate.conf file.  However, nowadays with the infernal Poetering systemd I don't know how the log system works anymore, but it may be worth looking at the log files and see whether you need to purge /var/log.

---

### Post by dragonfly41 on 2016-12-05
@TheFu wrote ... > [COLOR=#000000]There are probably GUI tools for this stuff ... I don't use those so cannot recommend any

Perhaps running Baobab (System Tools > Disk Usage Analyzer) will give OP a visual representation of disk usage.

It does take a long, long time to gather the data .. so take a break (about 15+ minutes or so) while it continues running.[/COLOR]

---

