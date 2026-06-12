---
title: "I need help with GNU Privacy Guard and signing the Ubuntu Code of Conduct"
date: 2007-04-17
forum: General Help
---

### Post by Coop on 2007-04-17
Hello everyone


I am using Ubuntu 6.10 Edgy Eft, as you can see in the right to my avatar.


I want to sign the Ubuntu Code of Conduct and become an Ubuntero.


I have registered my Open PGP key, and decrypted the email Launchpad.net sent me.


I am upto the part of signing the Code of Conduct, which is on [this webpage]("https://launchpad.net/codeofconduct/1.0.1/+sign").



I am having a problem with this part:```
In a terminal, run the command: 
gpg --clearsign UbuntuCodeOfConduct-1.0.1.txt 
(or whatever filename you gave to the code). This will create a file with a name like UbuntuCodeOfConduct-1.0.1.txt.asc.
```


When I run the command: > gpg --clearsign UbuntuCodeOfConduct-1.0.1.txt , instead of asking for the passphrase for the OpenPGP key which I registered on Launchpad.net, it asks for the passphrase for an older OpenPGP key which I created which I didn't register on Launchpad.net.


How do I make the command: > gpg --clearsign UbuntuCodeOfConduct-1.0.1.txt  ask for the passphrase for the OpenPGP key which I registered on Launchpad.net, instead of asking for the passphrase for the older OpenPGP key which I haven't registered?


Do I have to add any special parameters to the command: > gpg --clearsign UbuntuCodeOfConduct-1.0.1.txt ?



Please answer me. I will highly appreciate any help you can give me.

---

### Post by Brucevdk on 2007-04-17
You can use the -u switch to specify which user ID to use. From the man page:

```

-u, --local-user name
                 Use name as the key to sign  with.   Note  that  this  option
                 overrides --default-key.

```

So try:

```
gpg -u <userid> --clearsign UbuntuCodeOfConduct-1.0.1.txt
```

I personally don't have a lot of experience with GPG/PGP, but perhaps you should look into deleting/revoking the other key if you don't use it anymore.

---

### Post by Coop on 2007-04-17
Thank you Brucevdk for your help. I highly appreciate it.
I'll try your advice.

---

