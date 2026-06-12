---
title: "memory leak?"
date: 2006-08-05
forum: General Help
---

### Post by kno712 on 2006-08-05
Hello all!

Here is what I have. I boot up, run a console and type 'free' and I get nearly half of the memory installed is free (I have 512 Mb on a laptop with a Centrino 1.5 Mhz). Then I run firefox for a while (it is the main use of my laptop), then close firefox and even if i wait for a while, free memory has dropped down drammatically!

Can someone tell me if this is normal?

---

### Post by Jagot on 2006-08-05
Firefox is well known for memory leaks.  You may want to try this:

[http://www.realtechnews.com/posts/2920](http://www.realtechnews.com/posts/2920)

---

### Post by kno712 on 2006-08-05
so, what other program do you recommend me to use?

---

### Post by Jagot on 2006-08-05
You could try Opera or Epiphany if you are bothered about it.

---

### Post by kno712 on 2006-08-06
I've downloaded Opera. It seems that it doesn't have the memory leak problem (althougth I liked more Firefox). Someone knows how is that the Firefox team did not put a stop to this probem yet? I hate to say this but in this situation Firefox is not can not be considered a re-emplacement to Internet Explorer. I can not recommend ayone to use it. Hope that next releases solve the problem.

Best regards and thanks for your help.

---

### Post by mcduck on 2006-08-07
> **kno712 said:**
> Hello all!

Here is what I have. I boot up, run a console and type 'free' and I get nearly half of the memory installed is free (I have 512 Mb on a laptop with a Centrino 1.5 Mhz). Then I run firefox for a while (it is the main use of my laptop), then close firefox and even if i wait for a while, free memory has dropped down drammatically!

Can someone tell me if this is normal?

Keep in mind that the line you need to read to find out the amount of free ram is the '+/- buffers/cache'.

Linux uses all free RAM as disk cache so the first line of 'free' output will almost always show all your RAM to be used after the system has been used for a while.

But it's true that Firefox can eat quite a lot of memory. Usually this isn't a problem unless you are running a machine with less than 256 MB of RAM or keep open many FF windows with tens of tabs at the same time. If the problem is more serious than that it's most likely caused by some bad extension you are using..

---

