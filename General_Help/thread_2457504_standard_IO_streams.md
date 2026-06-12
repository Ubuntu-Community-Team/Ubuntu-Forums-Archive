---
title: "standard I/O streams"
date: 2021-02-03
forum: General Help
---

### Post by jcdenton1995 on 2021-02-03
Hello all,

I'm a little confused by the concept of stdin, stdout, stderr and their file descriptors.

On the whole I understand but what I can't work out is this; if each process gets three streams when it's initialised, and by default they point to the controlling terminal, how is it that they are able to be represented by the file descriptors 0, 1 and 2?

I would think each stream for each individual process would need it's own file descriptor because they could connect to different terminals?

Are stdin, out and err basically three streams that are shared by multiple processes?

I hope that makes sense

---

### Post by The Cog on 2021-02-03
I found this - hope it helps. The file descriptor is local to a process, and somewhere, there is a lookup from the process's descriptor to the real file structure.
[https://en.wikipedia.org/wiki/File_descriptor](https://en.wikipedia.org/wiki/File_descriptor)

---

### Post by HermanAB on 2021-02-03
You can change the file descriptors - it doesn't have to be 0, 1 and 2.  By doing that, you can do quite complex things with IO streams.  

You can change the descriptors with the *exec* command for example.

See this: [https://wiki.bash-hackers.org/howto/redirection_tutorial](https://wiki.bash-hackers.org/howto/redirection_tutorial)

and maybe see serial port redirection described here:
[https://www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html](https://www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html)

---

### Post by jcdenton1995 on 2021-02-04
> **HermanAB said:**
> You can change the file descriptors - it doesn't have to be 0, 1 and 2.  By doing that, you can do quite complex things with IO streams.  

You can change the descriptors with the *exec* command for example.

See this: [https://wiki.bash-hackers.org/howto/redirection_tutorial](https://wiki.bash-hackers.org/howto/redirection_tutorial)

and maybe see serial port redirection described here:
[https://www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html](https://www.aeronetworks.ca/2015/10/reading-and-parsing-data-from-serial.html)

> **The Cog said:**
> I found this - hope it helps. The file descriptor is local to a process, and somewhere, there is a lookup from the process's descriptor to the real file structure.
[https://en.wikipedia.org/wiki/File_descriptor](https://en.wikipedia.org/wiki/File_descriptor)

Thanks to you both! what I now understand is that the terms stdin, stdout and stderr refer to the data streams themselves, and not the source / destination of those streams. All programs get three streams by default and because everything is handled like a file, each stream gets it's own file descriptor on a per process basis. 0 = stdin, 1 = stdout and 2= stderr. Your first link HermanAB probably does the best job of explaining it that I've seen anywhere on the web.

Thanks again to you both!

---

