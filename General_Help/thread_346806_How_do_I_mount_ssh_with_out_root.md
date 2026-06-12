---
title: "How do I mount ssh with out root?"
date: 2007-01-26
forum: General Help
---

### Post by encompass on 2007-01-26
I am able to mount my ssh connection to a directory just fine and it seems to work great except that I can't do it as a normal user.
I do I get this little program to mount and unmount without access from sudo everytime... I need to use it for my website work that I do.
Thanks, 

Currently I use gnome's connect to server... but found it unrealiable for connections like this.

Oh yes... and the program I user is 

sshfs

Thanks,

---

### Post by Ramses de Norre on 2007-01-26
Add "user" to the option list in fstab.

---

### Post by encompass on 2007-01-26
Yeah... thanks for the pointer... I knew that one... I needed something a little more dinamic than that.  Little did I know that if I load the module to mount the partitions in then /etc/modules file.  It allows those kinds of mounts.  Kinda nice.  I like it alot!
Thanks none the less.

---

