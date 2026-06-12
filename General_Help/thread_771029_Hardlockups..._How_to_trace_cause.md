---
title: "Hardlockups... How to trace cause?"
date: 2008-04-27
forum: General Help
---

### Post by SSamiK on 2008-04-27
I've been running Hardy on three computers since Alpha 3 or somewhere around there... Never had any big troubles with any of those machines, on my main desktop computer I've keept Gutsy until yesterday... And now I'm plaged with random, but frequent, hard lockups. I've tried looking throught logs, but nothing stands out. 

Only way to get out of the hardlock is to powerdown. No key combo helps.. 

So, how do I trace whats going on? 

Im on a AMD Athlon with a NVIDIA GPU, 1GB RAM. Added output of lspci -vvv
 
I'll provide more info as needed.

---

### Post by SSamiK on 2008-04-28
Forgot mention in my previous post, that i've read up on this issue for quite some time. I first found it in Gutsy, but by adding noapic and nolapic to my menu.lst my comp was running rock solid. However, in Hardy this do nothing... Nether to "acpi=off" or "noacpi" 

I've read anything that I can find about these random lockups on different forums and at launchpad, but nothing seems to help. So, ether I'll have to go back to Gutsy and hope I'll get it running smoothly again OR the other option wich ATM seems the most likely, change distro. Windows is not an option. :-) (Gutsy lost some appeal as a update to hardy mosy likely will bork my system again, only thing that speeks for a Gutsy "rollback" is that i've got /home on a seperate partition, so I wouldn't loose any data)

Now, what would be the next logical distro to check out? I've tried Fedora, didn't like it... I got a server running Gentoo, but it seems a bit over the top for a desktop computer, and time consuming to setup/intall apps. 

I used to love Ubuntu (and still do), now it just gets me frustrated and almost makes me miss Windows, cause back then i didn't know that anything could perform any better so I just were happy. Now, I can barely check my mails, letalone play a game or watch a movie throught my comp. 

Actually, it feels like I'm dying a tiny little bit each time a hardlock occur. :(

---

### Post by ghost_ryder35 on 2008-04-28
you running 64bit?

---

### Post by SSamiK on 2008-04-28
> **ghost_ryder35 said:**
> you running 64bit?

Nope... 32bit generic kernel atm, also tried the -rt kernel. Sorry, forgot to mention that. Also, no desktop effects enabled.

---

### Post by ghost_ryder35 on 2008-04-28
rt kernel was locking up too?  I was under the impression the rt kernel fixed it for everyone I have read about.  GRRR...  Is your computer capable of running 64bit?  If it is I would try running the 64bit version to see if it keeps locking up.  And if you are seriously considering switching distros I would recommend [Debian 4.0]("http://www.us.debian.org/")  Things rock solid :) And sine Ubuntu is based off of it there practically the same :) :) :)

---

### Post by SSamiK on 2008-04-28
Better to be safe than sorry, so i'll go ahead and try the rt kernel once more. Maybe that in my frustration I forgot to boot the right kernel. If the troubles persist afterwords I'll propably give Debian a try. It's safe to say; It propably can't get worse! :-D

---

### Post by ghost_ryder35 on 2008-04-28
> **SSamiK said:**
> Better to be safe than sorry, so i'll go ahead and try the rt kernel once more. Maybe that in my frustration I forgot to boot the right kernel. If the troubles persist afterwords I'll propably give Debian a try. It's safe to say; It propably can't get worse! :-D
If that doesnt work.  In all the reading I have done I have not heard about anyone compiling there own kernel for their specific system.  Only using generic kernels.  Maybe you should try compiling your own kernel and see if that helps.
Download the Kernel = [http://www.kernel.org/](http://www.kernel.org/)
How Too = [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by SSamiK on 2008-04-29
It comes as a surprise on me, but since I last installed -rt kernel, I've had no more hardlockups. I'm off to work now, can't wait to get back and check if it's still alive in some hours. :-D


Note: 4 days later, and still no lockups with -rt kernel.

---

