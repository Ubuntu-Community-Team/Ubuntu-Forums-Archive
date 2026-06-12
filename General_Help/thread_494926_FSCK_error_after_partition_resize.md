---
title: "FSCK error after partition resize"
date: 2007-07-07
forum: General Help
---

### Post by caish5 on 2007-07-07
Hi all,

I just modified my HD to have just one partiton and a swap instead of two and a swap. Anyhow it all went well until i rebooted. Now i get and FSCK error every time i boot up. The log is like this.....

```

Log of fsck -C -R -A -a -f 
Sun Jul  8 02:58:05 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=8262bd04-e863-4705-bbaf-2ac727f38a02'

fsck died with exit status 8

Sun Jul  8 02:58:05 2007

Can anyone help me?
Thanks,
 Andy
----------------

```

---

### Post by atlfalcons866 on 2007-07-07
[http://ubuntuforums.org/showthread.php?t=291890](http://ubuntuforums.org/showthread.php?t=291890)

---

### Post by atlfalcons866 on 2007-07-07
not sure if it partition related only posted the link because that person had exit status 8

---

### Post by caish5 on 2007-07-07
Thanks that threrad sorted it for me.

Turned out my /etc/fstab was still mentioning the partition i removed!

---

