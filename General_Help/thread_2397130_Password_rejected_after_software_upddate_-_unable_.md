---
title: "Password rejected after software upddate - unable to restore or reset password"
date: 2018-07-25
forum: General Help
---

### Post by lmart on 2018-07-25
**Problem:** Updated systems software, rebooted after installation, User #1 password not accepted, User #2 password accepted. User #2 cannot not access root.
**Environment:** Xubuntu 18.04 LTS; 2 users; only OS installed on computer HDD
**Attempts to recover User #1 password.**
[LIST=1]
[*]GRUB’s System Recovery Mode
[*]Manually edit GRUB’s options to enable root shell.
[*]Reset password from the Live CD
[*]
[/LIST]
**Results:** Mixed. Once or twice, User #1 password changed successfully. However, when re-booting the system, it did not work. So, back to square 1.

**Sources:**
[LIST]
[*][https://www.wikihow.com/Change-the-Root-Password-in-Linux](https://www.wikihow.com/Change-the-Root-Password-in-Linux)
[*][https://mintguide.org/system/248-reset-the-password-for-root-or-any-user-in-linux-mint.html](https://mintguide.org/system/248-reset-the-password-for-root-or-any-user-in-linux-mint.html)
[*][https://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](https://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)
[*]
[/LIST]

---

### Post by Impavidus on 2018-07-26
Does it tell you that the password is wrong, or are you simply returned to the login screen? In the latter case, the password is correct, but login fails for some reason. Many users confuse these issues.

Did you try the on-screen keyboard? It's possible something went wrong with your keyboard layout, so the password checked by the system is not the same password as you thought you typed. As you may have changed the password with an unknown keyboard layout, you can't be sure what the password currently is. You could try and reset the password to something that you know to work, that is, check beforehand that every key generates the character you expect.

---

### Post by lmart on 2018-07-26
Thank you for your reply.

I can log into User #2 without any problem.

On User #1 login, it rejects the password as wrong password.

Unfamiliar with on screen keyboard.

I attempted, in excess of 15 times, the 3 methods of resetting the password. None worked.

---

