---
title: "RT2870 questions.. on my last leg here..."
date: 2008-04-08
forum: General Help
---

### Post by Brandnew70x7 on 2008-04-08
This is my third attempt at getting Ubuntu to work. I have the RT2870 drivers extracted and I can't figure out how to compile them... when I try make install I get dozens of errors.

I'm on AMD64 and I'm getting so aggrivated.. any help will be greatly appreciated...

(Obviously I don't have access to the internet so sudo apt get is out of the question. I do however have Mac OS 10.5.2, is it possible to compile from there and put it on linux?)

---

### Post by negora on 2008-04-25
Hi there:

I don't know if you're a novice like me, but the main problem compiling (at least in my case) came from the lack of certain libraries, specially those related to the Linux kernel, the kernel headers. These aren't installed by default, since they're supposed to be required only by people with certain experience who want to get the best binary from the source code. Obviously, by default, you don't know that until you search in the Internet a little.

You should install the pack called "build-essential" as it's a references pack which will install all the most common and needed libraries and tools for compiling. After doing this, I bet you won't have any problem to build your own KO driver. By the way, I guess you're speaking about the official Ralink source code...

But be aware that it will fail if you're using the last Ubuntu, since it includes a new kernel and the code from Ralink has to be updated yet. I recommend you to track this thread of the forum: [http://ubuntuforums.org/showthread.php?t=475847](http://ubuntuforums.org/showthread.php?t=475847) .

---

### Post by matthew.kent on 2008-05-06
Try [http://ubuntuforums.org/showpost.php?p=4808839](http://ubuntuforums.org/showpost.php?p=4808839) as well

---

