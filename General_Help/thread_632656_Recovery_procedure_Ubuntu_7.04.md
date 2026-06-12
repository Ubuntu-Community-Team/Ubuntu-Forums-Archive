---
title: "Recovery procedure Ubuntu 7.04"
date: 2007-12-05
forum: General Help
---

### Post by basilgunn on 2007-12-05
I seem to have hosed my system using Adept & adding a package. I think I was adding libc6-debug version but not completely sure. I was able to get most of my apps back with apt-get. I then rebooted my workstation & got "Error 15: File not found". So my question is:

Is there a way to do a non-destructive install of Ubuntu, that is, can I install just the operating system & leave my partitions and usr directory alone? Anybody have suggestions on recovery?

Thanks for any help.

/basil

---

### Post by mikewhatever on 2007-12-05
You should be able to recover from a backup, if there is one, or painlessly reinstall if your home is on a separate partition. You can theoretically have /usr on a separate partition if needed.

---

### Post by basilgunn on 2007-12-05
Thanks for the reply.
I can get to a root prompt by booting the kernel in recovery mode. It looks like my file systems are all mounted & apt-get seems to work.  I'm now trying to figure out if I can use apt-get to update my current version of Ubuntu 7.04 to refresh some files that appear to have gone missing. I'd prefer not to do a dist upgrade put that seems to be an option.

Is it possible to use apt-get to re-install the current version of  ubuntu without blowing away my /etc & other config?

/basil

---

