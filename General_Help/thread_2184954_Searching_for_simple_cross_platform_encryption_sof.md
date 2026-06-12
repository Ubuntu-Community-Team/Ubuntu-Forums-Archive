---
title: "Searching for simple cross platform encryption software"
date: 2013-10-31
forum: General Help
---

### Post by andan on 2013-10-31
Hi all

I need a suggestion with encryption software.

Now idea behind is this. I need a cross platform software able to encrypt and decrypt on fly files (folders is ok too but main point is  files). For example I want to backup documents in cloud (for example. Ubuntu1 or G drive or Box.com) but I want it encrypted. I also need to be able to decrypt it on different OS and  platforms (so far using ubuntu, mint and  win 7 powered machines on daily bases). Most of encryption software I checked are container encryption based (TrueCrypt for example) and  make this quite simple steps I want, way to complicated.

I would  like to be able to encrypt a file (xyz.odt for example)  on my ubuntu 12.04 upload it to G Drive, download it on Win 7 decrypt it. 

Any suggestions?

---

### Post by Impavidus on 2013-10-31
gpg should do the job.

---

### Post by andan on 2013-10-31
I prefer something with GUI too since I would like my family to be able to use it too. Not sure how to set up gpg to act as explained in opening post?

---

### Post by Dennis N on 2013-10-31
**seahorse** is a Linux graphical front-end for **gnupg**.
[http://xmodulo.com/2013/08/how-to-pgp-encrypt-decrypt-digitally-sign-files-via-gnupg-gui.html](http://xmodulo.com/2013/08/how-to-pgp-encrypt-decrypt-digitally-sign-files-via-gnupg-gui.html)
**GPG4Win** is for Windows; **Mac GPG** for Mac.

I have been using the command line program **gnupg** so cannot comment on **seahorse**. The kind of encryption you would be using would be symmetric encryption, which uses the same password or passphrase to encrypt and decrypt. There are no public and private keys involved with that. The code is very simple to encrypt and decrypt with symmetric encryption from the command line.

---

### Post by andan on 2013-10-31
Thanks gonna check Seahorse to see if it can cover my needs.

**UPDATE**: Seahorse installed gpg key obtained the encryption done but once encrypted file is downloaded from server on different machine decryption just doesn't work. error message says key missing.
Couldn't find any decent seahorse manual, is anyone able to explain the process in u know  simple  words :).

> [COLOR=#000000]The kind of encryption you would be using would be symmetric encryption, which uses the same password or passphrase to encrypt and decrypt. There are no public and private keys involved with that.[/COLOR][COLOR=#000000]The code is very simple to encrypt and decrypt with symmetric encryption from the command line.[/COLOR]
Yes that exactly what I'm searching for with GUI if possible. Is there any cheats list for such commands written in manner that not tech savvy people can understand, So I don't spend days to explain my family how to decrypt a simple odt document?

---

### Post by Dennis N on 2013-11-02
The first time you run seahorse you could be asked to generate a public-private key pair (I am not familiar with seahorse so can't say for sure). That is ok, they will be stored and used later if needed. They are not needed for symmetric encryption. In command line gnupg, you have to explicitly choose to generate a key pair.

I only use the command line, and don't know seahorse's interface. So here is a quick example of command line encrypt and decrypt. Google "gpg tutorial" and you will find lots of guides.

Here is command line encrypt and then decrypt:

encrypt:
```
dn@Sydney:~$ gpg -c test
```

I made a file named test to encrypt.  -c is switch for doing symmetric encryption. You will be asked for passphrase, and confirm. Make one up but record it somewhere as you need it to decrypt. The file is encrypted to test.gpg. You should see it in the the same directory (using home directory here). 

When doing this for real, I suggest you use a password generator to make one that is considered secure enough.


To decrypt, the switch is -d. The output will appear on the screen.
```
dn@Sydney:~$ gpg -d test.gpg
gpg: CAST5 encrypted data
gpg: encrypted with 1 passphrase
This is a test message.
gpg: WARNING: message was not integrity protected

```
Don't worry about the warning.

 If you want to output result to a file, you have to supply a file name. In the example below, I chose 'test-decrypted'.
```
dn@Sydney:~$ gpg -d -o test-decrypted test.gpg
```

To decrypt on a different machine, you have to get the password to the other person. If this is for real, you would meet them in person. What else is secure nowadays? Certainly not email, or even the telephone. Depends how secure you want to be. 

This is just one type of encryption. The other, public-private key encryption is common for sending messages or documents back and forth by email and is secure for that. No clandestine meetings needed.

Hope that helps.

---

### Post by Dennis N on 2013-11-03
**Seahorse** provides "passwords and keys" manager. Encryption/decryption of files using **seahorse** with gnupg requires the plug-in **seahorse-nautilus**. This means you can only encrypt/decrypt if your file manager is nautilus, not thunar or pcmanfm.

There was a bug that has prevented a symmetric encryption option with seahorse-nautilus. It is reported fixed as of Aug 2013. You could still do public/private key encryption, and also manage keys.  

I installed seahorse and seahorse-nautilus (which also installs seahorse-daemon as a dependency) in Ubuntu 12.04 and it works for encrypting with a public key (but no symmetric encryption option).

I don't know if the symmetric encryption is present in the Ubuntu 13.10 version. If not, you must use the command line to do symmetric encryption. Fortunately, that is relatively easy (see post 6).

---

### Post by andan on 2013-11-04
Thank you!, marked as solved. I'm running 12.04.LTS but with Nemo instead of Nautilus, seahorse in context menu doesnt offer symetric encryption, but adding the key psyhically to all 3 machines at home should do the trick.

---

