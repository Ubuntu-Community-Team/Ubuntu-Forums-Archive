---
title: "I need some help"
date: 2008-03-03
forum: General Help
---

### Post by lekkin on 2008-03-03
Okay, let me first say that I'm basically a noob, just as a warning.  Anyways, I have a laptop which came with Vista on it.  Needless to say, I wasn't all that happy.  Anyways, my brother partitioned my computer and installed Linux on it for me, so I can choose between Linux and Vista when the computer starts.  One time while I was on Vista (I do need windows to run some programs, unfortunately), and it froze on me, so I had to manually shut down the computer.  I started up Linux again and it started a forced system check.  I don't have the details off the top of my head, but I can get them if you need them, though I'm hoping it's some common problem you can help me solve.  This happened once before, and I just loaded Windows and shut it down properly in order solve the problem, but that didn't work this time.  Oh yeah, the problem with the forced system check is that it freezes and won't finish.  If this isn't enough info, I'll try it again and see what I can come up with.  Oh!  And I'm using Ubuntu.

There's one other minor thing not as important.  I didn't give Vista quite enough memory for it's partition, how can I take a little bit from Linux that's not being used and give it to Vista?

---

### Post by RedSquirrel on 2008-03-03
Are you sure the system check is frozen? Sometimes it takes a while.

---

### Post by lekkin on 2008-03-03
Well, that depends.  Does 20 minutes on the same exact percent count as frozen?

---

### Post by lekkin on 2008-03-04
Hmm, an interesting thing happened this last night: I tried to turn on Linux again, and it started the scan again.  It got farther this time, up to 55.6.  So I left it on over night to see if it would finish.  When I woke up, it was still stuck at 55.6%.  Does this mean I just need to keep turning it on and off?  Can anyone help?

---

### Post by RedSquirrel on 2008-03-04
I have never had this issue myself, but I found this thread:

[http://ubuntuforums.org/showthread.php?t=526095](http://ubuntuforums.org/showthread.php?t=526095)

which may or may not help.

It seems that it could be an Ubuntu kernel bug or a hardware problem.

If I find anything more about this I will post. You might try searching the forums, Google, and [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/).

---

### Post by lekkin on 2008-03-04
Thanks :-)

Okay, I tried running it again a couple times tonight.  It got as far as 74.6% once, but it still froze.  Here's how I know it froze: there's this little blinking underscore under the beginning of the line, and as long as that's there, it's doing stuff.  Even if the percent doesn't move for a minute or two, it's scanning.  But multiple times, that just disappears before the scan is finished, and then I know that the scan is frozen.  Waiting 20 minutes, an hour, or even over night doesn't help.  But anyways, that's that.  I have no idea if that information helps or not.  

Anyways, could you help me with something?  In that thread you linked to, the following thing worked for two people, but I really don't understand what it means to do (my brother installed Ubuntu for me, I really don't know what I'm doing, I can use Ubuntu well, I just have no idea how to repair it), so could you interpret the following for me into something I can understand? :)

> **markph said:**
> I booted up using my LIVE CD and ran:
```

sudo e2fsck -C0 -p -f -v /dev/sda2
```

No errors were reported.  I shutdown the laptop, removed the LIVE CD and booted back up into Kubuntu with no problem.

---

### Post by RedSquirrel on 2008-03-04
It's just repairing the file system.

You can read about it in the man page. Open a terminal (Applications -> Accessories -> Terminal) and type

```
man e2fsck
```

Here is a summary:

**e2fsck**
check a Linux ext2/ext3 file system

**-C0**
Show progress bar.

**-p**
Automatically repair ("preen") the file system.  This option will case e2fsck  to  automatically fix any filesystem problems that can be safely fixed without human intervention.  

**-f **
Force checking even if the file system seems clean.

**-v**
Verbose mode.

Have a look at this:
[http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_](http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_)

Using a LiveCD with GParted, you should be able to do the repairs as described in the steps in that link. I have never tried those steps (haven't had to ;)), but it sounds like it would be worth trying.

Good luck. :)

---

