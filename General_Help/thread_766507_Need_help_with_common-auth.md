---
title: "Need help with common-auth"
date: 2008-04-25
forum: General Help
---

### Post by Arne Christian on 2008-04-25
Hi

I was trying to install my fingerprint reader, but it was to unstable so i want to uninstall it.

I did the stupid thing and configured rules of PAM without bacuping the original data. ](*,)
I am running Ubuntu 8.04 x64

Can someone type "sudo gedit /etc/pam.d/common-auth" in their terminal and post the original file?

I just need the two lines in the bottom. I changed it to:

auth	sufficient	pam_fprint.so
auth	required	pam_unix.so nullok_secure

Tnx...

---

### Post by jespdj on 2008-04-25
Unstable, what do you mean, what problems do you get when you use it? I have one annoying problem when I login by swiping my finger: I get a prompt after logging in that nm-applet needs access to the GNOME keyring, and I have to type in my password to grant it access. Swiping doesn't work for that prompt. So I still have to type in my password, which is what I wanted to avoid... :roll:

Anyway, these are the original lines in common-auth:
```

auth    requisite    pam_unix.so nullok_secure
auth    optional     pam_smbpass.so migrate

```

---

### Post by Arne Christian on 2008-04-25
tnx...  this solved my problem :D

When i installed the fingerprint-reader the hole system started to act funny. Spesially when i tryed to install new programs. It did not ask fore any password or finger, but it just stopped, and it did not work to try to drag my finger..  But the fingerprint sensore is very cool, so i am going to try again, and this time im going to backup ;) hehe. Do you know of any other fingerprint program than fprint?

---

### Post by jespdj on 2008-04-25
I didn't know fprint, I use thinkfinger:
```
sudo apt-get install thinkfinger-tools libpam-thinkfinger
sudo tf-tool --acquire
sudo tf-tool --verify
```
See this: [https://wiki.ubuntu.com/ThinkFinger](https://wiki.ubuntu.com/ThinkFinger)

I filed a bug report for my problem, see [bug # 221900](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/221900).

---

### Post by j0rd on 2008-11-17
Here's the thinkfinger / keyring bug in launch pad. I already said my piece about it, please go in there and let them know how you feel and maybe we can move this bug forward.

[https://bugs.launchpad.net/gnome-keyring/+bug/276384](https://bugs.launchpad.net/gnome-keyring/+bug/276384)

---

