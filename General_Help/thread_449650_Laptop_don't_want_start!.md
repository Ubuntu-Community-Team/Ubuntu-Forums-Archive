---
title: "Laptop don't want start!"
date: 2007-05-20
forum: General Help
---

### Post by jprl12 on 2007-05-20
Hello,

[Yesterday, on the french forum, I ask some help for install the UVC driver.]("http://forum.ubuntu-fr.org/viewtopic.php?pid=939092#p939092") A user ask me to do some command, but now my laptop don't want start ...

These commands was :
```

& sudo ln -sf /bin/bash /bin/sh
& sudo ./installl.sh
& sudo ln -sf /bin/dash /bin/sh

```

And the errors is :
```

init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS main process (2551) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: Not a directory
init: rc-default main process (2552) terminated with status 255

```

I really like Ubuntu, but I hope that I will can see it again! I have some important documents on it for my job :S

Thanks,
Jean-Philippe

---

### Post by jimrz on 2007-05-20
> **jprl12 said:**
> Hello,

[Yesterday, on the french forum, I ask some help for install the UVC driver.]("http://forum.ubuntu-fr.org/viewtopic.php?pid=939092#p939092") A user ask me to do some command, but now my laptop don't want start ...

These commands was :
```

& sudo ln -sf /bin/bash /bin/sh
[COLOR="Red"]**& sudo ./installl.sh**[/COLOR]
& sudo ln -sf /bin/dash /bin/sh

```

And the errors is :
```

init: Unable to execute "/bin/sh" for rcS: Not a directory
init: rcS main process (2551) terminated with status 255
init: Unable to execute "/bin/sh" for rc-default: Not a directory
init: rc-default main process (2552) terminated with status 255

```

I really like Ubuntu, but I hope that I will can see it again! I have some important documents on it for my job :S

Thanks,
Jean-Philippe

sholdn't the above item, in red, read "./install.sh". that 3rd "l" looks like a typo. if so, you may be able to correct it by booting into recovery mode

---

### Post by jprl12 on 2007-05-20
I try to boot in recovery mode, but I have the same errors and I can't have a ssh access ...

---

### Post by jimrz on 2007-05-20
> **jprl12 said:**
> I try to boot in recovery mode, but I have the same errors and I can't have a ssh access ...

ouch ... maybe someone else might know a way, but sounds to me like you need to re-install. if you have a separate /home partition it will be less painful. if not, you can use the live cd to copy your important data to a different partion or drive (external?).

EDIT: or, before backup/re-install, you could try the live cd and try to mount your current ubuntu partition(s) and delete the above script and all references to it, then reboot and see if the problem persists.

---

### Post by jprl12 on 2007-05-22
Thanks for your suggestions ... I used the live CD for copy my important documents with a USB device and on another computer with my home network ...

I installed the new Ubuntu Feisty without any problems! But now, my /home is on another partition! Thank for this idea! And soon, I will have a USB external disk only for backup!

---

### Post by jimrz on 2007-05-22
> **jprl12 said:**
> Thanks for your suggestions ... I used the live CD for copy my important documents with a USB device and on another computer with my home network ...

I installed the new Ubuntu Feisty without any problems! But now, my /home is on another partition! Thank for this idea! And soon, I will have a USB external disk only for backup!

glad to hear you were able to save the important stuff

---

