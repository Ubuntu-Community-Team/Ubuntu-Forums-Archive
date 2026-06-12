---
title: "Problem Booting Up"
date: 2008-05-16
forum: General Help
---

### Post by MosMusy on 2008-05-16
Recently I've had trouble booting up. Everytime I attempt to boot up it goes to a command line and begins doing some stufff after a while of waiting and it doing similar things, I turned off the computer than turned it on again. Now where it reads "Grub is loading" there is an error 16 and it does not load the list of platforms. How do I fix this? I don't want to lose my work!

---

### Post by pmlxuser on 2008-05-16
There might have been an error in the Boot sector (Grub), try reinstalling grub. if you dont know how to do it the foloowing thread will help you

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by pedro_orange on 2008-05-16
Hello,

I presume you have multiple operating systems on your machine.
I also presume that your MBR has got messed up. Probably from a partition not being unmounted incorrectly or something.

You could try re-installing the GRUB:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub)

Or you could try and boot from the LiveCD and check the partition with:

```
fsck
```

NB: To use Fsck you have to use it on unmounted drives :)

---

