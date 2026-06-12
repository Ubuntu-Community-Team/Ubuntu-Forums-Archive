---
title: "PGP Problem"
date: 2008-05-30
forum: General Help
---

### Post by JohnSearle on 2008-05-30
Hello,

I recently encrypted a file, and then was forced to back up the file and format my system. I had encrypted it through KGpg, and I didn't think to bring the key along with the backup.

Being the neophyte that I am, I thought that as long as I had the password that went along with the encryption, I would be ok. Now it seems that it doesn't even ask me for a password, but rather it just states that I'm missing the key. Have I totally messed things up, and have now lost the information in the file? Does the password that I use have no real meaning without the key that went along with it?

I really don't know the mechanics behind this, so I apologize.

Thanks for any help,

-John

---

### Post by Monicker on 2008-05-30
If you encrypted it using your public key, then you definitely need the key pair.  The password is used for unlocking the private key, so that it can be used for decryption.   

Without the key pair you will not be able to decrypt the file at all.


EDIT: FYI - gpg does support encryption using just a passphrase without having to use the key pairs.  As long as you pick a good passphrase this is also secure.  

The main purpose of having a public/private key pair is so that people can encrypt things with your public key, and only you can decrypt it with your private key.  Hence the need for a strong passphrase to use the private key itself, to prevent somebody from being able to use it to decrypt your files/messages just by virtue of somehow obtaining the private key itself.  Private keys should always be kept secured.

---

### Post by JohnSearle on 2008-05-30
Very good, thanks.

Unfortunately that I essentially lost my data, though. I'll have to be a little more careful about my experimentation next time.

Thanks for the additional info on the password protect. I'll have to go find an article detailing those methods.

Cheers,

- John

---

### Post by lcpltyler on 2008-09-19
I have a similar problem I lost every thing from my last ubuntu failure which I caused. I didn't back up my encryption keyring and had encrypted files. I still have the encrypted files and know the original password is there a way i can un-encrypt it.

---

