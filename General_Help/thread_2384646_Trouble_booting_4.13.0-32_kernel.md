---
title: "Trouble booting 4.13.0-32 kernel"
date: 2018-02-09
forum: General Help
---

### Post by jcarey9149 on 2018-02-09
I'm running 17.10, and was recently updated to the 4.13.0-32 kernel.  When I restarted the computer, it hung at the splash screen.  I tried restarting it with the quiet and splash parameters removed, and tried rebooting.  There was a lot of text that flew by, but after a while it slowed down and I could read a message about  failing to connect to lvmetad and falling back to device scanning.

My system is configured with a logical volume, and luks.  It did not get as far as asking for the luks password.  I can boot into 4.13.0-31 from the hard drive with no issues, so I don't think the hard drive or the encryption is the problem.

I'm not sure how to go about debugging this.  I'm fairly competent with linux, but the boot process (especially with the encrypted drive) is not something I'm very familiar with.

Help would be very welcome.  Thanks in advance.
Jim

---

### Post by harterc2 on 2018-02-25
I am having similar problems.  initrd.img-4.13.0-26-generic will boot and initrd.img-4.13.0-32-generic  or newer kernel fails.  I even built the latest stable kernel, and it also failed.
When it fails the boot process drops to a shell.  I found that the shell did not have cryptsetup in it.  So I modified the initramfs-tools package to enable it and rebuilt some initrd images.  Why it is failing for me is that the partition is not getting decrypted so that lvm can recognize the vg.  It would then be mounted.  I also got messages about lvmetad failing.  It could not create the socket it needs in the standard directory (/run/lvm). A few times I was able to continue the boot process by manually running cryptsetup and exiting the shell.  I saw some posts with similar troubles caused by systemd.  Perhaps running debug (set -x) in one of the initramfs-tools scripts may help to determine what is happening. In a init-premount script I was seeing the lvmetad socket not found error.  I saw some other posts where the problem was fixed by loading modules dm-crypt and dm-mod which wer missing. I am not sure if it is related to this though.

---

### Post by wildmanne39 on 2018-02-25
Hello and welcome to the forums, please start your own thread instead of posting in someone else's so you can get the help you need and so can the person that started this one.

Thanks

---

