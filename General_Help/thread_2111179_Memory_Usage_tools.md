---
title: "Memory Usage tools"
date: 2013-02-01
forum: General Help
---

### Post by matimont on 2013-02-01
Hi,

I'm using the command "top" to see how much memory the system is using (ram). Now, when I go to the desktop and run the system monitor tool that comes by default with the OS, it shows lot less memory usage then "top".

Top shows I'm using 1.7GB memory while the system monitor tool shows I'm using 560MB... Is there a reliable tool I can use to find out how much memory system is using?

Something I notice is that using "top" I see cached memory and if I substract the total used and cached I get more less the memory usage I see when I go to system monitor..


Mem:   2051648k total,  1835596k used,   216052k free,   113500k buffers
Swap:        0k total,        0k used,        0k free,  **1178872k cached**

Thanks!

---

### Post by grahammechanical on 2013-02-01
There is this

[http://en.wikipedia.org/wiki/Htop]("http://en.wikipedia.org/wiki/Htop")

[http://htop.sourceforge.net/index.php?page=faq]("http://htop.sourceforge.net/index.php?page=faq")

It is in the Ubuntu Software Centre

Regards.

---

### Post by sudodus on 2013-02-01
> **grahammechanical said:**
> There is this

[http://en.wikipedia.org/wiki/Htop]("http://en.wikipedia.org/wiki/Htop")

[http://htop.sourceforge.net/index.php?page=faq]("http://htop.sourceforge.net/index.php?page=faq")

It is in the Ubuntu Software Centre

Regards.
+1
I like htop and use it a lot. It shows memory the same way as the system monitor, it gives a clear overview, there are some easy tools, and it needs much less horsepower to run compared to the system monitor.

---

### Post by TheFu on 2013-02-01
top, htop all use the same system calls, so do not expect different answers. I don't know what *system monitor* uses or how it displays what it sees.  It isn't loaded on my system.

There is all sorts of "memory" in a Linux computer and so there are different uses and different labels for each kind.  Often, unused RAM is used for disk buffers to speed up reads and writes - from the end-user perspective.  It is available for programs, but using it for disk cache makes sense if no programs are using it.  When programs need it, the disk cache is flushed to disk so a program can use it.

There is shared memory too where the code segments, CS, from multiple running programs is loaded only once, but each program has a different DS, Data Segment, for itself.  So if the total memory used by a program is 500MB and you close it, it is unlikely that 500MB of RAM will become available.  Hopefully, most of the program uses shared libraries that other programs utilize too.  This is why people try to use either 100%
* GTK
or
* Qt
based programs. By using only 1 of those toolkits, less overall RAM is needed. If even 1 program uses the alternative GUI libraries, then all the RAM savings is lost, at least while it runs.

In the old days we used:
* sar
* vmstat
to monitor memory use. 

Of course, to understand exactly what each tool is reporting, check the man page.

[B]$ man top
$ man htop
$ man vmstat
[/B]
for example.  I also like a simple tool to monitor disk and network I/O along with memory use.  **saidar**.  It is like top with a text only display.

---

