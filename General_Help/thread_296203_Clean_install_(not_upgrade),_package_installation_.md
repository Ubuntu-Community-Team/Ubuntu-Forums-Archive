---
title: "Clean install (not upgrade), package installation hangs"
date: 2006-11-09
forum: General Help
---

### Post by CarinArr on 2006-11-09
I just did a clean install of Edgy on my work machine Friday.

Installed/configured LDAP to connect home directories/other bits and bobs, which works absolutely fine.

Now, I'm having problems with the package manager, I'm pretty sure it's not because of the LDAP stuff as the same procedure works fine for others with machines running edgy.

For example, I tried to install fluxbox, it hung at "Setting up fluxbox...". Eventually I had to kill it, and the package hadn't been set up completely. When I try to remove it it hangs at "Removing fluxbox...".

This is the case with other packages as well (i.e. sun-java5-* which are the only ones i've tried to install bar fluxbox).

It happens regardelss of whether i'm using synaptic/apt-get/aptitude/dpkg.

```
01. strace dpkg --purge fluxbox
02. 
03. ...
04. mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d19000
05. write(5, "#padding\n#padding\n#padding\n#padd"..., 4096) = 4096
06. write(5, "padding\n#padding\n#padding\n#paddi"..., 512) = 512
07. _llseek(5, 0, [0], SEEK_SET)            = 0
08. stat64("/var/lib/dpkg/info/fluxbox.postrm", {st_mode=S_IFREG|0755, st_size=854, ...}) = 0
09. clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7e2b6f8) = 9959
10. rt_sigaction(SIGQUIT, {SIG_IGN}, {SIG_DFL}, 8) = 0
11. rt_sigaction(SIGINT, {SIG_IGN}, {SIG_DFL}, 8) = 0
12. waitpid(9959,
13. 
14. ------------------------------
15. root      9959  0.0  0.0   1660   484 pts/2    S+   13:33   0:00 /bin/sh /var/lib/dpkg/info/fluxbox.postrm purge
```

Above shows where it hangs running strace, and what ps says it is waiting for.

Other strace output i've had says "resource unavailable" (though at the moment I can't seem to reproduce it so can't give any output)

If anyone can shed any light whatsoever at why things are messed up, please please let me know.

---

