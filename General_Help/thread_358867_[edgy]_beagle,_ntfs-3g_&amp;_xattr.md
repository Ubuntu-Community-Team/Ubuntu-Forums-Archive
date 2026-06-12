---
title: "[edgy] beagle, ntfs-3g &amp; xattr"
date: 2007-02-11
forum: General Help
---

### Post by A-1337 on 2007-02-11
Hello!
I use beagle and want to index huge ntfs volume. 
I know  its performance suffers greatly in case xattr ( filesystem exteded attributes?) is't used. On the ext3 partition its just "user_xattr" in the options section of /etc/fstab.
What should I do for ntfs-3g driver?

I've checked their docs and there they mention "streams_interface" paramenter and 
[q]If its set to xattr, then the
named data streams are mapped to xattrs and user can manipulate
them using {get,set}fattr utilities.[/q] 

Do I need only "streams_interface=xattr" instead user_xattr?

---

### Post by zukakog on 2007-03-29
::bump::

I can't get Beagle to index anything but my ext3 root partition.  It doesn't want to index my NFS connections, my xfs drives, or my NTFS drives.  Any suggestions?

---

### Post by dbera on 2007-04-01
You might want to follow this up in the beagle mailing list dashborach-hackers@... (the full address is in [http://beagle-project.org](http://beagle-project.org), I dont remember completely). They will most probably ask you for ~/.beagle/Log/current-Beagle log file

Did you add the other partitions to beagle via beagle-config or beagle-settings ?

---

### Post by zukakog on 2007-04-01
> **dbera said:**
> You might want to follow this up in the beagle mailing list dashborach-hackers@... (the full address is in [http://beagle-project.org](http://beagle-project.org), I dont remember completely). They will most probably ask you for ~/.beagle/Log/current-Beagle log file

Did you add the other partitions to beagle via beagle-config or beagle-settings ?
Thanks!  I forgot to add some paths to be indexed.  Still no luck with the NTFS drives, but I'm going to be transfering the stuff to a better FS anyway.

---

