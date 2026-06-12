---
title: "Finding startup files"
date: 2007-07-27
forum: General Help
---

### Post by carpetn on 2007-07-27
I'm studying the chapter on "Understanding System Initialization" in Wells's book on Linux sysadmin. The book says there should be a file /etc/inittab "that contains pointers to the scripts that init runs to initailze the Linux system services...." Wells's book uses Fedora, not Ubuntu.

On Feisty there is not such file. I have tried searching for it using the Nautilus search tool but it doesn't come up anywhere.

So my question is, where do I find this file (or its Ubuntu equiv) on my Feisty Fawn installation?

Also, is there some documentation somewhere that gives for Feisty the kind of information about startup processes that this chapter gives for Fedora?

Thanks.

Nailz

---

### Post by rotalever on 2007-07-27
There is the /etc/init.d directory containing all startup scripts. And there are /etc/rc* dirs for the different runlevels which contain symlinks to /etc/init.d
Did you search for that?

---

### Post by carpetn on 2007-07-27
Thanks for your reply.

I guess I was still at the stage of looking for the inittab file. I did look in /etc/init.d for that file. Should I take it that Ubuntu doesn't use that file? 

It looks like the various README files under /etc/init.d and /usr/share/doc/sysv-rc/ are the next thing for me to study.

Thanks again.

---

### Post by stylishpants on 2007-07-27
Your book won't apply to Ubuntu so much anymore.  Ubuntu has rewritten the init system over the last two releases.  The new init system is called upstart.     ( [http://upstart.ubuntu.com/](http://upstart.ubuntu.com/) )

On your Feisty Fawn system, you can learn about it from its main documentaion file:

    /usr/share/doc/upstart/README.Debian.gz


Upstart will respect the /etc/inittab file if you create it (as mentioned in the above file) but does not need or create it by default.  Ubuntu systems that were originally installed before Edgy Eft will all have this file.

---

