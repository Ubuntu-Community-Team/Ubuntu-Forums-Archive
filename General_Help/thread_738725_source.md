---
title: "source"
date: 2008-03-28
forum: General Help
---

### Post by gaurdianAQ on 2008-03-28
hi just out of curiosity where can I get access to the Ubuntu source code I want to try a project for modding and learning how linux works and I want to see if I can create a version of linux based on ubuntu that can integrate with windows seamlessly or possibly where I can get the kernel source code

---

### Post by herbster on 2008-03-28
kernel.org

And have you tried Virtualbox/VMWare?

---

### Post by Joeb454 on 2008-03-28
I'm not sure exactly. And I don't think you can get the source entirely in one go.

I do know that using *apt-get source* allows you to get the source for a package though :)

---

### Post by gaurdianAQ on 2008-03-28
so Ubuntu does not offer the source code in a download only the iso?

---

### Post by lloyd_b on 2008-03-29
> **gaurdianAQ said:**
> so Ubuntu does not offer the source code in a download only the iso?

For a given package, "sudo apt-get source {package}" will retrieve the source for the associated package.

For kernel sources, "sudo apt-get source linux-image-2.6.24-12-generic" will retrieve the sources for the 2.6.24-12 kernel (Hardy) - for other kernels versions, substitute the correct version.

Note that these are installed into the current directory.

Lloyd B.

---

### Post by Bllasae on 2008-03-29
I believe that you can download it from the Ubuntu wiki. Under "building" or something like that.

---

### Post by gaurdianAQ on 2008-03-30
well this will come in handy once I get my system working

---

