---
title: "What can I expect backing up at home and to an online service, with Encrypted Files?"
date: 2015-07-20
forum: General Help
---

### Post by mikodo on 2015-07-20
Hi everyone.

Presently, I am only backing up my "Data" with rsync locally, to two usb nodes, with nothing encrypted. I don't like that and, I want to get back to encrypting a small file,  (< 20kB) within "Data" separately, (make 2 files). One with KeePassX and another gpg AES256 symmetrically. I also plan to use an online service, that charges per bit of transfer and for backup. I want to continue to use rsync -- delete, with subsequent backups.

Question.

 Because these two encrypted files will remain in "Data" for backups, will the rsync backups start making repeats of the encrypted <20kB files, because it wouldn't be able to read what is inside of them? What can I expect? 

Edit: I should have mentioned, those 2 < 20kB files, will change +/- as I need. (passwords, banking stuff, etc).

Thanks, for sharing your wisdom/experience.

---

### Post by Geoffrey_Arndt on 2015-07-20
Some files and directories are (in my humble opinion) too important to not to compress and encrypt manually.  I use the 7zip tool to do that (AES256), then move the files to appropriate dropbox folder.    I like using Zim for managing the text files, including those specific files that will need encryption & unencryption.   7z works perfect for that.   KeePassX does offer a substantial benefit - - the generation of super complex, long passwords (which is not addressed by 7z.

---

### Post by mikodo on 2015-07-21
> **Geoffrey_Arndt said:**
>  -snip-
Thanks. 

More to think about now.

I appreciate your sharing, what might be a better way.

---

### Post by Geoffrey_Arndt on 2015-07-21
Your method is just fine, especially use of KeePassX - which is still all around a great tool for a password database (much better than zim).    But Zim is more flexible for general data, as a knowledge base, and has excellent and growing base of plug-ins.   Some of that data could be sensitive, but 7zip does provide an easy way to archive the whole zim database (notebooks) or just parts of it.

I still have a friend that uses Excel as a db, and another program (PGP) for encryption.   It may be the strongest, especially if using "twofish" . . . perhaps the only secure algorithm left without a back-door.

---

### Post by mikodo on 2015-07-21
Thank you.

> **Geoffrey_Arndt said:**
> Your method is just fine, especially use of KeePassX which is still all around a great tool for a password database (much better than zim). 
It was HermanAB's idea, that he suggested to me.

>  Zim is more flexible for general data, as a knowledge base, and has excellent and growing base of plug-ins.   Some of that data could be sensitive, but 7zip does provide an easy way to archive the whole zim database (notebooks) or just parts of it
Thanks, for that. I am still wrestling with the idea of backing up encrypted files and maybe getting another repeat each time, as it has changed, in the encrypted file. Using 7zip, sounds like a way to minimize the amount of bits in each repeated encrypted file though.

> I still have a friend that uses Excel as a db, and another program (PGP) for encryption.   It may be the strongest, especially if using "twofish" . . . perhaps the only secure algorithm left without a back-door.

I was thinking of using gpg  AES256 symmetrically. AES algorithms have known backdoors?

---

### Post by Geoffrey_Arndt on 2015-07-23
Re use of AES . . . I use it daily (7z), along with GPG.  If used with hard passwords, and for general consumer or business use, no issues.   Certain organizations will use the Twofish algorithm for specific high risk use cases.

The issue is not UK or US govts, but just keeping content from exploitation by groups wanting financial gains.   These people go after much easier targets.

---

### Post by mikodo on 2015-07-23
> **Geoffrey_Arndt said:**
> Re use of AES . . . I use it daily (7z), along with GPG.  If used with hard passwords, and for general consumer or business use, no issues.   Certain organizations will use the Twofish algorithm for specific high risk use cases.

Good to know. Thanks!

> The issue is not UK or US govts, but just keeping content from exploitation by groups wanting financial gains.   These people go after much easier targets.

Same here.

---

