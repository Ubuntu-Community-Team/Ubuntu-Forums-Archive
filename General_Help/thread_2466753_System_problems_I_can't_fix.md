---
title: "System problems I can't fix"
date: 2021-09-04
forum: General Help
---

### Post by Gnusboy on 2021-09-04
Hello all;

I stuck on trying to fix system issues with Ubuntu 20.14. 

My system: AMD 9850 Quad core, 650 HD, 2 GB ram, a 1TB external drive.

I do not know whand I continually have system problems that cause the pointer to freeze 
and requires a reboot to free it. 
When I am working, I often have a few different windows I work in and I have occasionally had my system fail if there is a glitch with a web site. But it is nothing like my current problems. 

During this process there was a reference to a site open in the Firefox browser. 
It strangely referred to https/www.harborfreight.com.  I have not seen that anywhere before now.

When this happens, if I kill a process that is using resources, it will usually return my system to normal operation - until it happens again.  at worst it will need a reboot to clear the problem.

Most of the time a reboot releases the pointer, which allows me to go back to work util I have the same problem.
Once I get back control of the system, I go back to work - until it happens again. I was used to things like that when I worked using Windows. But Ubuntu is far more stable. 
 This appears to be random, but I don't know how to diagnose it or recreate it on command. 

I have tried a variety of ways to figure out and/or fix it. In my current situation - which is far worse than usual, I've tried many ideas to fix the system and hopefully stop it from happening again.

I've tried to wait it out, to see if it fixes itself, but it does not.
I tried rebooting seeing if it would lload normally. That just loads the same version as before. 
I also tried to make it load into an earlier version, using recovery mode. However, that takes me to a screen prompt that allowed me to input FSCK. I thought using FSCK would either fix the errors or show me the problem. When I tried FSCK I got a line showing "Unexpected Inconsistency" Run FSCK manually. 
FSCK exited with Status Code 4.
The result of this displayed several lines of errors of missing Inodes and block errors with lines of options to repair the system. 
These lines were asking "Ignore Error" <y> or continue. I hit <y> all the way through. When it was finished it took me to a line showing



 ```
***** FILE SYSTEM WAS MODIFIED***** 
/dev/sda5 ... 271633/39043072 files (1.3% non-contiguous)788/156151296 blocks.
```

(initramfs) The only way I know how to get past the INITRAMFS is to boot into the live 20.41 disk. I know there are other options, but I could not locate them.

```
(Initramfs) FSCK 
FSCK from util-linux 2.34
(Initramfs) /dev/sda5
(Initramfs) /dev/sda FSCK from util-linux 2.34
sh: /dev/sda5: Permission Denied 
(Initramfs)
(Initramfs) FSCK /dev/sda5 
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/sda5: clean, 271633/39043072 files,7884737/156151296 blocks
(initramfs)
```

I might not be describing this situation. I'm writing this on an old windows machine still running XP. If I am not clear in this description, because I'm trying to remember information showing on my Ubuntu desktop. Much of the descriptions of my problem scroll through very fast. I've looked for a way to page up so I can read them. But the solutions I found don't work for me.
I'm also not a Ubuntu super whiz. Everything I learn, must get whizzed out.
I will try to answer all the questions.
Thanks for your help.


 Addendum:
I know there is a command to get past INITRAMFS  but I could not find it.

There is a strange problem the showed up during this process. It showed that looked like ia problem with Firefox and a storage default at https/www.harborfreight.com 
I primarily use Firefox. 
It's possible that this might be part browser problem, and part system issue. I've never heard of it before, but I don't know how to diagnose the problem. I don't know why that would show up when I am working in a terminal.







 Then I use the live 20.14 disk

---

### Post by DuckHook on 2021-09-05
There is no version 20.14 nor 20.41. I assume you mean 20.04, which is LTS and therefore still supported. If 20.10, then this is out of support. General users should run LTS. However, be aware that 2GB of RAM is not realistically enough to run Ubuntu and if you are running an older MOBO where the video card steals RAM to use as VRAM, then 2GB could very well be the bottleneck that causes your mouse freezes.

Moreover, one of the worst apps to run on limited RAM is a web browser. They all eat RAM for breakfast. You need at least 4 GB of RAM to run Ubuntu properly. So, at the outset, I would suspect that your limited RAM played at least some part in your initial freeze&#8209;ups.

At this point, it will be hard to determine if the problem is further exacerbated by a corrupted OS from the reboots. You do not tell us how you rebooted, but if it was done by using the physical reset button on your computer, then the file system could have been left in an open and unstable state which would lead to data corruption, hence the requirement for FSCK.

It is also possible that your HDD is failing. If the corrupted sectors are those holding your OS, then this may have resulted in loading a corrupted mouse driver.

I'm afraid that my advice is not directed at solving your immediate problem, but the larger meta&#8209;issue:

[list=1]
[*]First, check that you still have a good and reliable HDD. There are many web articles advising how to use *hdparm* or *smartctl* (found by installing *smartmontools*)
[*]If the HDD is fine, then you should increase your RAM to at least 4 GB.
[*]If increasing RAM is not an option, then you should consider running a lighter flavour (see my sig: *The Best 'buntu Flavour*) instead of Ubuntu.
[*]Even if running a lighter flavour, consider a lighter browser like *Midori* or *Epiphany* (now marketed as Gnome Web).
[/list]

---

