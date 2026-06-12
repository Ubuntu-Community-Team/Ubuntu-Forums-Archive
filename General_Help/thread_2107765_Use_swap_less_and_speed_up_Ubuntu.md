---
title: "Use swap less and speed up Ubuntu?"
date: 2013-01-22
forum: General Help
---

### Post by pretty_whistle on 2013-01-22
I have Ubuntu 12.04.

Can I do this to speed things up?

> Use swap less frequently. It will enable faster switching between applications:

sudo sysctl vm.swappiness=10

And edit /etc/sysctl.conf and add the line at the end of the file to set it automatically at boot time:

vm.swappiness=10

---

### Post by tgalati4 on 2013-01-22
Open a terminal, post the output of:

```
free
```

What processor are you running?

---

### Post by pretty_whistle on 2013-01-22
> **tgalati4 said:**
> Open a terminal, post the output of:

```
free
```

What processor are you running?
Processor?  How do I find that out?

---

### Post by pretty_whistle on 2013-01-22
I found it.  Processor info:

Dual Core AMD Athlon QL-62.

---

### Post by pretty_whistle on 2013-01-22
Output of free:

[IMG]http://i46.tinypic.com/301dc7n.png[/IMG]

---

### Post by mcduck on 2013-01-22
> **pretty_whistle said:**
> Output of free:


You have plenty of free memory, and are not using swap at all. Adjusting swappiness value wouldn't have any effect on your computer's performance.

---

### Post by pretty_whistle on 2013-01-22
> **mcduck said:**
> You have plenty of free memory, and are not using swap at all. Adjusting swappiness value wouldn't have any effect on your computer's performance.
Thanks.

That's what I thought.

---

### Post by tgalati4 on 2013-01-22
If the desktop manager response is too slow, then change desktop managers.  Try Linux Mint Mate 64-bit with a Live DVD and see if the response is any better.

I agree with the others, if you are not using swap, then changing swapiness is not going to have any effect.

---

