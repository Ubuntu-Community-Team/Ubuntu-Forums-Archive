---
title: "Compiling kernel from source"
date: 2008-04-05
forum: General Help
---

### Post by nick_d on 2008-04-05
hi all,

I'm a newby to Ubuntu, while it is installing I have been trying to absorb the documentation as far as possible, one thing I've been unable to find is any instructions on compiling a kernel from source and/or obtaining the default kernel configuration files used by Ubuntu.  Am I missing something?  Links to documentation would be appreciated, or any general comments that might help me get started.

I have been able to make customised kernels under Red Hat and Gentoo so it's not that I'm a total novice, I just need a bit of a push in the right direction...many thanks.

cheers, Nick
PS. If you could tell me where to find/install the scripts that build the necessary initrd files that would also be appreciated.

---

### Post by brian_p on 2008-04-05
> **nick_d said:**
> hi all,

I'm a newby to Ubuntu, while it is installing I have been trying to absorb the documentation as far as possible, one thing I've been unable to find is any instructions on compiling a kernel from source and/or obtaining the default kernel configuration files used by Ubuntu.  Am I missing something?  Links to documentation would be appreciated, or any general comments that might help me get started.

I have been able to make customised kernels under Red Hat and Gentoo so it's not that I'm a total novice, I just need a bit of a push in the right direction...many thanks.

cheers, Nick
PS. If you could tell me where to find/install the scripts that build the necessary initrd files that would also be appreciated.

Install kernel-package. It's all you need. Unless you do not want to it the Debian way.

---

### Post by dstew on 2008-04-05
Here is the basic instruction document for compiling custom Ubuntu-type kernels: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by brian_p on 2008-04-05
> **dstew said:**
> Here is the basic instruction document for compiling custom Ubuntu-type kernels: [https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

A nice document. I've only ever used the 'Old-Fashioned' way.

---

### Post by SOULRiDER on 2008-04-05
Check out:
[http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

Remember, compiling the kernel is not an easy task so make sure you have another kernel to boot into if you dont add the proper hardware support in your new kernel.

---

### Post by nick_d on 2008-04-06
Great.  Thanks all for your comments.  I knew there must be some doco somewhere!
cheers, Nick

---

### Post by ramjet_1953 on 2008-04-06
You can download the very comprehensive book 'Linux Kernel in a Nutshell' by O'Reilly from here:

[http://www.kroah.com/lkn](http://www.kroah.com/lkn)

Regards,
Roger :cool:

---

### Post by SOULRiDER on 2008-04-06
> **ramjet_1953 said:**
> You can download the very comprehensive book 'Linux Kernel in a Nutshell' by O'Reilly from here:

[http://www.kroah.com/lkn](http://www.kroah.com/lkn)

Regards,
Roger :cool:

Thats so nice, a book under the CC license :)

---

