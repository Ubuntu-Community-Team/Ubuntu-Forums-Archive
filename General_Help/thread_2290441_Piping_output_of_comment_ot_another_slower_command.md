---
title: "Piping output of comment ot another slower command ... does the second buffer?"
date: 2015-08-12
forum: General Help
---

### Post by cherva on 2015-08-12
Hello,
I have an interesting question.
If you have a program generating a lot of output ... lets say mysqldump.
And you pipe this output to the input of a zipping program, BUT that needs more time to compress the data.
For example if you have output of mysqldump of 1 Mb/s, but you zip with 500Kb/s.....
What will happen in such a situation ?
Will the second app throttle the first app ? Like the TCP window size option ?
Or the kernel will buffer it in ram ?
I have no idea :)

---

### Post by Topsiho on 2015-08-12
Interesting question.
Why don't you try this (and tell us about the results :) ) ...

Topsiho

---

### Post by Lars Noodén on 2015-08-13
I saw an article on this a while back but cannot find it again.  The manual page for [pipe](http://manpages.ubuntu.com/manpages/trusty/en/man7/pipe.7.html) tells that the writing process stops writing, getting blocked, until the reading process has read enough for a write to complete.

---

### Post by echotech2 on 2015-08-13
Wouldn't the zip program need to see the whole input file before zipping?

---

### Post by tgalati4 on 2015-08-13
Instead of using pipe, you could write a script that dumps the mysqldump to a file in /tmp then add a *sleep 30* and then start the zip on the /tmp file.  That gives you the advantage of having the intermediate file in /tmp so you can see the size, time, etc for troubleshooting.

In linux things generally work the way you expect, and sometimes in surprising ways.  BUT, with buffering, you have a lot of hardware elements in play and that can lead to unexpected behavior.

---

### Post by SeijiSensei on 2015-08-13
> **echotech2 said:**
> Wouldn't the zip program need to see the whole input file before zipping?
I don't know about zip, but gzip doesn't seem to require it.  "tar czvpf archive.tgz /path" creates two processes, a tar process and a gzip process, that appear to run simultaneously if I use top.

---

