---
title: "Can't shut down laptop and 'suspend' causes crash."
date: 2016-05-10
forum: General Help
---

### Post by Laura_Nbl on 2016-05-10
Hi

I have an Acer E5-511-P7AT on which I am running Xenial. The problem is that I can't shut it down. A shut down will cause it to re-start and closing the laptop lid or manually suspending it will cause it to crash (black screen, fan whirring, needing to hard reboot). The crashes used to be random but that problem was solved: [http://ubuntuforums.org/showthread.php?t=2323265](http://ubuntuforums.org/showthread.php?t=2323265)

Apparently many people have the same problem, but their solutions don't work for me.

This thread contains all three options I have tried so far: BIOS, GRUB and Laptop-mode-tools.
[http://askubuntu.com/questions/452750/reboot-after-shutdown-ubuntu-14-04-also-12-04-dell-latitude-e7440](http://askubuntu.com/questions/452750/reboot-after-shutdown-ubuntu-14-04-also-12-04-dell-latitude-e7440)

However, like the one answer said, I also had to skip step 2 of the GRUB option.

Any ideas? Because right now, I have to shut down my computer every night by waiting until it shut down and then quickly closing the lid before it can reboot...

---

### Post by Bucky Ball on 2016-05-10
Rather than acpi=force, try acpi=off then 

```
sudo update-grub
```

... then reboot.

Fun reminder: after making changes to the grub, of course you ran this command on previous attempts. Without doing so, any changes you make to /etc/default/grub are lost on reboot. Just in case ... ;)

* While I think of it, what happens with:

```
sudo shutdown -h now 
```

? That might put an end to the nightly shutdown saga.

---

### Post by Laura_Nbl on 2016-05-10
Didn't work :(. Also, yes, I updated grub after my other attempts :). ```
sudo shutdown -h now
``` does the same thing as 'shutdown'.

Oh, and my BIOS doesn't have a 'wake on lan' option to disable.

---

### Post by Laura_Nbl on 2016-09-20
Hi, So I know this thread is old but I thought I'd tell you that one of the recent updates fixed the issues. I can now shut down and suspend my laptop without any problems :).

---

### Post by Bucky Ball on 2016-09-20
Great news and thanks for marking as solved. 

Good luck. :)

---

