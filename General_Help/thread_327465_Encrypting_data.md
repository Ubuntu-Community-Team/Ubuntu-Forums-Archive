---
title: "Encrypting data"
date: 2006-12-29
forum: General Help
---

### Post by linuxbun on 2006-12-29
I have heard of many solutions, one I used to use was luks & cryptoloop back in the days that I used FC5.

I'm just wondering what the securest way is for ubuntu? I have a computer set with automatic login (it's locked in a safe so physical access is almost impossible) but just to be a bit more secure, I want to encrypt the data (through a fs loop if I remember correctly).

I'm hoping for something that will just allow me to mount this folder via terminal which prompts me for a password.

Any suggestions? What do you use? What's your personal favorite?

---

### Post by capitalistpiglet on 2006-12-29
i use encfs to encrypt data, it would do what you want mount the encrypted system to a directory from the terminal.
The main problem with security is the passphrase you use, obviously a easily guessable phrase like password. Go for a long random string of characters.

---

