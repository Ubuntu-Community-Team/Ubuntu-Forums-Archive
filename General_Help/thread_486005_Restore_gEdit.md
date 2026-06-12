---
title: "Restore gEdit"
date: 2007-06-27
forum: General Help
---

### Post by tL0z on 2007-06-27
Hello,

I installed a config and a set of plugins but I don't like them. How can I restore gEdit to it's default state?

Thanks

---

### Post by tL0z on 2007-06-28
up

---

### Post by moore.bryan on 2007-06-28
[I]you could try 
```
sudo aptitude remove --purge gedit && sudo aptitude install gedit
```
[/I]

---

### Post by tL0z on 2007-06-29
It says that I have to remove ubuntu-desktop.

---

### Post by moore.bryan on 2007-06-29
*that's okay... ubuntu-desktop is often referred to as a "meta-package."  it really doesn't do anything, but it is dependent on everything.  if you're still leary, you can try ```
sudo aptitude reinstall gedit
```*

---

### Post by tL0z on 2007-06-29
The plugins are still there. Isn't there a way to remove them?

Thanks

---

### Post by p_quarles on 2007-06-29
> **tL0z said:**
> The plugins are still there. Isn't there a way to remove them?

Thanks
If you're using the set of plugins available in the repositories, then you can just type this ```

sudo apt-get remove gedit-plugins
```

---

