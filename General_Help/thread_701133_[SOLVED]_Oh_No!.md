---
title: "[SOLVED] Oh No!"
date: 2008-02-19
forum: General Help
---

### Post by baudday on 2008-02-19
Ok well it doesn't seem like it's a real big deal right now, I am able to still use everything, but I assume that I'm gonna have problems downloading and installing future updates.

I was transferring music, and my iPod is really annoying, and will randomly turn off when hooked up to the computer and mess up the program. I didn't know how to force quit, so I thought the whole system hung up, and just turned it off, forgetting I was updating in the background. Now I try to install updates and get an error message as soon as I open the updater. I ran the Synaptic thing and got this,

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

Can anyone help me out? I would really appreciate it.

---

### Post by p_quarles on 2008-02-19
One nice thing about *nix systems: the error messages are actually helpful. It took me a while to get used to this myself. 

Basically, you just need to do what it says. Run the following in the terminal:
```
sudo dpkg --configure -a
```
There's a chance that this won't completely fix the problem, but there are a few more things to try if it doesn't.

---

### Post by baudday on 2008-02-19
Man that's awesome, that's so easy. Thanks a lot for the help..

---

