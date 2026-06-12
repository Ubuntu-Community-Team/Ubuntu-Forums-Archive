---
title: "Broken pipe"
date: 2013-02-25
forum: General Help
---

### Post by sunfromhere on 2013-02-25
(Ubuntu 12.04)

Hello, I'm reading the book The Linux Command Line and while reading, I also try out things in terminal. One of the things was: set | less. Seems simple enough.

From the book:

The set command, when used without options or arguments, will display both the shell
and environment variables, as well as any defined shell functions. Unlike printenv,
its output is courteously sorted in alphabetical order.

I get the output in less, I can read it, everything seems normal, but upon quitting less, this shows in terminal:
**bash: set: write error: Broken pipe**

What gives?

---

### Post by Impavidus on 2013-02-25
The set command can generate a lot of output, 253774 bytes in my case. This is written into a finite buffer, which is read by less. Less only reads as much as it needs to show the first screen full. When the buffer is full, set is paused and therefore isn't terminated until you scroll down in less until you've seen most of the output. When you close less before set has terminated, the reading end of the pipe is destroyed. Set can no longer write to the pipe and is terminated by the broken pipe signal.

---

### Post by sunfromhere on 2013-02-25
So if I output it to a file, I shouldn't be getting this?

---

### Post by Impavidus on 2013-02-25
```

set >file.txt

```
That's how I found out it was 253774 bytes. And your broken pipe is reproduceable.

---

### Post by sunfromhere on 2013-02-25
250660 here :p

Thanks!

---

