---
title: "How to emulate a file, that shows contents that are result of a script."
date: 2019-10-15
forum: General Help
---

### Post by syadnom on 2019-10-15
My google-fu is failing me.

I have a few stubborn pieces of software that read from a config file and I cannot modify the source.

I want to store the config in a database, and currently I'm do that and then pulling the config results into a config file and overwriting the existing.

What I'd like to do is have a virtual file that when read would run a script and return the results.

ie, cat /etc/config.file, triggers /scripts/getconfigfromsql.sh whos stout get's returned to cat.

---

### Post by HermanAB on 2019-10-15
Hmm, I think what you need is a FIFO.  It is a file system buffer that allows different processes to communicate.

man mkfifo:

mkfifo() makes a FIFO special file with name pathname. mode specifies the FIFO's permissions. It is modified by the process's umask in the usual way: the permissions of the created file are (mode & ~umask).

A FIFO special file is similar to a pipe, except that it is created in a different way. Instead of being an anonymous communications channel, a FIFO special file is entered into the file system by calling mkfifo().

Once you have created a FIFO special file in this way, any process can open it for reading or writing, in the same way as an ordinary file. However, it has to be open at both ends simultaneously before you can proceed to do any input or output operations on it. Opening a FIFO for reading normally blocks until some other process opens the same FIFO for writing, and vice versa. See fifo(7) for nonblocking handling of FIFO special files. 

A little googling on "linux fifo howto" or similar will get you going.

---

