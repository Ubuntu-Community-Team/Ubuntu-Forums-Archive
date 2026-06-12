---
title: "I want to overwrite the blank sector of my hard drive but can't find a tool to do so"
date: 2013-04-06
forum: General Help
---

### Post by EliteNeophyte on 2013-04-06
Hi, I'm not new to Ubuntu, but I'm looking for a specialized tool and I can't seem to track it down, when I was a windows user I had a program called Eraser, I had set eraser to give the empty and deleted sectors of my hard drive a once-over with a layer of zeroes every morning at 3 am, simply as a matter of privacy, now that I have made the full switch over to Ubuntu (I'm no longer dual booting) I would like to do the same, I had un-alocated my partitions using a live version of Gparted, then installed the os I'm running from now, I want to give my harddrive one last scrub, spring cleaning if you will but can't find a Linux compatible program that performs the task, any of you know something?

(and I know google is your friend, I searched high and low for a program like this, found nothing that wouldn't do a complete erasure)

---

### Post by ibjsb4 on 2013-04-06
There are several ways to do it, check here.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=secure+delete+hdd+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=secure+delete+hdd+partition&sa=Search&cof=FORID:9)

---

### Post by EliteNeophyte on 2013-04-06
Wow thanks for the speedy reply, I'm checking out the link now

---

### Post by EliteNeophyte on 2013-04-06
Okay I just have a question about the wipe command, does that just clear the empty sectors or will it preform a full erasure?

---

### Post by zero2xiii on 2013-04-07
Hay,

As a general rule, if ever you want more information on an installed application, run "man command" in terminal, such as "man wipe".

However if the software is not installed, a simple google search will give you the same result most of the time, or directly go to: manpages.ubuntu.com/

And according to this website:
[http://manpages.ubuntu.com/manpages/precise/man1/wipe.1.html](http://manpages.ubuntu.com/manpages/precise/man1/wipe.1.html)

> wipe repeatedly
       overwrites special patterns to the files to  be  destroyed,  using  the
       fsync()  call  and/or  the  O_SYNC  bit to force disk access. In normal
       mode, 34 patterns are used (of which 8 are random). These patterns were
       recommended      in      an      article     from     Peter     Gutmann
       (pgut001@cs.auckland.ac.nz) entitled  "Secure  Deletion  of  Data  from
       Magnetic and Solid-State Memory". A quick mode allows you to use only 4
       passes with random patterns, which is of course much less secure.

But
> Journaling filesystems (such as Ext3 or ReiserFS) are now being used by
       default  by  most Linux distributions.  No secure deletion program that
       does filesystem-level calls can sanitize  files  on  such  filesystems,
       because  sensitive  data  and  metadata  can be written to the journal,
       which cannot be readily accessed.  Per-file secure deletion  is  better
       implemented in the operating system.

However please read through the above mentioned page. There are a few pitfalls, depending on HOW SECURE you wish the data to be erased. If just to protect against script kiddies with "photorec" and "test disk" or a copy of backtrack 5... Wipe should be fine. If you want to protect against forensic investigators that recover data from crispy hard drive platters (mission impossible jumps to mind)... well then wipe will not be enough.. Remember: "a certain task has a certain tool, other may work, but not as good as a certain tool for a certain task"

Regards

---

