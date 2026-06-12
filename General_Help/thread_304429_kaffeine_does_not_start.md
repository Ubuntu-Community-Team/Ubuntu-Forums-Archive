---
title: "kaffeine does not start"
date: 2006-11-21
forum: General Help
---

### Post by shpook on 2006-11-21
Hi

I am having a problem getting Kaffeine to work. For some reason it refuses to start up.

If I use the gui to start it from Multimedia>Kaffeine an hourglass icon appears in the taskbar for a few moments and then goes away.
Tried firing it up from command line with

```
kaffeine
kaffeine --verbose
kaffeine -w
```

.. but nothing seems to happen. Command executes without producing any output whatsoever.

I've reinstalled kaffeine and kaffeine-xine packages but that didn't help.

I would appreciate any suggestions on what else I could try to make it work, or any ways to figure out what is causing this behavior.

Please help. Thanks!

---

### Post by bjrnfrdnnd on 2006-11-25
Got the same problem...
I am running kubunt 6.10

---

### Post by rvdrijst on 2006-11-27
I had the exact same problem and [this post]("http://ubuntuforums.org/showthread.php?t=288077&highlight=kaffeine") has a (partial) solution.

Basically, kaffeine is already running and you have to kill it first. This can be done as follows (in case you don't know):

**ps -ef | grep kaffeine**, gives the *process id* of the hidden kaffeine process

**kill -9 *process id***, kills this hidden instance and 'fixes' kaffeine.

All that's left, is how to stop this hidden instance from starting automatically every time I reboot, crippling kaffeine. Anyone?:confused: 

-Robin

---

### Post by rvdrijst on 2006-11-27
Hmm, just rebooted and guess what: kaffeine still worked! I don't know what I did to stop it from automatically running...

I *did* run **kaffeine -w **from the Konsole which might have something to do with it so if you have problems after rebooting, try that.

-Robin

---

### Post by shpook on 2006-11-28
Thanks Robin!

That solved it for me. For some reason I had "kaffeine -session 10456e740000116284207600000046990052_1164749577_49839" running. Once that process was killed kaffeine could start again.

After rebooting everything seems to work fine too. There is no need to kill kaffeine on every reboot on my system.

---

### Post by maddbaron on 2006-11-29
this is what I get, which is the process ID?

> maddbaron@baronworks:~$ ps -ef | grep kaffeine
1000      4855     1  0 Nov26 ?        00:00:44 kaffeine -session 1013b14be1e1000116252954800000045860025_1164590133_404696
1000     28776 28758  0 09:36 pts/4    00:00:00 grep kaffeine


---

### Post by epd on 2006-11-29
the second number in the row is the Process ID.

In your case:

> 1000 4855 1 0 Nov26 ? 00:00:44 kaffeine -session 1013b14be1e1000116252954800000045860025_1164590133 _404696

> 4855

is that process ID.

e.

---

### Post by apanloco on 2006-11-29
thanks guys, this solved it for me too!

---

### Post by maddbaron on 2006-11-29
thank you

---

