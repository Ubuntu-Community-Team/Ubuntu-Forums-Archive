---
title: "Encrypt doesn't work"
date: 2015-02-25
forum: General Help
---

### Post by enricobe on 2015-02-25
Hello, i'm trying to encrypt a folder/file. I have created the OpenGP Key from the Passwords and Keyrings application and the "Encrypt" option now appears when I right-click on a file/folder. 
When i click on "Encrypt", I can select the Key to use for the encyption, but when i press "Ok" nothing happens.

Am I doing something wrong?

---

### Post by enricobe on 2015-02-27
Nobody has any suggestion? :(

---

### Post by Dennis N on 2015-02-27
You can encrypt a file from Nautilus with gpg, but can't encrypt a folder without an extra step:

Using the right-click option in Nautilus to encrypt a file:
**file.txt** encrypts to a new file, **file.txt.pgp**

To encrypt a folder you have to first compress it to a file using the archive manager, then encrypt the archive file:
**foldername** (with its contents) compresses to **foldername.tar.gz** and then that will encrypt to a new file, **foldername.tar.gz.pgp**
An alternate way would be to only encrypt each the files inside the folder. 

(The original unencrypted file or folder and the compressed file are still present, so of course you need to delete them for security.)

---

### Post by enricobe on 2015-02-28
> **Dennis N said:**
> You can encrypt a file from Nautilus with gpg, but can't encrypt a folder without an extra step:

Using the right-click option in Nautilus to encrypt a file:
**file.txt** encrypts to a new file, **file.txt.pgp**

To encrypt a folder you have to first compress it to a file using the archive manager, then encrypt the archive file:
**foldername** (with its contents) compresses to **foldername.tar.gz** and then that will encrypt to a new file, **foldername.tar.gz.pgp**
An alternate way would be to only encrypt each the files inside the folder. 

(The original unencrypted file or folder and the compressed file are still present, so of course you need to delete them for security.)
Thank you very much for your reply.
I didn't know that I can't Encrypt a folder, but I have the same problem with a single file. 
I'm testing on a PDF. I right-click on the PDF and I choose "Cifra" ("Encrypt" in Italian). A new window opens and I can choose the key to use for the encryption. I have only one GnuPG key, so I select this one and I click OK. After the OK, nothing happens. No files with *.pdf.gpg is created.
I've also tried with a .txt, but it doesn't work.

---

### Post by Dennis N on 2015-02-28
If you haven't done so, I would test the key by encrypting from the terminal to be sure it works:

Change directory to where the pdf is and use this pattern to encrypt. I used a pdf file named Ubuntu_MATE1410.pdf. **-r** is followed by the recipient's email address (identifies which key to use), and **-e** is followed by the name of the original file to be encrypted.
 
My test:
```
dmn@Sydney:~/work/test$ gpg -r xxxxxx@gmail.com -e Ubuntu_MATE1410.pdf
```
When executed, here is the encrypted file and the original.
```
dmn@Sydney:~/work/test$ ls
Ubuntu_MATE1410.pdf  Ubuntu_MATE1410.pdf.gpg

```
Note that the **pgp** ending in post #3 is what seahorse-nautilus uses by default (in Ubuntu 12.04), it's not a typographical error. The terminal uses **gpg** as the extension.
If this test doesn't work, I would try creating a new key pair. 
If the test works, your key is obviously ok. The problem could be with the nautilus encrypt plugin (seahorse-nautilus). You did check the box for your key in the dialog before pressing OK? Sorry, but no other ideas for what is wrong come to mind.

---

### Post by sandyd on 2015-02-28
> **enricobe said:**
> Hello, i'm trying to encrypt a folder/file. I have created the OpenGP Key from the Passwords and Keyrings application and the "Encrypt" option now appears when I right-click on a file/folder. 
When i click on "Encrypt", I can select the Key to use for the encyption, but when i press "Ok" nothing happens.

Am I doing something wrong?

What version of Ubuntu are you using
seahorse-nautilus encryption (which powers the encrypt menu) is once again broken in 14.10, and some versions before 14.04.
14.04 seems to be unaffected.
[https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1168685](https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1168685)

---

### Post by enricobe on 2015-02-28
> **Dennis N said:**
> If you haven't done so, I would test the key by encrypting from the terminal to be sure it works:

Change directory to where the pdf is and use this pattern to encrypt. I used a pdf file named Ubuntu_MATE1410.pdf. **-r** is followed by the recipient's email address (identifies which key to use), and **-e** is followed by the name of the original file to be encrypted.
 
My test:
```
dmn@Sydney:~/work/test$ gpg -r xxxxxx@gmail.com -e Ubuntu_MATE1410.pdf
```
When executed, here is the encrypted file and the original.
```
dmn@Sydney:~/work/test$ ls
Ubuntu_MATE1410.pdf  Ubuntu_MATE1410.pdf.gpg

```
Note that the **pgp** ending in post #3 is what seahorse-nautilus uses by default (in Ubuntu 12.04), it's not a typographical error. The terminal uses **gpg** as the extension.
If this test doesn't work, I would try creating a new key pair. 
If the test works, your key is obviously ok. The problem could be with the nautilus encrypt plugin (seahorse-nautilus). You did check the box for your key in the dialog before pressing OK? Sorry, but no other ideas for what is wrong come to mind.

Thank you. From the terminal the encrypted file has been created, so the problem is the nautilus plugin.... I don't know how to solve the problem, but i'll try to remove and install again the plugin. 
Thank you anyway, now i know how to encrypt w/o the GUI :)

> **sandyd said:**
> What version of Ubuntu are you using
seahorse-nautilus encryption (which powers the encrypt menu) is once again broken in 14.10, and some versions before 14.04.
14.04 seems to be unaffected.
[https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1168685](https://bugs.launchpad.net/ubuntu/+source/seahorse-nautilus/+bug/1168685)

Sorry for the delay. I guess we were replying in the same time. 

I have 14.10 indeed. Thank you for the information

I can confirm that is a problem of 14.10. 
I've upgraded to 15.04 and now the "encrypt" function works.

---

