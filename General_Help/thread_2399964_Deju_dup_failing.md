---
title: "Deju dup failing"
date: 2018-08-31
forum: General Help
---

### Post by Robbyx on 2018-08-31
I have the latest version of Backup installed on 18.04. It seems my auto backups are no longer happening, although they did in 16.04.

Do you have a way for me to correct for this message, that shows when the backup fails?

GPGError: GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: WARNING: "--no-use-agent" is an obsolete option - it has no effect
gpg: AES256 encrypted data
gpg: gcry_kdf_derive failed: Invalid data
gpg: encrypted with 1 passphrase
gpg: decryption failed: No secret key
===== End GnuPG log ====

---

### Post by Robbyx on 2018-09-06
Apologies for pushing for a reply, but I do not know how to resolve the backup failure. I am using 18.04 gnome. Since the upgrade I have not had successful deja dup backups. 


GPGError: GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: WARNING: "--no-use-agent" is an obsolete option - it has no effect
gpg: AES256 encrypted data
gpg: gcry_kdf_derive failed: Invalid data
gpg: encrypted with 1 passphrase
gpg: decryption failed: No secret key
===== End GnuPG log ====

---

### Post by #&amp;thj^% on 2018-09-06
I have no problems with backups but I use Grsync>>>But maybe this might help.
[https://superuser.com/questions/984977/duplicity-restore-failing-no-secret-key](https://superuser.com/questions/984977/duplicity-restore-failing-no-secret-key)
> gpg: decryption failed: No secret key
Good Luck

---

### Post by Robbyx on 2018-09-06
Thank you for your help. 

I did not find it easy to follow the comments in the links as I was getting increasingly uneasy about what parts I should follow, I took a gamble, by creating a new, empty,  destination folder.  When I started a manual backup i was immediately asked for a new pass phrase but decided not to encode.  I think the error report has gone!

---

