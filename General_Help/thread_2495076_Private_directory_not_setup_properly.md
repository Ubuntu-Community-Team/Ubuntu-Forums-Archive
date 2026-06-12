---
title: "Private directory not setup properly"
date: 2024-02-06
forum: General Help
---

### Post by billyjimmyx on 2024-02-06
I've used recovery mode to reset a forgotten password and now that I'm logged in I've attempted to run the **ecryptfs**-**setup**-**private **script and it says that the private directory wasn't setup properly, is there any way I can fix this to gain access to my files?

---

### Post by #&amp;thj^% on 2024-02-06
You need to show what command you used with ecryptfs-setup-private
I use something like:
```
sudo ecryptfs-mount-private /home/.ecryptfs/<username>/.Private
```
And Please be sure to replace "<username>" with your real username

---

### Post by Holger_Gehrke on 2024-02-06
ecryptfs uses the login password to encrypt the key it uses to encrypt and decrypt  the data. After a 'normal' login it hooks itself into the functions to change the password so it will update the key when you change the password. When you reset a forgotten password from recovery boot, ecryptfs can't do that. You need your old password to decrypt the data or the 'unwrapped ecryptfs password'. If you have neither, then the encrypted data is probably lost.

Holger

---

### Post by loycekunze on 2024-02-12
Thanks for advice, I will try it and if I still face any issue, I will update you.

Edit: All good.

---

