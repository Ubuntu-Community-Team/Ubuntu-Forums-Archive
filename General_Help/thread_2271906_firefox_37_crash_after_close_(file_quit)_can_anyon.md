---
title: "firefox 37 crash after close (file quit) can anyone reproduce ?(14.10)"
date: 2015-04-02
forum: General Help
---

### Post by cosy2 on 2015-04-02
since i updated to version 37 i see that each time i want to restart firefox it crashes and i need to kill the process or wait for the crash report window to show up

i did disable all add-on and got the same problem even with all the add on disabled 

so in my opinion it was something between firefox and my system (maybe related gksu ? [http://ubuntuforums.org/showthread.php?t=2224760](http://ubuntuforums.org/showthread.php?t=2224760) )

I decided to remove:

```
xul-ext-ubufox
webaccounts-extension-common
xul-ext-webaccounts
```

this did remove the problem but i want to know why
can anyone tell me why and what was happening ?  

tia

---

### Post by dino99 on 2015-04-02
i'm using vivid i386 with gnome-shell
when i click on the firefox 37 icon, it first try to load but silently fails; FF36 was working fine, so 37 has an issue.

this is the terminal output:
[u32 1] ~ > firefox

(process:13728): GLib-CRITICAL **: g_slice_set_config: assertion 'sys_page_size == 0' failed
(but i also use the 3.16 gnome version packages from the staging ppa; so could be related to)

---

