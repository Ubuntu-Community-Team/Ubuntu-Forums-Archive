---
title: "Trouble with verifying iso - cannot open gpg file"
date: 2016-01-25
forum: General Help
---

### Post by phyrius2 on 2016-01-25
I’m still relatively new to the CLI and trying to make myself use it more, although I'm not sure this is really a CLI issue or not. I'm currently stuck on step 2 of the instructions for verifying an .iso given here:

[https://help.ubuntu.com/community/VerifyIsoHowto](https://help.ubuntu.com/community/VerifyIsoHowto)


Step 2 indicates a user can determine what key is needed for verification by executing

```
gpg --verify SHA256SUMS.gpg SHA256SUMS
```

According to the instructions, I should receive something like

```
gpg: Signature made Wed 11 Nov 2015 20:08:10 GMT using RSA key ID EFE21092
gpg: Can't check signature: public key not found
```

However, when I do this I get the following

```
gpg: can't open 'SHA256SUMS.gpg'
gpg: verify signatures failed: file open error
```




I can confirm both SHA256SUMS.gpg and SHA256SUMS files are on my local machine, located in the same directory.  

What does this terminal result mean?  How can I proceed?

---

### Post by lisati on 2016-01-25
Duplicate of [http://ubuntuforums.org/showthread.php?t=2311221](http://ubuntuforums.org/showthread.php?t=2311221) (accidental?) closed.

---

