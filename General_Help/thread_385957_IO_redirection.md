---
title: "I/O redirection"
date: 2007-03-16
forum: General Help
---

### Post by rafaelperrone on 2007-03-16
I was reading the Introduction to Linux guide from TLDP and i didn't undestand one art of the I/O redirection chapter. Hope you can clarify this to me:

It says:


"
ls > dirlist 2>&1

directs both standard output and standard error to the file dirlist, while the command

ls 2>&1 > dirlist

will only direct standard output to dirlist.


Why is that?

Thanks,

Rafael

---

### Post by Kalyan Manchikanti on 2007-03-16
The shell evaluates redirections basically from left-to right. 2>&1 means associate the file that is opened by file descriptor 1 (STDOUT), which in first case is what ever you specify after the ">"  to the file descriptor 2 ( STDERR)..

In the second case you don't have a file to associate 2 -STDERR to, as 2>&1 is your first argument.

---

### Post by rafaelperrone on 2007-03-16
I think I understood it. So the ampersand works just like the C programming language ampersand?

And then, in the second case, you just have STDOUT written to the file dirlist because &1 is not associated with any file yet, because its the first argument.

One more question, shouldn't it be written like 2> &1 (with the space between the > and the &1?

Thanks a lot, I couldnt figure it out on my own.

---

