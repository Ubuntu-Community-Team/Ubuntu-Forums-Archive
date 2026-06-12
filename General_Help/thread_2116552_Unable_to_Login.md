---
title: "Unable to Login"
date: 2013-02-16
forum: General Help
---

### Post by HippoCrit on 2013-02-16
I installed Ubuntu via Wubi onto my PC, everything was working fine until I ran out of space, so I created a new larger .disk and transfered all my stuff into that, swapped it with my old one, then I can't login. It will take me to a black screen then back to the login page. The Guest Session works, that's what I am in right now. I tried to fix it using the following help:

> On Login Screen Press Ctrl-Alt-F1, login and type the following
sudo mv ~/.Xuathority ~/.Xauthority.backup
sudo service lightdm restart
Then press Ctrl-Alt-F7 to get back to the login screen

Problem was, when I use Ctrl-Alt-F1 or Any between F1 - F6, I just get a blank black screen where I can't do anything.

I'd really appreciate it if you give me some help.

---

### Post by HippoCrit on 2013-02-16
Any Ideas? Really need help with this

---

### Post by steeldriver on 2013-02-16
If you can't use the Ctrl-Alt-Fn virtual terminals, then you can boot into recovery mode instead - check the ownership and permissions on both the 'authority' files AND your user's home dir

```

# ls -ld /home/username
# ls -l /home/username/.{ICE,X}authority

```You will probably need to remount the root filesystem with write permissions if anything needs fixing:

```
# mount -o remount,rw /
```

---

### Post by HippoCrit on 2013-02-16
I managed to solve my problem. I wiped the .disk, then I re-copied everything, and then presto! It worked.

---

