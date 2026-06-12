---
title: "rc.local executing before fstab?"
date: 2013-03-18
forum: General Help
---

### Post by Asday on 2013-03-18
I have a ramdisk mounted by fstab, and it works pretty well.  It also works pretty well with samba, sharing it to some windows PCs.  When I start the PC, it doesn't require any intervention for things to be running smoothly.

The downside to a ramdisk, though, is the volatility.  It's absolutely fine by me, but I'd like somewhat of a structure there.  My idea was to put a load of mkdirs in rc.local.

For whatever reason, it isn't working.  I've read about adding a sleep at the top of the script, but this seems a bit barbaric, and I only ever saw people using that when they were doing something with networking in rc.local, whereas mine is only dealing with filesystems.

I've read that rc.local is executed asynchronously, but I have also read that fstab will always run before it, so I don't know why what I'm trying isn't working.

Here are some of the lines in my current rc.local:

```
su asday -c mkdir /media/ramdisk/4x6
su asday -c mkdir /media/ramdisk/4x6/done
su asday -c mkdir /media/ramdisk/ID\ Cards
```

etc.

Thank you for your time

---

### Post by TheFu on 2013-03-18
An understanding of the /etc/rc{N}.d/ directories and /etc/init.d/ will help you greatly.

init.d/ holds all the legacy startup scripts and the rc3.d/ holds softlinks back to those scripts based on the init-level (also called runlevel) and order to start/kill the scripts.  Looking in /etc/rc3.d/ I see [SK]{NN}scriptname links.  The S or K are for start and stop. The number is the order to be run.  "S99rc.local" means that rc.local will be called after every other startup script with lower numbers for that init-level.  The stop scripts begin with "K" and are run in reverse order for the runlevel.

Recently, a different process called "upstart" has begun taking over these 25+ yr old scripting methods to solve a few issues. How those integrate in, I don't understand. In some ways, it must be better, but I haven't had a reason to learn upstart.  I like the simplicity of the /etc/rcN.d/ scripts. Nothing is hidden, it is easy to understand and it has worked "well-enough" for the huge majority of users all this time. 

I might become sold on upstart in the future. Can't say.

The other thing is that you might want to read the man-page on mkdir.  There is a -p option you might like.

---

### Post by rnerwein on 2013-03-18
> **TheFu said:**
> An understanding of the /etc/rc{N}.d/ directories and /etc/init.d/ will help you greatly.

init.d/ holds all the legacy startup scripts and the rc3.d/ holds softlinks back to those scripts based on the init-level (also called runlevel) and order to start/kill the scripts.  Looking in /etc/rc3.d/ I see [SK]{NN}scriptname links.  The S or K are for start and stop. The number is the order to be run.  "S99rc.local" means that rc.local will be called after every other startup script with lower numbers for that init-level.  The stop scripts begin with "K" and are run in reverse order for the runlevel.

Recently, a different process called "upstart" has begun taking over these 25+ yr old scripting methods to solve a few issues. How those integrate in, I don't understand. In some ways, it must be better, but I haven't had a reason to learn upstart.  I like the simplicity of the /etc/rcN.d/ scripts. Nothing is hidden, it is easy to understand and it has worked "well-enough" for the huge majority of users all this time. 

I might become sold on upstart in the future. Can't say.

The other thing is that you might want to read the man-page on mkdir.  There is a -p option you might like.
hi 
+++++++++++++++++++++++++++++++1
from a unix user since 1983 (sytem III), even minix ( tannenbaum - 1988 i guess this was the root of linux because unix becomes comercial (torvald linus), linux since (1993).
and i think: the upstart is bul.... . rc's was working fine and sorry - for me more logical.
my opinion was and is still now: assembly is the latin of programing languages, C is like a rasor blade but without a grip and the next time i can't sleep i'll think about a new
language, using yacc and lex ;-) to make things more complicated.
ciao
   richi
ciao
           richi

