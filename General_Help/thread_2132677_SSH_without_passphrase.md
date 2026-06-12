---
title: "SSH without passphrase"
date: 2013-04-05
forum: General Help
---

### Post by graabein on 2013-04-05
Hi, I have generated SSH keys and copied id_rsa and id_rsa.pub to local and remote .ssh folders. Still when I do "ssh remoteserver" I have to enter passphrase. What am I missing?

I've checked that both files are identical locally and remote. Please help :)

---

### Post by CaptainMark on 2013-04-05
No you dont copy all the files, from the client you need to copy the contents of the file id_rsa.pub and append the contents to the servers file .ssh/authorized_keys this file can contain many lines, one for each authorized client. The command ssh-copy-id done on the client will do this for you but only whilst the server has password authentication enabled, once done, you can disable password authentication and have a passwordless login

---

### Post by graabein on 2013-04-05
I did "ssh-copy-id -i ~/.ssh/id_rsa.pub servername" and it outputted the expected response. Still, using ssh servername asks for the passphrase.

I'm using xmonad BTW, if there's a GNOME program that needs to be in the loop for this? Terminal is gnome terminal.

---

### Post by steeldriver on 2013-04-05
You need to be clear about the difference between a pass**word** and a pass**phrase** - if it's asking for a pass**word** then it suggests it's not finding/recognising the key and is dropping through to regular password-based authentication but if it's asking for a pass**phrase** then it wants the phrase you entered when generating the key pair - you can set a blank phrase if you don't want to be prompted but obviously that loses one factor in security

```
     
man ssh-keygen
     .
     .
     .
     Normally this program generates the key and asks for a file in which to store the private key.  The public key is stored in a file with the same name but “.pub”
     appended.  The program also asks for a passphrase.  The passphrase may be empty to indicate no passphrase (host keys must have an empty passphrase), or it may be a
     string of arbitrary length.  A passphrase is similar to a password, except it can be a phrase with a series of words, punctuation, numbers, whitespace, or any string of
     characters you want.  Good passphrases are 10-30 characters long, are not simple sentences or otherwise easily guessable (English prose has only 1-2 bits of entropy per
     character, and provides very bad passphrases), and contain a mix of upper and lowercase letters, numbers, and non-alphanumeric characters.  The passphrase can be changed
     later by using the -p option.


```

---

### Post by efflandt on 2013-04-05
Something does not make sense.  If you generate a key without a passphrase and properly set it up on the server, nothing should ask for a passphrase and no passphrase would work.

So either you generated that key using a passphrase, or that key does not work and some other key with that passphrase is being used.

Note that once it is working without any passphase or password, you should limit what commands that key can be used for.  Otherwise if anyone obtains that private key, they could do anything you can do.

---

### Post by Habitual on 2013-04-05
> **graabein said:**
> when I do "ssh remoteserver" I have to enter passphrase. What am I missing?
technique mostly;

```
ssh -qi /path/to/keyfile.pub user@domain.com
```This **assumes** that you have copied contents of /path/to/keyfile.pub to the *end of the file on *remoteserver:/home/x/.ssh/authorized_keys
Where x is the user that you want to have login. x will never be root at that location.

So, on the machine you want to log into, you should add a line to    your ~/.ssh/authorized_keys file that contains exactly    the single line that was created in the keyfile.pub    file (for whatever choice of "keyfile" you made).

[http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html](http://www.eng.cam.ac.uk/help/jpmg/ssh/authorized_keys_howto.html)

---

### Post by markbl on 2013-04-05
Note also, that most client environments cache any entered pass-phrase locally in your keychain so you only have to enter it once the first time after login. Certainly the ones I use, Ubuntu and Mac OS X do this by default. Make sure you enable ForwardAgent in your ~/.ssh/config. A pass-phrase makes your key much more secure and it's not very onerous to use a pass-phrase once it's cached in your keychain.

---

