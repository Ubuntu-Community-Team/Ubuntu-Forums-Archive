---
title: "GNUPG 2.1.0 encrypt and decrypt syntax"
date: 2013-05-16
forum: General Help
---

### Post by hbhfit on 2013-05-16
Hi,

I saw this thread and it was closed so I decided to open a new thread.
[http://ubuntuforums.org/showthread.php?t=1510360](http://ubuntuforums.org/showthread.php?t=1510360)

I can't seem to find help with getting the syntax down for DEcrypting using GNUPG 2.1.0

What I'd like to do is create a one line command that has:
[LIST]
[*]the passphrase (so i don't need to deal with a dialog box ASKING for the passphrase)
[*]the drive path and exe name of the the GPG exe to be used
[*]the name of the output file (what the file will be named when it is DEcrypted)
[*]any other switches needed to get the job done
[*]the reference needed telling it what DEcrypt key to use
[*]the name of the ENcrypted file that we're going to DEcrypt
[/LIST]

Here's what Im using so far and it's not working:

DECRYPT:

    (passphrase) | drive:\path\gpg2.exe (--output DEcryptedFilename.txt) (--decrypt) (--always-trust) (-r [EMAIL="EmailAddressUsedToReferenceDEcrypt@Key.com"]EmailAddressUsedToReferenceDEcrypt@Key.com[/EMAIL]) (ENcryptedFileToBeDEcrypted.txt.gpg)


ENCRYPT:

   drive:\path\gpg2.exe (--output EncryptedFile.txt.gpg) (--encrypt) (--always-trust) (-r [EMAIL="EmailAddressUsedToReferenceDEcrypt@Key.com"]EmailAddressUsedToReferenceDEcrypt@Key.com[/EMAIL] ) (FileThatNeedsToBeENcrypted.txt)

I'm not stuck on any particular way / format for this command - I just need an EN and a DE crypt line of code that will do the job and for DEcrypt it has to pass the passphrase so as to not need me to deal with the dialog box ASKING for the passphrase (see the bullet point list above)

Thanks for any help anyone can provide.

H

---

