---
title: "Create ram disk"
date: 2013-06-14
forum: General Help
---

### Post by nicvan on 2013-06-14
Hi

i've recently managed to setup a ramdisk on my windows machine to speed things up a little. 
So i've tried to do the same on my laptop which runs ubuntu 13.04. but i haven't found anything that worked. 
I would like to storage all the temporary files, on the ramdisk.
  
i'm pretty new to ubuntu so i pretty much don't what im doing. :) :)

Any help is appreciated.

---

### Post by Vitsliputsli on 2013-06-14
For example, string from my /etc/fstab:
```
tmpfs     /tmp     tmpfs     rw,size=128M     0     0
```
it's mount into /tmp ramdisk with 128M.

---

### Post by Cheesemill on 2013-06-14
For temporary application files you can do this...
[http://www.itworld.com/data-centerservers/306676/use-tmpfs-make-ubuntu-1210-faster](http://www.itworld.com/data-centerservers/306676/use-tmpfs-make-ubuntu-1210-faster)
It's written for 12.10 but the procedure is exactly the same for 13.04.

This only affects files that are created in the /tmp directory so you probably wont see much difference, on my machine at the moment there are only around 20MB of files in the /tmp directory and it's been running for days. You'll get more of a noticable speed increase by moving your browser profile to RAM as this will drastically improve the response of your browser. This can be done by following the directions on this page.
[http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html](http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html)

---

### Post by nicvan on 2013-06-14
seems to work vitsliputsli

I'll definitely give it a try with the browser cheesemill (:

Is it possible to create a separate drive for example a svn checkout ? (:

And what can i do, if i want to use it for the output from compilers ? (:

---

### Post by Vitsliputsli on 2013-06-17
I haven't use SVN on Linux, but ram-disk have no difference with real almost. Must work.

---

### Post by varunendra on 2013-06-17
Doesn't Ubuntu already have a ramdisk mounted as /run/shm ?

It is half the size of installed RAM as far as I know. On my laptop with 4GB RAM, its size is 2GB and I keep using it all the time.

You can create a shortcut to it in your home (like I have done) for easy access.

---

### Post by HermanAB on 2013-06-17
tmpfs is a RAMdisk

---

### Post by nicvan on 2013-06-18
> **varunendra said:**
> Doesn't Ubuntu already have a ramdisk mounted as /run/shm ?

It does, arrh i should have seen that, thanks :D ! - actually all i needed to know :D

---

### Post by varunendra on 2013-06-18
> **nicvan said:**
> It does, arrh i should have seen that, thanks :D ! - actually all i needed to know :D
Yeah, it was a revelation for me too when I recently found it ! :)

Enjoy!!

Oh, and please consider marking the thread as **[Solved]** now, as it would help others with similar questions. :)

---

