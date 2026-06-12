---
title: "Keyring questions"
date: 2008-02-06
forum: General Help
---

### Post by MountainX on 2008-02-06
I just installed Seahorse. Where does it store the keys? Are public and private keys stored in the same location?

If I want to import PGP keys, how can I do that? I tried the straight-forward "import" command, as described in help, and none of the keys show up in Seahorse. However, if I type gpg --list-keys in a terminal, I see all the imported keys. I find this very confusing. Where the heck are they stored and how secure is that location?

If I want to store my private key on removable media, how can I do that?

If I want to be able to move keys stored in gpg to another computer, how would I do that?

On Windows I have the Aladdin eToken (with PGP). Can I use that here? If not, I have to figure out how to get my private key out of the token...

Thanks for any tips.

---

### Post by euler_fan on 2008-02-06
> **MountainX said:**
> I just installed Seahorse. Where does it store the keys? Are public and private keys stored in the same location?

If I want to import PGP keys, how can I do that? I tried the straight-forward "import" command, as described in help, and none of the keys show up in Seahorse. However, if I type gpg --list-keys in a terminal, I see all the imported keys. I find this very confusing. Where the heck are they stored and how secure is that location?

If I want to store my private key on removable media, how can I do that?

If I want to be able to move keys stored in gpg to another computer, how would I do that?

On Windows I have the Aladdin eToken (with PGP). Can I use that here? If not, I have to figure out how to get my private key out of the token...

Thanks for any tips.

Not sure off-hand where the file is, but for any given secret key it is protected by your password as usual.

Public keys and private keys are stored in different files in the same folder.

When you look in Seahorse for keys, don't forget to check the other tabs besides yours. It may have dropped it elsewhere because it doesn't know it's yours yet. Just a thought. But since it's in GPG it should show up somewhere. Seahorse is just a front end for GPG after all.

Export your complete key (right-click on a key, select properties, should be on the last tab), and save/burn to removable media. Bang, backup copy. I don't know if you can run Seahorse on a set of keys not stored locally, but I don't think you can.

As for moving stored keys, Seahorse has an option under File to backup the keyring. Back it up and move it. Otherwise export copies of all your keys, put the on a USB drive, and import them all to another machine.

No idea about PGP, sorry.

Otherwise, just play around with it some. It's quite forgiving software and there's not much to explore nor find.

---

### Post by MountainX on 2008-02-10
Does GPG (GnuPG) support storing private keys on Aladdin eToken? Thanks.

---

### Post by kevdog on 2008-02-10
> Aladdin eToken

What is this?

---

### Post by seventhc on 2008-02-10
In your home directory, press <ctrl-h> and you keys should be in .gnupg
I would save this folder.

---

### Post by euler_fan on 2008-02-10
> **MountainX said:**
> Does GPG (GnuPG) support storing private keys on Aladdin eToken? Thanks.

Given Aladdin eToken is a proprietary security solution, my guess would be not out of the box if at all.

I have seen threads to get DOD CAC credentials to work, so anything is possible.

---

### Post by MountainX on 2008-02-11
After lots of research, it seems pretty clear that GnuPG (gpg) does not support the Aladdin eToken.

A suitable alternative is probably to put gpg keys on a TrueCrypt encrypted USB drive.

Surely the Aladdin eToken is more secure, but I think I would rather have a less proprietary solution. eToken requires OS support AND application support. At the moment I can't even get the commercial PGP on Windows to recognize my eToken. (It was working a few weeks ago.) I'm locked out of my data until I reach Aladdin Tech Support on Monday.

A plain old USB drive with TrueCrypt will be a lot less problematic and it will probably do the job for me.

If someone wanted to go even further, the biometric USB flash drives (or IronKey) might be other alternatives, although I'm not sure they will work well on Linux. IronKey has Linux support in the works and Transcend's JetFlash drives have some support for Linux, but I'm not sure the fingerprint reader feature works on Linux... searching on Google gives no answers either.

---

### Post by MountainX on 2008-02-11
> **kevdog said:**
> What is this?

Aladdin eToken is a USB "smart card"-thingy for public key encryption. The private key cannot be extracted from the token.

[http://www.google.com/search?num=100&hl=en&safe=off&q=Aladdin+eToken&btnG=Search](http://www.google.com/search?num=100&hl=en&safe=off&q=Aladdin+eToken&btnG=Search)

---

### Post by shkuter on 2008-03-19
[http://www.aladdin.ru/bitrix/redirect.php?event1=download&goto=/upload/iblock/2c5/eToken_PKI_Client_4_55_Linux.rar](http://www.aladdin.ru/bitrix/redirect.php?event1=download&goto=/upload/iblock/2c5/eToken_PKI_Client_4_55_Linux.rar)

eToken PKI Client v4.55 & PKCS#11

---

### Post by MountainX on 2008-03-20
> **shkuter said:**
> [http://www.aladdin.ru/bitrix/redirect.php?event1=download&goto=/upload/iblock/2c5/eToken_PKI_Client_4_55_Linux.rar](http://www.aladdin.ru/bitrix/redirect.php?event1=download&goto=/upload/iblock/2c5/eToken_PKI_Client_4_55_Linux.rar)

eToken PKI Client v4.55 & PKCS#11

I got a 404 - HTTP not found. Is the documentation in English or Russian? Does this work with GPG?

---

### Post by shkuter on 2008-03-21
sorry
[http://www.aladdin.ru/upload/iblock/609/eToken_PKI_Client_4_55_Linux.rar](http://www.aladdin.ru/upload/iblock/609/eToken_PKI_Client_4_55_Linux.rar)
documentation in English

---

