---
title: "Very slow booting - please assist"
date: 2012-12-27
forum: General Help
---

### Post by 9antreas9 on 2012-12-27
I installed ubuntu on my system when I bought it, around one year ago.

I installed 11.10, then upgraded to 12.04 and 12.10.

Over the last year my system boot time has deteriorated a lot, to the point that it led me to look into it.

So I installed bootchart and bootchart GUI to see if I can find any clues.

Sadly, I have no skill in understanding the output chart, so I am posting it here in case someone might help me.

[http://anpel.dimiourgiasite.gr/ubuntu-quantal.png](http://anpel.dimiourgiasite.gr/ubuntu-quantal.png)

The rest of the files generated is here:

[http://anpel.dimiourgiasite.gr/ubuntu-quantal.tgz]("http://anpel.dimiourgiasite.gr/ubuntu-quantal.png")

Please let me know if there is anything I can do to make my system boot faster, or if I should just accept it and go on.

---

### Post by oldfred on 2012-12-27
I never learned to read boot charts.

But I do look at log files. Specifically dmesg and errors, long times between entries, or repeated attempts at loading and either fail or sometimes working.

---

### Post by Polydorus on 2012-12-27
How much time are you talking about?  Since I installed 12.04 in September, start up has gone from something like 20 seconds to maybe 90.  I assumed that was normal as I have added more programs, files and such.

---

### Post by 9antreas9 on 2012-12-27
90 seconds seems to be close to what I'm getting, and 20 seconds is pretty close to what I was initially getting.

If that is just the extra load I've put on my system over time, I can compromise with it.

But if something is wrong and I can fix it, why not ask?

Hibernate does not work on my system (don't know if I can fix it, tried a few workarounds with no luck) so I have to shut down every time I leave my workstation.

So 90 seconds bugs me, and changing it would make me happier with my system.

---

### Post by 9antreas9 on 2012-12-27
Looks like I found something..

In dmesg there seem to be some big time differences between log entries.

One of them is about 35 seconds.

Here is my dmsg output.

Look what happens after exactly 2 seconds, 2.003964 to be exact.

[http://anpel.dimiourgiasite.gr/dmesg](http://anpel.dimiourgiasite.gr/dmesg)

Any ideas?

---

### Post by Impavidus on 2012-12-27
It can increase a bit when it has to start more things at boot, but quadrupling sounds excessive. It's not what I see in my computer that has been running Ubuntu for six years without reinstalling. Have a look at the log files, especially dmesg, as oldfred suggested. You can find them in /var/log.

PS: I see you just did that.

---

### Post by mrjava on 2012-12-27
I have a boot time of around 70-80 seconds on 12.04, 90 seconds doesn't seem much longer.


However, if you have the option, use all cores (multicore systems only, obviously :P) during startup:

```
sudo gedit /etc/init.d/rc
```

Find the line that reads CONCURRENCY=none and replace it with CONCURRENCY=makefile

---

### Post by 9antreas9 on 2012-12-27
> **Impavidus said:**
> It can increase a bit when it has to start more things at boot, but quadrupling sounds excessive. It's not what I see in my computer that has been running Ubuntu for six years without reinstalling. Have a look at the log files, especially dmesg, as oldfred suggested. You can find them in /var/log.

PS: I see you just did that.

Yes I did, and it looks like there is something to fix, as the system remains idle for 35 seconds for some reason.

Can you point me to where should I start looking?

---

### Post by Cheesehead on 2012-12-27
The first thing I see on that bootchart, line 9 and taking about 18s, is mount.ntfs. That's an unusually long time to mount a drive.

- Are you really running from an NTFS hard drive? That's not recommended.
- Have you booted into windows and defragged it? Is it almost full?
- Or if you are using an ext* format, how full is it?

Take a look at the second graph line - disk throughput and disk utilization. See how utilization (the shaded area) is very high, but throughput (the green line) is very low and wiggles around a lot? That's unusual - Ubuntu uses a program called ureadahead to make the green line rather constant and load the system faster.

- That's another clue that your drive might need to be defragmented.

See the vertical dashed line around 45s? That's the point where the command-line system is complete. After that it's starting lightdm (the login screen) and the windowing system and Unity.

---

### Post by oldfred on 2012-12-27
I noticed just mounting NTFS partitions changed my boot time from 20 sec to 25 sec with an SSD.
But I have had issues where my XP would boot but Linux would not see the NTFS partition. After running chkdsk XP booted a bit faster and then Linux mounted it without issue. I might try chkdsk on all NTFS partitions.

---

