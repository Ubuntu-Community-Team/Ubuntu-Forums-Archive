---
title: "bash strangeness"
date: 2008-03-10
forum: General Help
---

### Post by pjkoczan on 2008-03-10
So, I'm having a slight problem setting up my .bashrc at work. When I start up a new shell, it goes to my home directory, but it appears to expand the symlink, and that screws up my prompt. My home directory in /etc/passwd in /u/k/o/koczan, which is expanded to /afs/[cell]/u/k/o/koczan.

My question is this...is there a way to tell bash to not follow symlinks for new terminals? Or is there a way to detect a new terminal so that I can tell it to cd ~. Note that I don't want to do this for every new shell, just ones where I start up a new terminal. Sometimes I need to start up tcsh or get a shell with superpowers, so a blanket cd won't work.

The other issue is a little weirder. I connect via serial console to many machines, and I've been having a little problem with this regarding bash.

```

[koczan@ator] ~ $ ls
Desktop/  lab/  mail@  private/  public/  vmware/

[koczan@ator] ~ $ console vero
Attached to vero

Red Hat Enterprise Linux Server release 5.1 (Tikanga)
Kernel 2.6.18-53.1.13.el5PAE on an i686

vero login: [then I disconnect] 
[koczan@ator] ~ $ [koczan@ator] ~ $ [koczan@ator] ~ $ Desktop/  lab/  mail@  private/  public/  vmware/

```

I hit Enter, Enter, and then ran ls, it appears to lose input echoing. Anyone know what could be causing this and possibly how to fix or work around it? I know I could alias console to "tcsh; console; exit", but I was wondering if there's a more elegant solution.

I should note neither of these issues occur when using tcsh (the former issue exists but is not a problem since tcsh apparently follows symlinks better).

Thanks.

---

