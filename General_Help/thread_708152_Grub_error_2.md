---
title: "Grub error 2"
date: 2008-02-26
forum: General Help
---

### Post by Tosa on 2008-02-26
So now I have grub error 2, and I couldn't find anything on it...

It all started weired. There were some updates couple of days ago, and when I rebooted I realized I didn't have sound any more.

After another reboot sound was there again! But, no more internet connection...

Another reboot, and after grub menu all I got was black screen. Two more reboots, the same.

Yet another reboot, just in case, and I got **grub error 2**.

Now what?

---

### Post by Tosa on 2008-02-27
Maybe I should change thread's name.
After booting with live CD I'd found out that /boot directory simply desapeared! In the mean time I've reinstalled Kubuntu, but why this happend?

---

### Post by redenex on 2008-02-28
Ironically I have the same error today! Someone help please? :popcorn:

---

### Post by Pekeh on 2008-02-28
That's weird ... i got the same problem and right now i have to use the live cd to use the computer D;

---

### Post by redenex on 2008-02-29
I ran ```
e2fsck -CO -f -v /dev/hda1
``` and Grub Error 2 is solved, but it is now giving me grub Error 15 :mad:

---

### Post by Sifilis on 2008-02-29
I get an Error 17 while the computer is booting, cannot enter nor Windows nor Ubuntu or even the Terminal in Ubuntu...

ooops, I found it..[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

