---
title: "error with installing some packages"
date: 2006-10-24
forum: General Help
---

### Post by Fittersman on 2006-10-24
this error comes up when i try and install some packages such as macromedia flash player 

```
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
```

---

### Post by catlett on 2006-10-24
That is asking you for the public key to that repository. In linux you will see lots of people sign programs,emails, etc with a public key. Some repositories have a public key which you need to download to access. There are a few pages on wikipedia about it [http://en.wikipedia.org/wiki/Public-key_cryptography](http://en.wikipedia.org/wiki/Public-key_cryptography)
All you need to know is the process to use when you see that. This is the template
```
    gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -
```
When you get an error message, replace the word "KEY" with the numbers in the eror message. For your error you would enter this command 
```
 gpg --keyserver subkeys.pgp.net --recv  F120156012B83718 
```
After you press enter and it sends the command, you would enter the second line
```
 gpg --export --armor  F120156012B83718 | sudo apt-key add -
```
After that, the key will be added to a list and the error will not appear.

---

