---
title: "groups cannot find random group IDs"
date: 2014-02-14
forum: General Help
---

### Post by krafczyk-matthew on 2014-02-14
Hi, some time ago I upgraded to 13.10 from 12.10. After the upgrade, I've been getting the following messages whenever I open a new terminal of any sort, using bash, I get the following message.

groups: cannot find name for group ID 1107158749

Now it's important to note that the group ID is different each time I restart my machine. I tried to create a temporary group thinking that it was linked to some program and that I'd figure out which later, but when I restart my machine, the missing ID changes. 

Another important note is that it only happens when using bash. If I use ksh, csh, tcsh, zsh, basically any other shell, this message doesn't pop up.

Any idea what this is?

---

### Post by krafczyk-matthew on 2014-02-15
bump

---

### Post by steeldriver on 2014-02-15
Someone here had a similar issue but it doesn't look like it was ever resolved --> [http://ubuntuforums.org/showthread.php?t=2198232](http://ubuntuforums.org/showthread.php?t=2198232)

Maybe something in your ~/.bashrc file? Happy to take a look if you post it. Or you could try invoking bash with --norc and/or --noprofile to try to narrow down if it's something in a system-wide startup file

```
bash --norc --noprofile
```

---

### Post by krafczyk-matthew on 2014-02-16
Thanks a lot for your response!

So, I tried bash --norc --noprofile, and the message didn't get printed.
I then tried bash --norc and the message didn't get printed. I then tried
bash --noprofile and the message was printed.

So like an idiot, I accidently just straight away deleted my .bashrc file. So I guess I can't trouble shoot that file exactly anymore.. HOWEVER the error still exists even if the bashrc file which is loaded is empty. very weird. Whats more is that the warning is printed if I execute

```
bash --rcfile /path/to/empty/file -ci "pwd"
```

but NOT if I execute

```
bash --rcfile /path/to/empty/file -c "pwd"
```

So I guess it's happening specifically when I use bash to have an interactive session which loads any kind of rc file even an empty rcfile.

Any ideas?

---

### Post by krafczyk-matthew on 2014-02-21
bump

---

