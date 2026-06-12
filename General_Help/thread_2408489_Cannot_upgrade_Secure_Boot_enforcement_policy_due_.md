---
title: "Cannot upgrade Secure Boot enforcement policy due to unsigned kernels"
date: 2018-12-19
forum: General Help
---

### Post by jiapei100 on 2018-12-19
My issue is exactly as [https://lukasmestan.com/your-kernels-are-unsigned-this-system-will-fail-to-boot-in-a-secure-boot-environment/]("https://lukasmestan.com/your-kernels-are-unsigned-this-system-will-fail-to-boot-in-a-secure-boot-environment/") and [https://www.reddit.com/r/linux4noobs/comments/9a1382/grub_wont_update_since_my_kernel_is_unsigned_how/]("https://www.reddit.com/r/linux4noobs/comments/9a1382/grub_wont_update_since_my_kernel_is_unsigned_how/") .

I wonder if there is a possibility for me to remove an old signed/unsigned linux-image, while still running under the current unsigned linux-image?
BTW, I'm using 
```

&#10140;  ~ uname -r
4.19.10-041910-generic

```
which is manually downloaded and installed from [https://kernel.ubuntu.com/~kernel-ppa/mainline/]("https://kernel.ubuntu.com/~kernel-ppa/mainline/") .


Cheers
Pei

---

