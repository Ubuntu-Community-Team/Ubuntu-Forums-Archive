---
title: "xubuntu NTFS read/write at boot"
date: 2007-09-01
forum: General Help
---

### Post by phillips321 on 2007-09-01
Hi guys,

using Xubuntu im trying to enable NTFS read/write support at boot

I'm using the guide from ubuntuguide.org


```
 How to mount Windows partitions (NTFS) on boot-up, and allow users read and write access

Warning: The software you will use is still in Beta. You should not enable it on production machines

    * Read #General Notes 

    * Enable universe. Read #How to apt-get the easy way (Synaptic) 

    * Applications -> Add/Remove -> search for 'NTFS', you should find NTFS Configuration Tool, install it. 

    * Applications -> System Tools -> NTFS Configuration Tool -> Enable Write Support (depending on your device internal/external) 

    * Further troubleshooting is listed at this comprehensive howto thread. 
```

The problem is i cant find the NTFS Configuration Tool as im using xfce.

Does anyone known the command so that i can run it from the terminal using gksu.

Cheers

---

### Post by merlinus on 2007-09-01
Open a terminal and enter:

```

sudo apt-get install ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

### Post by phillips321 on 2007-09-02
magic cheers for that

now works fine :)

---

### Post by merlinus on 2007-09-02
Glad to hear it.  Good luck!

-merlin

---

