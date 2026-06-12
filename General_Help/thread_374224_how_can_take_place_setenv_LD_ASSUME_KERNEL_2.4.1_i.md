---
title: "how can take place setenv LD_ASSUME_KERNEL 2.4.1 in ubuntu"
date: 2007-03-02
forum: General Help
---

### Post by petersky on 2007-03-02
In red hat , I can write setenv LD_ASSUME_KERNEL 2.4.1 to change the vision of the kernel, how can I do the same thing in the ubuntu. It seems there are not setenv and LD_ASSUME_KERNEL in ubuntu.
Thanks.

---

### Post by slumcat05 on 2007-03-05
Try this:

```
export LD_ASSUME_KERNEL=2.4.1
```

I'm no expert, but from what I've read this is the equivalent bash command. Be cautious though, I have read that setting this option is a bad idea and can mess up some programs. I'm not sure on the details, but you should do some research on it.

---

