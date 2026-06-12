---
title: "Ubuntu server 12.04: Load fallback graphics devices Fail"
date: 2013-04-02
forum: General Help
---

### Post by tatatiti on 2013-04-02
Hi everyone,

I'm installing Ubuntu server 12.04 DomU on Xen.
But I have the error: 
>  * Starting load fallback graphics devices                               [fail]

at boot.

This is not a big problem, because the system is functioning, but it's some dirty.

I don't need a graphical environment, because this is a server usage. I'm connecting via SSH and use the prompt.

So there is a way to resolve or disable this error?

I'm french, so I'll hope you understand my english.

Thanks & Best Regards

---

### Post by tatatiti on 2013-04-03
I've deleted /etc/init/udev-fallback-graphics.conf
Is this bad?

---

