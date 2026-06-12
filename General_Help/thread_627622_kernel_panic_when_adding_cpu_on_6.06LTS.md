---
title: "kernel panic when adding cpu on 6.06LTS"
date: 2007-11-30
forum: General Help
---

### Post by hogz on 2007-11-30
hello.

i am trying to add a second opteron 2218 cpu to a dual socket system.  the OS was installed with only 1 cpu present.  after installing the second cpu I am getting a kernel panic during the boot process.  the new cpu shows up correctly in the bios.

Linux db1 2.6.15-29-amd64-server #1 SMP Wed Aug 29 14:03:12 UTC 2007 x86_64 GNU/Linux

any ideas would be most appreciated.

---

### Post by elctb on 2007-11-30
The linux kernel needs to have support for multiple cpus. If the installed kernel doesn't have support for multiple cpus, I would think the second cpu could step over the first cpu and cause all kind of problems.

See if you can boot up off the live cd and check if the kernel installed in the hard drive has smp support.
Look in /boot for a file like config-<kernel-version> and search for SMP.

Also, post the kernel panic information you are getting, at least  the description off the panic, don't bother with all the hex dump.

---

### Post by hogz on 2007-11-30
thanks for the response.  i believe it does have SMP...as you see in my first post SMP is reported from uname.  if that isn't correct i can test from the livecd.

---

### Post by hogz on 2007-11-30
also in /boot/config-2.6.15-29-amd64-server the following line is present...

CONFIG_SMP=y

---

