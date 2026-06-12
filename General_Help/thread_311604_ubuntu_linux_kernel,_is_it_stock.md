---
title: "ubuntu linux kernel, is it stock?"
date: 2006-12-03
forum: General Help
---

### Post by spip on 2006-12-03
Hello,

Are there any modifications made to the linux kernel packaged with an ubuntu distribution? Or is it a stock kernel?

On my drapper drake distro, uname -a shows:

[INDENT][INDENT]*Linux redhawk 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux*[/INDENT][/INDENT]

So am I to assume this is the unmodified kernel 2.6.15-23?

Thank you.
spip

---

### Post by zgornel on 2006-12-03
Ubuntu kernels are modified to improve performance and hardware support.

---

### Post by spip on 2006-12-03
Are there articles/discussions that cover the parts that have been modified? I can also look at the source, but I am interested in discussions detailing why the changes are thought to yield performance gains.

As for the improve hardware support, is it the kernel that is changed in order to achieve this, or rather the distribution packaged with additional drivers, detection tools, etc?

Thanks.

---

### Post by RAOF on 2006-12-03
New drivers, bugfixes, etc are backported from new kernel versions into the Ubuntu kernel.  I don't think the kernels are particularly changed to improve performance.  And the patches are mainly backports from newer kernels.

---

