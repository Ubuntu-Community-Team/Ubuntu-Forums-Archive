---
title: "Login process in console mode"
date: 2007-02-11
forum: General Help
---

### Post by blackd0t on 2007-02-11
Hi everyone!

Today I installed Ubuntu on my laptop and I wanted to change the login process to be only in console mode as I prefer it that way. I disable gdm, modified grub settings to disable quiet mode and the splash screen and it worked great. There is one thign though that bugs me and I have no idea why it's happening.

Just when scripts from rc2.d start being executed the login prompt appears :| The scripts produce some output information which appears right after the login prompt making it look really awful and eventually when all scripts finish their execution I am able to enter my username somewhere in the middle of the screen where the cursor stops after printing all script output.

Does anyone know why the login prompt doesn't appear only after all scripts finish execution?

Regards,
Black Dot

---

