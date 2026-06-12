---
title: "Security  oriented note taking app?"
date: 2013-12-11
forum: General Help
---

### Post by gregory12 on 2013-12-11
Which of the notes app is the most security oriented? 
Like having AES256 encryption of the DB?

I see basket notes can put password on a note, but it's unclear what encryption that uses (if it's not just interface gimmick) and on top of that, it doesn't work for me :)
Nothing happens when i set a password.

---

### Post by tgalati4 on 2013-12-12
None of the common packages have it, but you could write a simple script to decrypt the database, open the application (say *zim*), then when you are finished, close the application and the script would continue by encrypting the database.  Send an email to the developers to include an encryption option.

---

### Post by gregory12 on 2013-12-12
yeah but in that case the program will need to be closed in order to sync the database with another device.
uh i can't believe there isn't security oriented note taking program
a lot of people store their credit card and other sensitive info in those

---

### Post by Irihapeti on 2013-12-12
You can set up something like zim so that the notebooks are kept in an encFS-encrypted area. You can sync the encrypted files while they are in use. I'm not sure, though, how well that would work if you're wanting to sync the files with an Android device.

---

### Post by cjhabs on 2013-12-12
I store my sensitive notes (using Zim Wiki) in a Truecrypt volume.

---

### Post by gregory12 on 2013-12-14
> **Irihapeti said:**
> You can set up something like zim so that the notebooks are kept in an encFS-encrypted area. You can sync the encrypted files while they are in use. I'm not sure, though, how well that would work if you're wanting to sync the files with an Android device.


yep, that seems to be viable option, thank you :)

---

