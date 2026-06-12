---
title: "can not start desktop environment"
date: 2015-07-15
forum: General Help
---

### Post by anieruddha on 2015-07-15
Hi,

From last 2-3 days, I am getting error & not able to boot into desktop environment. Attach the screenshot for error


[ATTACH=CONFIG]263208[/ATTACH]

Thanks
Aniruddha

---

### Post by Bucky Ball on 2015-07-15
*Thread moved to **General Help**.*

For now. Looks like you might have a graphics issue. Did you install drivers or do an update? Please include all info about what you were doing prior to this happening and what, if anything, you have tried to fix it. Have you researched any of the errors? Have you tried doing what the output at the end of your screenshot asks you to?

Try that, then this if it doesn't work. Boot to the list of kernels (grub) and highlight the kernel you normally use. Type 'e' to edit it. Look for the kernel line. It ends in:

'quiet splash'

Or one or a combination of these two words. At the end, after a space, add 'nomodeset' so the end of that line looks like:

```
quiet splash nomodeset
```

Control+x then 'b', I think (see the bottom of that screen to be certain), to save and resume boot. Any luck?

PS: Are you actually using 10.04 LTS???

---

### Post by anieruddha on 2015-07-15
> **Bucky Ball said:**
> 

For now. Looks like you might have a graphics issue. Did you install drivers or do an update? Please include all info about what you were doing prior to this happening and what, if anything, you have tried to fix it. Have you researched any of the errors? Have you tried doing what the output at the end of your screenshot asks you to?


The problem I experienced yesterday first time, then after searching, I referred ```
http://askubuntu.com/questions/374889/ubuntu-hangs-after-starting-with-issue-pointer-to-flat-panel-invalid-message
``` and install nvidia drivers. In the log following error message

```

Building initial module for 4.0.0-040000-generic
ERROR (dkms apport): kernel package linux-headers-4.0.0-040000-generic is not supported
Error! Bad return status for module build on kernel: 4.0.0-040000-generic (x86_64)
Consult /var/lib/dkms/nvidia-304/304.125/build/make.log for more information.

```

> **Bucky Ball said:**
> 
Try that, then this if it doesn't work. Boot to the list of kernels (grub) and highlight the kernel you normally use. Type 'e' to edit it. Look for the kernel line. It ends in:

'quiet splash'

Or one or a combination of these two words. At the end, after a space, add 'nomodeset' so the end of that line looks like:


quite splash is already there.

> **Bucky Ball said:**
> 
PS: Are you actually using 10.04 LTS???
[/QUOTE]

No I am using 15.04 now. My profile had the old information. Updated that.

---

### Post by Bucky Ball on 2015-07-15
You didn't read the rest of my post. Yes, I know quiet splash is there. Reread the post. I want you to add 'nomodeset' to the end of the kernel line. That was the whole point of the post. How to do that is all explained in the last post.

---

