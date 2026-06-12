---
title: "Login and password problem"
date: 2006-08-20
forum: General Help
---

### Post by soaring747 on 2006-08-20
I cannot logon. It says that the password or username is incorrect.

The problem started after I foolishly shut down Ubuntu manually when the startup files were loading. I couldn't gain access into root nor the user account I normally work in.

I tried to fix this problem by taking the advice of a password cracking expert not associated with Ubuntu. I used my live Slax CD (I also still have the Ubuntu version) to edit the /etc/shadows and /etc/shadows- files so that all and only the encrypted "x" password was blank. I assumed that this would solve the problem.

What should I do to regain entry at login?

---

### Post by baldy1324 on 2006-08-20
im not sure this would help but to change your password, restart your computer, and at the grub "prompt" type "e". this will change grub's boot paremeters, then add the word single at the end. when you boot you will be dumped into a single user mode where you can type passwd (username) and the type your new password. then restart the computer press e and get rid of the "single" on your grub entry. not boot into the entry and your password is changed.
hope that helped

---

### Post by soaring747 on 2006-08-20
Thank you, that solves my problem. I really appreciate the help.  :)

---

