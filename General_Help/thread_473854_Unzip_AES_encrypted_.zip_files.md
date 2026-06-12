---
title: "Unzip AES encrypted .zip files"
date: 2007-06-14
forum: General Help
---

### Post by scottmuz on 2007-06-14
I need to unzip (and unencypt) a encrypted ZIP file made with 
WinZip 9+. I know the password have unzipped it by logging into
Windows but this is obviously a rubbish solution.

I believe it uses AES encryption. When I try the gnome archiver or unzip
I get:

unzip -P XXXXXX jpm.zip
Archive:  jpm.zip
   skipping: MURRAY, Scott.doc       unsupported compression method 99
   skipping: MURRAY, Scott Website Letter.doc  unsupported compression method 99

Anyone know of a way to solve this problem in Linux?

---

### Post by vanhoudn on 2007-11-07
You need 7zip to unzip it. 

Install it with 
 $  sudo apt-get install p7zip-full

Then you can extract your file with:
 $ 7z x yourArchiveName.zip

It will prompt you for a password, enter it, and then it will extract it for you.

---

### Post by UbuGianlu on 2007-12-11
Thanks!! very useful! I was looking for a graphical tool that permit AES256 encryption but i didn't find anything for linux,,
Graphical doesn't matter the important is that works :popcorn:

luca

---

### Post by Fatboy Snarky on 2008-04-05
Hi,

are you looking for a GUI tool to create/use archive encrypted archive files under Linux?

Maybe what you're looking for is TrueCrypt (truecrypt.org) or FreeOTFE (freeotfe.org)...

Truecrypt is more widely known. FreeOTFE's advantage: It also reads DM-Crypt/LUKS containers.

HTH,
Ulrich

---

