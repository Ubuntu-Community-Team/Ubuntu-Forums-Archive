---
title: "Why doesn't &quot;nice +n &lt;cmd&gt;&quot; work in ubuntu?"
date: 2007-08-17
forum: General Help
---

### Post by Sporkman on 2007-08-17
Last night I tried to run a program using "nice +5", but it said nice "wasn't installed, so I ran sudo apt-get install nice, and it installed something, but then nice still wasn't recognized.

Nice works on Solaris & Fedora, why not on Ubuntu? Is there another way to run programs at a lower priority (when invoking the command)?

---

### Post by Mogurijin on 2007-08-17
This strange, I've had no problems running nice. I've used it mainly with Wine to run it at a higher priority such as nice -15 wine program.exe. I'm not sure what your problem is :P. But what version of Ubuntu are you using, I don't know if it would make a difference, but I'm using 7.04 Feisty Fawn.

---

### Post by Sporkman on 2007-08-17
> **Mogurijin said:**
> This strange, I've had no problems running nice. I've used it mainly with Wine to run it at a higher priority such as nice -15 wine program.exe. I'm not sure what your problem is :P. But what version of Ubuntu are you using, I don't know if it would make a difference, but I'm using 7.04 Feisty Fawn.

Same here - 7.04. Is there a special package I have to install?

---

### Post by Mogurijin on 2007-08-17
I didn't have to. Also what exactly are you putting into the terminal, maybe you have a slight syntax problem?

---

### Post by Sporkman on 2007-08-17
> **Mogurijin said:**
> I didn't have to. Also what exactly are you putting into the terminal, maybe you have a slight syntax problem?

Possibly - I'll try it again when I get home. Normally I'd type something like:

nice +5 ./myexecprog

---

### Post by Mogurijin on 2007-08-17
I don't exactly see anything wrong (I don't know about the ./). Like I said, stuff like nice -15 wine program.exe work fine for me :?

---

### Post by tszanon on 2007-08-17
Isn't it
```
nice -n NN <program>
```
? That's what I use in Dapper.

---

### Post by Sporkman on 2007-08-17
> **tszanon said:**
> Isn't it
```
nice -n NN <program>
```
? That's what I use in Dapper.

Not in Solaris & Fedora. I'll try that tonight.

---

### Post by Sporkman on 2007-08-17
> **tszanon said:**
> Isn't it
```
nice -n NN <program>
```
? That's what I use in Dapper.

Ah - that was the problem. Works now, thanks! 8)

---

### Post by tszanon on 2007-08-17
You're welcome. :)

---

