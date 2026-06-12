---
title: "How to unlock the keyring on login?"
date: 2015-08-27
forum: General Help
---

### Post by wbmilleriii on 2015-08-27
How do I automatically unlock the keyring at login on my Lubuntu 14.04 system?

There are a lot of answers to this problem on this forum and askubuntu, but none are applicable to a 14.04 Lubuntu system - it appears that the Passwords and Keys dialog has changed significantly since those answers were supplied.  

SO - answers telling me to tick the box for "Unlock the keyring at login" in the Seahorse app do not work, because it is not there.
       answers telling me to tick the box on the "Unlock the keyring" dialog box to unlock it at login do not work, because it is not there
       auto-login was never set on this system, so that is not a contributor
       I do not want an answer that involves removing the keyring password entirely

How can this rather basic requirement be met on a Lubuntu 14.04 system?

---

### Post by CantankRus on 2015-08-27
Try adding...
```
eval $(gnome-keyring-daemon -s --components=pkcs11,secrets,ssh,gpg) &
```
to your autostart file.
I only have openbox session here.
I believe the file should be at **~/.config/lxsession/Lubuntu/autostart**

---

### Post by wbmilleriii on 2015-08-27
Thanks for your input, but unfortunately, it didn't work.  No errors were thrown as far as I could see, but I still got the Unlock Keyring dialog when I started a backup (I logged out and back in first).

---

### Post by CantankRus on 2015-08-27
Are you using default Lubuntu?
I thought this just worked with lightdm?

---

### Post by wbmilleriii on 2015-08-27
As usual, found the answer after I gave up and asked.

Per [this comment ]("https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/1034108/comments/11")on bugs.launchpad.net, you have to install `libpam-gnome-keyring`.  Then, the next time the **Unlock Keyring** dialog box is displayed, it will have the box to tick giving you the option of automatically unlocking it at login.  

Verified to work on my 64-bit Lubuntu 14.04 install.

---

