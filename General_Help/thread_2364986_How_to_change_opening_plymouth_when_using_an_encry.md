---
title: "How to change opening plymouth when using an encrypted LVM"
date: 2017-06-30
forum: General Help
---

### Post by ronbu on 2017-06-30
I am using Lubuntu 16.04.  I would like to know how to change the opening plymouth when using an encrypted LVM.  I changed the closing plymouth from Lubuntu 16.04 to the C4C Lubuntu ReSpin plymouth.  But, even though I entered "sudo update-initramfs -u" after changing the closing plymouth, the opening plymouth is still the stock Lubuntu plymouth.

---

### Post by ronbu on 2017-07-28
I didn't have the plymouth in the right location before.  The user has to have the plymouth in /usr/share/plymouth/themes/*ubuntu_**flavor*-logo/  for update-alternatives to find it.  After I placed the plymouth and its corresponding .png in the right location and gave the right location in the plymouth for the image diriectory and the script file and then ran > 
sudo update-alternatives --config default.plymouth
sudo update-initramfs -u   I was able to successfully change the startup plymouth

---

### Post by sisco311 on 2017-07-28
Cool!

Thanks for posting the solution and marking this thread as solved.

---