---

### Post by Asday on 2013-03-18
Ok, so /etc/rc{N}.d/ is the stuff that runs when you enter different "run levels" denoted by {N}?

My /etc/init.d/rc.local looks completely different (doesn't even end with "exit 0").  Have I been editing the right one?  (/etc/rc.local)

In my /etc/rc3.d/, I have an S20ddclient file.  I have a ddclient line in my /etc/rc.local, too.  Did something that reads rc.local put the S20 file there, or did I just not know it before, and make redundancy myself?

I think I'm getting it, though, I need to figure out what a run level is, I think, but that shouldn't stop the mkdirs in my current rc.local executing...?

The -p switch is amazing, thank you.  I thought I was too cool to read the man pages for "simple" commands.

EDIT:  This is @TheFu.  I misunderstood the Quick Reply button.

---

### Post by Asday on 2013-03-27
So I thought I was onto something when I ran runlevel, and found I was in runlevel 2, which is because I'm on a single user machine, as far as I can gather, but then came up against another wall when /etc/rc2.d/S99rc.local is softlinked to the same place the rc3.d one is, and either should run /etc/rc.local.

Would commands in rc.local failing leave a log anywhere I could find?  (I can't actually restart the PC at whim, due to an unrelated issue with the motherboard, meaning it only POSTs about one in twenty times, so I'm reluctant to do my normal "change one thing, reboot, and see" method).

---

### Post by prodigy_ on 2013-03-27
Are you sure your fstab entries are correct? Does **sudo mount -a** complete without any errors? In any case rc.local can't run **before** mountall (how can you run anything when you don't have root file system?) so you should check your fstab syntax and add something like:
```
set -x
exec 2>/root/rc.local.log
```
to rc.local (before any other commands).

---

### Post by Asday on 2013-03-27
> **prodigy_ said:**
> Are you sure your fstab entries are correct? Does **sudo mount -a** complete without any errors? In any case rc.local can't run **before** mountall (how can you run anything when you don't have root file system?) so you should check your fstab syntax and add something like:
```
set -x
exec 2>/root/rc.local.log
```
to rc.local (before any other commands).

I dunno what I did, 'cause I usually break things before they work, but my fstab is immaculate, and works perfectly.  mount -a works just fine.

set doesn't have a man entry, and exec's man entry didn't make any sense to me, and ls /root/ gave me a permission denied; could you please explain your code to me?

Thank you for the fast response.

EDIT:  Well I decided to take a break from being an idiot, and `sudo /etc/rc.local`.  Apparently mkdir is missing an operand.

If this is what has been giving me problems, I might just take a break from life.  Go live in a mountain cave for a bit.

(Later)  Apparently I needed quotes around my mkdir command with su [user] -c.  Cool.

Hey how do I mark a thread as solved?  I don't see it in Thread Tools, and I can't seem to do it by editing my original post.

---

### Post by prodigy_ on 2013-03-27
Just add [SOLVED] manually to the title.

P.S. **set** and **exec** are bash built-ins, use **man bash**. **set -x ** essentially tells the shell to output all subsequent commands (after all expansions) to **stderr **so you can see what is actually being executed. This command is your best friend when you need to debug a bash script. :) And **exec** in this example redirects **stderr** output to **/root/rc.local.log** file.

---

### Post by Asday on 2013-03-27
So why /root/?  I was denied access there with ls; wouldn't /home/ be better?

---

### Post by prodigy_ on 2013-03-27
You could use **/home**, sure. However, rc.local is executed as root so **/root** would also work. :) And to view a file in /root: ```
sudo cat /root/filename
```

---

### Post by Asday on 2013-03-27
> **prodigy_ said:**
> You could use **/home**, sure. However, rc.local is executed as root so **/root** would also work. :) And to view a file in /root: ```
sudo cat /root/filename
```

Sweet, well, thanks for the help, (and thanks to TheFu up top, too).

---

