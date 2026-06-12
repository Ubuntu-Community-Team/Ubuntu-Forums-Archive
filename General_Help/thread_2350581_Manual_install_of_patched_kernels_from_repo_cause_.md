---
title: "Manual install of patched kernels from repo cause boot failure"
date: 2017-01-25
forum: General Help
---

### Post by theWhirlyNerd on 2017-01-25
Issue: manually installing a specific kernel version from the repos in 16.10 (both Ubuntu and Xubuntu tested) causes boot failures when attempting to boot with that specific kernel

I have an Asus X205TA and I've been following the thread here: [https://ubuntuforums.org/showthread.php?t=2254322](https://ubuntuforums.org/showthread.php?t=2254322). We had an issue where a patched kernel (4.8.0-34) started causing the internal keyboard to become inoperable. I had 4.8.0-22 installed and the keyboard worked fine. Some others in the thread had -30 and -32 installed and said those two were working just fine. So I could test, I installed -30 and -32 using the following:

```
sudo apt install linux-image-4.8.0-32-generic linux-headers-4.8.0-32 linux-headers-4.8.0-32-generic
```

This is not a copy-paste, so it may not be exact... you get the point: installed linux-image and the headers for it. I also did this for -30.

When attempting to boot into either of those kernels, the Ubuntu splash screen hangs for a long time and eventually I'm dropped into a BusyBox initramfs prompt. This happened in both Ubuntu and Xubuntu 64-bit. I figured it was just another peculiarity of this pain-in-the-ass hardware, but I was able to replicate the same issue on my MacBook Pro 12,1. 

It looks like update-grub and update-initramfs are running fine. I even ran them again manually for the heck of it. It also appears that apt is doing its job because it's marking the -22 packages for removal (though I did not remove them). 

Booting from the two kernels that were installed during the fresh installation process (-22 and -34) still works just fine. 

Am I installing the other kernels wrong? Is there something up with 16.10 that is causing this?

---

### Post by &amp;KyT$0P# on 2017-01-25
Do you have [FONT=Courier New]linux-image-extra-4.8.0-32-generic[/FONT] installed?

---

### Post by theWhirlyNerd on 2017-01-25
I figured it had to be something simple... that fixed it on both machines. Thanks!

---

### Post by &amp;KyT$0P# on 2017-01-25
You're welcome!  :KS

---

