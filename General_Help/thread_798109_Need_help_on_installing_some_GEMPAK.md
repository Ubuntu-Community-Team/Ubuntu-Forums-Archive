---
title: "Need help on installing some GEMPAK"
date: 2008-05-17
forum: General Help
---

### Post by Thunderman on 2008-05-17
I am trying to install a meteorology analysis program called GEMPAK.  I download the binary distro for 64 bit Linux OS, but I am totally lost as to what I need to do next in order to install it.  The instructions here:

[http://www.unidata.ucar.edu/software/gempak/GEMPAK/Install_GEMPAK.html](http://www.unidata.ucar.edu/software/gempak/GEMPAK/Install_GEMPAK.html)

is loosing me on installation from binary.

Thanks if anybody can help me out here :)

If this is in the wrong place let me know.

---

### Post by shirilover on 2008-05-18
Let's see, you state that you have downloaded the binary distribution.
So, follow step one by entering into a terminal
```

cd /path/to/distro/download
tar -xzvf disribution_name.tar.gz

```
This should extract the contents of the archive to a folder GEMPAKversion.
Then proceed to step 3, since you have a binary, and do the runtime configuration.

---

