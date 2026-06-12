---
title: "Forgotten password, can't get to Desktop"
date: 2020-11-18
forum: General Help
---

### Post by robert48 on 2020-11-18
Hello

A friend upgraded Ubuntu to 20.10 and was then presented with a login screen. He used to auto login and he has forgotten his password. Is there any way to reset the system password without having to completely re-install Ubuntu and lose all his Home content?

Many thanks
Robert

---

### Post by HermanAB on 2020-11-18
Boot into single user mode and reset the passwords.  

Google for "Ubuntu Single User Mode" for details.

---

### Post by grahammechanical on 2020-11-18
The login password would be the same as the password he used when using the terminal and prefixing commands with the word sudo. Now, tell us that your friend has never used terminal commands and never entered the sudo password in a terminal.

Even if we never use a terminal we sometimes have to give authorization to Software Updater when an update brings in a new Linux kernel. I may be wrong but I feell sure that we need to give authorization when upgrading from one version to another version of Ubuntu.

There is a way to set Ubuntu to autologin by getting a root shell prompt. At the Grub  menu select Advanced Options for Ubuntu. Then select a Linux kernel with recovery mode. At the recovery menu select Network. That will establish an Internet connection. It will also put the file system in read/write mode from read only. When back at the recovery menu select Root Shell prompt that will give you a terminal with root access. Be careful how you use this power.

type

```
nano /etc/gdm3/custom.conf
```

That will open the file custom.conf in a text editor. Now edit this line by removing the hash ( # )

> #  AutomaticLoginEnable = true

Now save the file by using ctrl + O to Write out. Then use ctrl + X to exit. Now, type exit again to get back to the recovery menu and select Resume to continue loading Ubuntu and with a bit of luck Ubuntu should autologin as before.

Regards

---

### Post by robert48 on 2020-11-18
Thanks HermanAB! Hole in one!

I have a tested method to change the pw following your advice. Should I post it or would it be too sensitive do you think?

---

### Post by robert48 on 2020-11-18
Hole in one for you too grahammechanical! He has never used a terminal and never updated since 17.10! I have moved since so maybe I should have kept a closer eye on him! All's well now, thank you.

---

### Post by DuckHook on 2020-11-18
> **robert48 said:**
> …Should I post it or would it be too sensitive do you think?
Please do *not* post your procedure. Forum policy prohibits posting of techniques for password cracking.

Re your friend's habits:

For general users, the ready ability to set automatic login is a curse. I have never agreed with it, but the devs have seen fit to implement it, so there's no point in my griping about it.

However, your friend's experience serves as an all too typical example of why it is such bad practice. It is an import of lousy widespread Windows security habits and has more downsides than merely forgetting ones password over time. It has further ramifications for practising lousy security hygiene, all of which are too complex to get into on this thread.

Your friend should disable automatic login now that s/he has recovered her/his password and start to cultivate better security hygiene. It starts with getting used to minor inconveniences like challenge/response for the sake of habituating her/himself to proper practice as s/he gets more proficient in Linux.

---

### Post by robert48 on 2020-11-18
I agree, I always use typed password every time I boot up. For me, any automated process is open to being hacked, the keyboard still remains a useful security device.

---

### Post by robert48 on 2020-11-20
FAO Grahammechanical

I have revisited your advice to take a note for the future. I found that when using your root shell approach I needed to enter the administrators password. Easy for me on my machine but in the context of this post would not work because the 'administrator' (my friend) had forgotten his password. Many thanks for your time regardless, just thought you might appreciate the feedback.

Best Regards

---

### Post by TheFu on 2020-11-20
The Redhat Admin test used to start at a machine without any login, so the first step in the test was to get into the OS without knowing any login or passwords. They didn't encrypt the OS on disk.

This skill is Admin 101 stuff.

---

### Post by Qassis on 2020-11-22
Step-by-Step HOWTO recover password: [https://www.osradar.com/access-single-user-mode-ubuntu-20-04/](https://www.osradar.com/access-single-user-mode-ubuntu-20-04/)  Hope it helps if not already fixed.

---

