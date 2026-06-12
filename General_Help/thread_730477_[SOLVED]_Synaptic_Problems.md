---
title: "[SOLVED] Synaptic Problems"
date: 2008-03-20
forum: General Help
---

### Post by M4rotku on 2008-03-20
Whenever i try to start the Synaptic package manager I receive the following error message:

```
E: ERROR: could not create configuration directory /home/root/.synaptic - mkdir (2 No such file or directory)
```

Neither my Synaptic Package Manager, nor my Add/Remove Applications application, nor my Update Manager can install packages.

Can anyone tell me how to fix this? They were just working a couple days ago.

Much Thanks.

---

### Post by keratos on 2008-03-20
why is your /root directory on /home ??

That is the problem.

root user's directory is /root
"normal" users are under /home/<username>

---

### Post by keratos on 2008-03-20
> **keratos said:**
> why is your /root directory on /home ??

That is the problem.

root user's directory is /root
"normal" users are under /home/<username>

so since the last couple of days, you have obviously changed something.

---

### Post by M4rotku on 2008-03-20
That is a good question.  I didn't even realize that.  Okay, so... how do I fix it?

<------------------- Noob :confused:

---

