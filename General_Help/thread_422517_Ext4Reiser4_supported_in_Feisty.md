---
title: "Ext4/Reiser4 supported in Feisty"
date: 2007-04-25
forum: General Help
---

### Post by zba78 on 2007-04-25
Does Feisty have support for Ext4 built into the kernel by default? What about support for ReiserFS 4?

---

### Post by Phineas on 2007-04-25
I do believe both are supported but neither are fully mature yet so they are not default options. You should be able to make a partition in those types and mount them in ubuntu.

Here is a thread discussing ext4: [http://ubuntuforums.org/showthread.php?t=293870](http://ubuntuforums.org/showthread.php?t=293870)

And here is a thread discussing Reiser4 from 2005: [http://ubuntuforums.org/showthread.php?t=87932](http://ubuntuforums.org/showthread.php?t=87932)

---

### Post by Computer Guru on 2007-04-27
No, I don't think you can.

You need to first install reiser4progs in order to make the reiser4 partition, but you can't mount it without recompiling the kernel.

:(

---

### Post by Sef on 2007-04-27
> Does Feisty have support for Ext4 built into the kernel by default?

It is not in the kernel yet.  It is being talked about being added, but when will it happen is not known now.

---

