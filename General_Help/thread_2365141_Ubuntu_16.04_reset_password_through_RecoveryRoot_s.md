---
title: "Ubuntu 16.04 reset password through Recovery/Root shell but could not login"
date: 2017-07-03
forum: General Help
---

### Post by kagashe on 2017-07-03
It is strange that I forgot the Ubuntu Login password which I used for 12 years.

In order to reset the password I boot into Recovery/Root shell and used:
```
# passwd username
```

to reset the password but I could not login.

My Laptop is Single user system hence Sudo password is same.

I also deleted files in ~/.local/share/keyrings folder.

Please help.

Kamalakar

---

### Post by TheFu on 2017-07-03
Did you also mount / with a chroot before changing your password? Otherwise, you are changing the password for under the live-boot environment, not the environment normally booted where /etc/password and /etc/shadow are.

---

### Post by kagashe on 2017-07-03
> **TheFu said:**
> Did you also mount / with a chroot before changing your password? Otherwise, you are changing the password for under the live-boot environment, not the environment normally booted where /etc/password and /etc/shadow are.
I did not boot into Live environment.

I boot into Ubuntu 16.04 Advance Options/Recovery Mode which is Ubuntu 16.04 itself and there is no need to mount anything.
But I found that / was mounted ro so I remounted it:
```
#mount -o remount /
```
and reset the password:
```
# passwd username
```

Now the password has been reset.

Kamalakar

---

### Post by TheFu on 2017-07-03
What do you mean it didn't work? What was the error?

Please copy/paste the password change command and output.  You can use redirection to save it to a file since a mouse isn't available.  I would use **tee**.

---

### Post by kagashe on 2017-07-03
> **TheFu said:**
> What do you mean it didn't work? What was the error?

Please copy/paste the password change command and output.  You can use redirection to save it to a file since a mouse isn't available.  I would use **tee**.

I could not login with the changed password.

Anyway the thread is marked SOLVED now since I tried again after remounting / as written in the reply above.

Kamalakar

---

### Post by ajgreeny on 2017-07-03
Recovery mode has mounted the root partition as read only for a few Ubuntu versions now and this has meant that the remount command has been needed to reset the user sudo password since that time.

If you can boot to recovery mode and do what kagashe has done it is a lot easier than using a live system and chroot.

---

