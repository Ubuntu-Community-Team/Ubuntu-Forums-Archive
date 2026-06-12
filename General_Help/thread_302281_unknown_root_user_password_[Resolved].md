---
title: "unknown root user password [Resolved]"
date: 2006-11-18
forum: General Help
---

### Post by little cazy on 2006-11-18
umm...this might seem a little cazy but i forgot my root user password!
So i'm asking how do u change a root user password without knowing the root user password?!?!?!?!?!?
or find out the password!

---

### Post by Ramses de Norre on 2006-11-18
Boot up recovery mode and run "passwd".

---

### Post by little cazy on 2006-11-18
i'll try that

---

### Post by cantormath on 2006-11-18
> **little cazy said:**
> umm...this might seem a little cazy but i forgot my root user password!
So i'm asking how do u change a root user password without knowing the root user password?!?!?!?!?!?
or find out the password!

This is by far my favorite post.....

ubuntu does not have one by default.  If you want to add one, which is not recommended,
$ sudo passwd root
type your password, the one you used to install the os.
type new root password.
type it again
done.

If this is something you actually have done, and you just forgot,
use a live cd, mount the hda in question, chroot to the hda, and passwd as root, change root password, or set it, and reboot.

---

### Post by aysiu on 2006-11-18
As far as I know, you don't have a root password (not one you could possibly know, anyway) and can't log into the graphical user interface with it, either.

Why do you need a root user password, anyway?

---

### Post by K.Mandla on 2006-11-18
> **little cazy said:**
> umm...this might seem a little cazy but i forgot my root user password!
So i'm asking how do u change a root user password without knowing the root user password?!?!?!?!?!?
or find out the password!
If you mean the password for the account you used to install Ubuntu, you should be able to boot into recovery mode and change it with 

```
passwd name_of_the_account_with_the_lost_password
```
As far as changing the root password itself, if you really, really want to change it, [read this first]("https://help.ubuntu.com/community/RootSudo").

---

### Post by cantormath on 2006-11-18
> **aysiu said:**
> As far as I know, you don't have a root password (not one you could possibly know, anyway) and can't log into the graphical user interface with it, either.

Why do you need a root user password, anyway?

The root password is not set, but you can set one and you can, if you know what todo, login as root via GUI.

why? Probably because its the forbidden fruit in ubuntu systems....

---

### Post by aysiu on 2006-11-18
> **cantormath said:**
> The root password is not set, but you can set one and you can, if you know what todo, login as root via GUI.

why? Probably because its the forbidden fruit in ubuntu systems....
From what I've read, the root password is set, but to something random you couldn't possibly know, so it's essentially unset.

I know it can be set, and I know you can enable a GUI root login, but those are off by default in Ubuntu...

... and also completely unnecessary.

---

### Post by cantormath on 2006-11-18
> **aysiu said:**
> From what I've read, the root password is set, but to something random you couldn't possibly know, so it's essentially unset.

I know it can be set, and I know you can enable a GUI root login, but those are off by default in Ubuntu...

... and also completely unnecessary.

It would not be difficult to recover it from shadow file I would think....if it is set, but  I believe it is not, this is the first time I have heard it was actually set on install.

---

### Post by Ramses de Norre on 2006-11-18
It's set in /etc/shadow as '*', which stands for a kind of impossible password.

---

### Post by little cazy on 2006-11-18
thanz it work after using some of ur guy surrgestgens.
the reason y i forgot it was because i was ground from the computer
and my bro change my password.so when i changed it back it kind of mess up.
anyways, thanks

---

