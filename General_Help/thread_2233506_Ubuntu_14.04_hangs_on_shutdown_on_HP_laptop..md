---
title: "Ubuntu 14.04 hangs on shutdown on HP laptop."
date: 2014-07-08
forum: General Help
---

### Post by Garchomps on 2014-07-08
Ubuntu hangs on shutdown while asking all remaining processes to stop, I have to press the power button for it to actually go down.
I've tried setting acpi=force, off, etc... In the grub config and nothing so far has worked. 
Is there a way around this?

---

### Post by claracc on 2014-07-09
Does it always hang at shutdown?, I mean, when the laptop is plugged to ac current and you try to shutdown hangs?, and on battery too?.

---

### Post by Bucky Ball on 2014-07-09
Would help if you could tell us which process(es) it gets stuck on. From what you describe you can see scrolling text then it stops. What does it stop on? ;)... 

Does it get stuck just on the 'waiting for remaining processes to stop' message?

PS: Please remove the changes you made to grub that didn't work. Thanks.

---

### Post by Garchomps on 2014-07-09
> **Bucky Ball said:**
> Would help if you could tell us which process(es) it gets stuck on. From what you describe you can see scrolling text then it stops. What does it stop on? ;)... 

Does it get stuck just on the 'waiting for remaining processes to stop' message?

PS: Please remove the changes you made to grub that didn't work. Thanks.
Done, it is just stuck on the 'waiting for remaining processes to stop' message, and I cannot tell which processes those are. And as someone asked earlier, yes, this done happen when it is plugged in and not plugged in to AC.

---

### Post by Bucky Ball on 2014-07-09
Happens on battery and not on wall socket?

When it gets stuck, can you get to a tty with pressing Ctl+Alt+F1? If so, you might need to login then type:

```
dmesg
```

Look at the bottom and it might let us know what the hold up is.

---

### Post by Garchomps on 2014-07-09
.

---

### Post by Garchomps on 2014-07-09
> **Bucky Ball said:**
> Happens on battery and not on wall socket?

When it gets stuck, can you get to a tty with pressing Ctl+Alt+F1? If so, you might need to login then type:

```
dmesg
```

Look at the bottom and it might let us know what the hold up is.

I think I may have worded that wrong, I get this problem both when  plugged in and not plugged in, regardless both have the same issue. As  for running dmseg, the keyboard doesn't work after pulling up the tty  during the shutdown process where it gets stuck.

---

### Post by Garchomps on 2014-07-09
bump

---

### Post by Bucky Ball on 2014-07-09
This might keep you busy for awhile. I have a few other things to do at the moment:

[https://duckduckgo.com/?q=14.04+hangs+at+shutdown](https://duckduckgo.com/?q=14.04+hangs+at+shutdown)

---

### Post by Garchomps on 2014-07-09
> **Bucky Ball said:**
> This might keep you busy for awhile. I have a few other things to do at the moment:

[https://duckduckgo.com/?q=14.04+hangs+at+shutdown](https://duckduckgo.com/?q=14.04+hangs+at+shutdown)I don't think you understand, I've already tried everything the forums recommended. However, I managed to write an init script that runs dmesg at shutdown and dumps the results to a file. I hope this all makes sense. Here it is, I posted it on pastebin since it was too large.
[http://pastebin.com/Rf1Zii9F](http://pastebin.com/Rf1Zii9F)

---

### Post by Garchomps on 2014-07-09
I solved it, an apparmor profile for a service was blocking shutdown. I just ran a command to put dnscrypt-proxy into complain mode and everything is back to normal. Problem solved.

---

### Post by Bucky Ball on 2014-07-09
Excellent news and good find. Could you please mark the thread as solved to help others using 'Thread Tools' at the top right of the page. Good luck. ;)

---

### Post by Arabella77 on 2014-07-12
"I just ran a command to put dnscrypt-proxy into complain mode and everything is back to normal."

Could you be a bit more specific, please Garchomps? I have the same problem with my HP laptop...

---

