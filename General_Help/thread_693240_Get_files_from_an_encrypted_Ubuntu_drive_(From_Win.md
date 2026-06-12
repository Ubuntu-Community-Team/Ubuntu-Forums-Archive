---
title: "Get files from an encrypted Ubuntu drive (From Windows)"
date: 2008-02-10
forum: General Help
---

### Post by sirchmeister on 2008-02-10
I have a 500 GB Seagate IDE drive that has full system encryption and I have this drive installed in a new PC which only includes Windows. I am not looking for any other method other than to access these files directly from Windows itself. I installed ext2-fs for Windows but as this is an encrypted drive what else do I need to do (including accessing my Home directory) to get my files while inside Windows?

---

### Post by Biggus on 2008-02-11
How is it encrypted?

If it's done using a bit of software like Truecrypt or something, then all you have to do is to install that software in windows, enter the key, and you can acess your files that way.

---

### Post by randy78 on 2008-02-11
> **sirchmeister said:**
> I have a 500 GB Seagate IDE drive that has full system encryption and I have this drive installed in a new PC which only includes Windows. I am not looking for any other method other than to access these files directly from Windows itself. I installed ext2-fs for Windows but as this is an encrypted drive what else do I need to do (including accessing my Home directory) to get my files while inside Windows?

If you used the Alternative Install media and chose LVM Encryption, then you will not be able to access your files because Windows will not recognize the filesystem or partition because of the encryption.

Some more information would help us diagnose and possibly provide a workaround for you.

How is the drive encrypted?

Good Luck

---

### Post by sirchmeister on 2008-02-11
Yes I used the Alternate install CD with LVM encryption. I do understand that by default Windows cannot access it and that is basically the point of this thread. I was wondering if a tool exists to retrieve files from a HD encrypted in this manner from Windows.

---

### Post by randy78 on 2008-02-11
No tool exists that can pull data from an encrypted LVM and decrypt it... Well, not for the general public anyways ;)

Your only hope is to decrypt the drive, but I'm not sure if you can do that with the LVM encryption...

Good luck:)

---

