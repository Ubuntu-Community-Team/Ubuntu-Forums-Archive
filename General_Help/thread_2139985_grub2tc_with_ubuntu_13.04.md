---
title: "grub2tc with ubuntu 13.04"
date: 2013-04-28
forum: General Help
---

### Post by BenWhitey on 2013-04-28
I just installed ubuntu 13.04 and encrypted my windows 7 partition with truecrypt. Now I'm trying to get grub2tc up and running. I was following the directions in the readme and I get an error. Does anyone have any experience with this?

```
b@b ~/...$ make
ruby extract.rb tcrescue.iso
make: ruby: Command not found
make: *** [tcloader] Error 127
```

Then it also doesn't make any files caled "tcloader." It makes tcloader.bin, tcloader.o, and tcloader.out but none of these files work when I move them to /bout and try to boot into windows.

And I am not making a hidden OS.

Thanks in advance

---

### Post by BenWhitey on 2013-04-30
Update: I was stupid and didn't realize that I hadn't installed ruby. I installed Ruby and it was able to build tcloader without errors. I put that onto the /boot and modified /etc/grub.d/40_custom as in the readme.

I was able to boot into the truecrypt bootloader but it says that my password is wrong. I tried over writing the keyfile and that didn't help. Any ideas?

---

