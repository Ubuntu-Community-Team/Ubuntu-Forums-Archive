---
title: "Import network server connections from KDE to Cinnamon"
date: 2015-09-05
forum: General Help
---

### Post by klasw on 2015-09-05
I installed Cinnamon desktop after have been using KDE a long time. It actually functions very well, it is faster even with KDE programs. 

Now i want to be able to import my network connections to different servers who KDE store in a catalog in to Cinnamon. How can I do that without having to enter password for them all again?  

 Were are those connections in KDE?

---

### Post by TheFu on 2015-09-05
What do you mean by "network connections"?
If they are ssh-based, that data is in ~/.ssh/ and portable.  If not ssh-based - WHY NOT?!!!  sftp is secure from anywhere in the world, assuming ssh-keys are used.

---

### Post by klasw on 2015-09-07
> **TheFu said:**
> What do you mean by "network connections"?
If they are ssh-based, that data is in ~/.ssh/ and portable.  If not ssh-based - WHY NOT?!!!  sftp is secure from anywhere in the world, assuming ssh-keys are used.

Thank you for your replay.

Most off the connections is actually SSH ore sftp, but some are only old ftp.

The thing is that KDE saved all the password to the connections in keyring. I just want to import the connections easy to Cinnamon.

---

### Post by TheFu on 2015-09-07
Spent the last 15 min looking for an answer - even how KDE does this.  

Found KWallet, but don't know how all of that fits together to store and access different credentials. I've never used any "wallet" - seemed single platform to me and that has always scared me.

Maybe you'll see something I didn't in these links:
* [https://help.ubuntu.com/community/kwallet](https://help.ubuntu.com/community/kwallet) - says "export" will be supported later
* [https://askubuntu.com/questions/129897/how-to-migrate-passwords-from-kwallet-to-the-gnome-keyring](https://askubuntu.com/questions/129897/how-to-migrate-passwords-from-kwallet-to-the-gnome-keyring) - seems KeePassX might read it? I've been using KeePassX for 8+ yrs. The DB for v1 KeePass is binary compatible with KeePassX and DroidPass. Don't know if this helps, but maybe.

BTW - Gnome has moved to "seahorse" for this function.

Also - old school FTP credentials are stored in the ~/.netrc file, unencrypted.

Good luck! Hope this helps. Sorry it couldn't be more.

---

### Post by klasw on 2015-09-07
Thank you, i try it out, to export and import the credentials.

---

