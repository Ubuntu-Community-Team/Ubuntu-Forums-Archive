---
title: "Disable runit"
date: 2007-05-12
forum: General Help
---

### Post by Dooley on 2007-05-12
Hey all,

I installed runit on my xubuntu system. Now I can even boot into my system anymore, not even in recovery mode. Is there anyway to remove runit from startup without booting into ubuntu?

Thanks in advance for any help, it's much appreciated!!

Dooley

---

### Post by taurus on 2007-05-12
You can boot your machine with the LiveCD, mount your / partition, and remove it from /etc/init.d.  Then, see if you can boot your machine from the harddrive now.

```
sudo fdisk -l
```

---

### Post by Dooley on 2007-05-12
I can't find runit in /etc/init.d but the error that comes up when I boot-up says there is problems with runit. 
I can't see the problem too cleary though the second the error comes up the booting process ends.

Any ideas?

---

### Post by taurus on 2007-05-12
Can you post the command from my previous reply?  Are you sure you looked at /etc/init.d on your harddrive, not from the LiveCD?

---

### Post by Dooley on 2007-05-12
No I'm definitely looking at my linux hard-drive. I wasn't actually using the live cd. I'm on my laptop and I don't have my cd drive with me, I'm using windows and can edit my partitions from there.

Is there anything I can do or will I have to wait for my cd drive?

---

### Post by Dooley on 2007-05-13
Has anyone got any ideas?

---

