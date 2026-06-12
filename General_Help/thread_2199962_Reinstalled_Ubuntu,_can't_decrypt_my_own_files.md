---
title: "Reinstalled Ubuntu, can't decrypt my own files"
date: 2014-01-16
forum: General Help
---

### Post by motoroller on 2014-01-16
Hi everybody... I'm having a bit of an issue here. Over the past year or so, my installation had become kind of messed up with all the desktop environments and other "flavours" I had installed. It was causing some errors here and there, and I was tired of fixing them as they popped up, so I decided to just do a clean install of Ubuntu 12.04 LTS. I backed up my home folder on a flash drive, and did a clean install on the SSD where Ubuntu resides. Everything went really well, except when it came time to transfer the contents of my old home folder into the new one. It wouldn't let me view the files until I opened it using sudo with the terminal.

After I transferred the contents of my old home folder into my new one, I tried decrypting some files with "decrypt file", but it said "Decryption failed. You probably do not have the decryption key." Clearly there's something I've missed. 

Here's the question: How can I use my old private key to decrypt my files? I'm stumped! Any help would be greatly apprectiated!

---

### Post by Dave_L on 2014-01-16
The original install had home directory encryption?

Try this command:

```
sudo ecryptfs-recover-private
```

Reference:
ecryptfs-recover-private - find and mount any encrypted private directories
[http://manpages.ubuntu.com/manpages/precise/en/man1/ecryptfs-recover-private.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/ecryptfs-recover-private.1.html)

---

### Post by motoroller on 2014-01-16
Hi thanks for replying. Actually no, the original install didn't have home directory encryption. The encrypted files were just a few files I had saved on another drive...

---

### Post by mastablasta on 2014-01-17
yes, you need the key to decrypt the files. how were they encrypted? using what program? was it a truecrypt contianer?

also, do not use sudo with grafical interface. use gksu or gksudo (kdesudo in KDE) instead.

---

### Post by Dave_L on 2014-01-17
How exactly did you transfer the old home folder into the new one?

When you originally encypted the files, did you have to create a GPG  key pair?

If you run "seahorse" from the terminal, does the key show up there?

---

### Post by motoroller on 2014-01-17
Hi Dave_L,

To transfer my old home folder, all I did was copy and paste individual folders from my old home folder into my new one. For .gnupg I believe I had to use gksudo nautilus and then move it over to the new home folder. 

When I originally encrypted the files, I did create a GPG key pair, but I don't know where the private key is stored...

and for mastablasta, I used GPG to encrypt the files individually.

in Seahorse, the old public key shows up under "other keys"


Hopefully that helps!

---

