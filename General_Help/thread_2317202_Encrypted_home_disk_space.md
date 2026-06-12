---
title: "Encrypted /home disk space"
date: 2016-03-14
forum: General Help
---

### Post by jim_deadlock on 2016-03-14
As I understand it, when a user logs in to an encrypted account the whole home directory for that user is decrypted and copied to disk, then when he logs out the .ecryptfs directory is updated and the (plain) home directory is emptied, it that right? So I would need to allow for twice the amount of space that I would for an unencrypted home if I only have one main user?

---

### Post by HermanAB on 2016-03-14
No, fortunately it doesn't work like that.  Files are decrypted on the fly as you access them.  The only thing kept in RAM is the key and a file buffer.  Therefore an encrypted file system doesn't use more space than a plain text file system.

---

### Post by jim_deadlock on 2016-03-14
Excellent thanks. I had a feeling my post was a bit dim-witted as I wrote it :redface:

---

