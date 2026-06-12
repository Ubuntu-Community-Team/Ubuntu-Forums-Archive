---
title: "Password won't reset Ubuntu 13"
date: 2014-02-09
forum: General Help
---

### Post by chris169 on 2014-02-09
A couple days ago I reset my password in "user settings".  My password is not being excepted now.

I then reset my password by booting from recovery mode and entering the root folder and followed the basic commands to reset my user folder as outlined here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) .

Needless to say, this did not work and my password is still being rejected.

Is this not working because my folders are encrypted?  And if so how do I go about reseting my login password to an encrypted folder?

Note, I do have my encryption key.

Any help is greatly appreciated, thank you.

---

### Post by Dave_L on 2014-02-10
Where is the password being rejected?  

If you switch to a command shell with Ctrl+Alt+F1 can you login? (Use Ctrl+Alt+F7 to return to the GUI.)

---

If your home folder encrypted is encrypted, you can use the ecryptfs-rewrap-passphrase command to re-encrypt your ecryptfs passphrase with your new login password:
manpages.ubuntu.com/manpages/lucid/man1/ecryptfs-rewrap-passphrase.1.html

Make a backup copy of the file /home/.ecryptfs/USER/.ecryptfs/wrapped-passphrase before you change it (USER is your username).

---

