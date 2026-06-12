---
title: "uswsusp didn't install s2ram?"
date: 2007-11-17
forum: General Help
---

### Post by ResumeMan on 2007-11-17
This is kind of odd.

I was using uswsusp in my Feisty install per [this thread]("http://ubuntuforums.org/showthread.php?t=471855&highlight=suspend"). It worked better than the native install but somewhat imperfectly.

I recently did a Gutsy install to replace Feisty. The Gutsy suspend wasn't working so hot, so I installed uswsusp. But the command s2ram returns "command not found." Looking in my /sbin folder I see that the files s2disk and s2both are there, but there's no s2ram.

Has something changed with the uswsusp program? I tried installing it again but it just said already installed.

What am I missing???

Thanks!

---

### Post by albertlash on 2008-01-31
Same here, what gives? s2ram was my way to sleep! I just tried reinstalling it, but then got an error about not having swap setup. Hmm.

---

### Post by FuturePilot on 2008-01-31
Looks like they're working on another way to implement this
[https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238/comments/16]("https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238/comments/16")

---

### Post by saeid on 2008-05-26
see:
[https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238](https://bugs.launchpad.net/ubuntu/+source/uswsusp/+bug/134238)

---

