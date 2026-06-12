---
title: "How do I update my kernel to 2.6.25.8?"
date: 2008-06-22
forum: General Help
---

### Post by AaronMT on 2008-06-22
Hi all,

How do I update my kernel to 2.6.25.8?

I do a **uname -r** and my output is 

```
2.6.24-19-generic
```

I did do all the available updates but my kernel is still old, not sure why. 

How can I resolve this?

---

### Post by kdcoetzee on 2008-06-22
Your kernel is not old.

Debian/Ubuntu tend to release new updates when they are happy with the stability.

if your repository is correct and apt-get does not give you any updates to download then your system is up to date.

---

### Post by sdennie on 2008-06-22
Ubuntu kernels don't update to the latest kernel version but instead pick a version and keep it up to date with security updates and bug fixes.  If you want to use a newer kernel than what Ubuntu provides you'll have to compile it yourself.  You can either use a guide to do it by hand such as: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) or, you can try this utility: [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158).

Either way, I don't recommend building your own kernel unless you have specific problems that a newer kernel is certain to fix or there are certain features in the new kernel that you need.

---

### Post by drs305 on 2008-06-22
2.6.24-19-generic is the latest kernel in the normal repositories. More advanced kernels are being developed and are available but have not been released for download from the repositories. For the general user, waiting for a kernel to be tested and fully-approved by the ubuntu team is probably the best bet. 

If you absolutely have to get a later kernel, they may be accessible by enabling some of the repository settings in synaptic by ticking the PreRelease and Unsupported boxes. I don't recommend it - there are reasons they are labeled *unsupported* and *PRE-release*.

---

