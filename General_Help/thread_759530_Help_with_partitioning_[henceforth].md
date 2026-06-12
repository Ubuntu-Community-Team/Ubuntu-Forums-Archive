---
title: "Help with partitioning [henceforth]"
date: 2008-04-19
forum: General Help
---

### Post by iandravid on 2008-04-19
Hi. I made a big jump to fulltime Gutsy recently but made a big mistake when I was partitioning. I have a sizeable 250GB HDD, and for some stupid reason I can't remember now I didn't want all my personal data on one /home partition.

So I set it up like this:
/boot   -   100MB
/          -   20+GB
swap  -   ~2GB
/home  -  137+GB
and for the rest of the space, I set it to mount at /usr...about 80+GB.

For now, there's isn't a problem. I managed to save static backups of files I definitely don't intend to delete by opening that drive as root in nautilus. But my question is, if I upgrade distro from let's say Gutsy to Hardy, or if I install a new distro, will this /usr drive be affected/wiped?

Also, in future, what should I name a partition that I don't want as /home but want to keep personal documents inside?
Learning n00bie. Please help!

---

### Post by Thanoulis on 2008-04-19
I believe that your /usr directory will be affected...
As for the name of the mount point, try anything that isn't used by the Linux system...(as usr, lib, include, home, bin, etc)

---

