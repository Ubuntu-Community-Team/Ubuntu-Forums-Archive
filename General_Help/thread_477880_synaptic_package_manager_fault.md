---
title: "synaptic package manager fault"
date: 2007-06-18
forum: General Help
---

### Post by letitworknow on 2007-06-18
when ever i open synaptic package manager i get an error that says...

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


when i hit the close button snyaptic shuts down.  it worked for a while but now nothing

---

### Post by jasmuz on 2007-06-18
Open a terminal, type: sudo dpkg --configure -a
Let it do its job and then try again to open Synaptic.

Please post the result

---

### Post by letitworknow on 2007-06-18
thanks man that worked i wasnt typing  "sudo" in the terminal.   what does sudo do if you would please enlighten me

---

### Post by jasmuz on 2007-06-19
Read this about [sudo]("http://en.wikipedia.org/wiki/Sudo")

---

### Post by sixou on 2007-06-19
I have the same issue. After running the script in the terminal I had the following result:

dpkg: parse error, in file `/var/lib/dpkg/updates/0015' near line 1:
 newline in field name `#padding'

I tried to edit the file but the file was empty. What should I do?

---

### Post by sixou on 2007-06-20
Ok I found the answer here :
[http://lists.debian.org/debian-dpkg/1998/06/msg00130.html](http://lists.debian.org/debian-dpkg/1998/06/msg00130.html)

I had to delete two files before running the script in terminal which repaired my system. 0015 and 0016. I knew that because after removing 0015, running the script would tell me that there was an error in 0016.
Then the script repaired update manager which is running without fault now.

---

