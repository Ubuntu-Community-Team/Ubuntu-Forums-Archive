---
title: "Linux alternative for offsite backup encryption"
date: 2016-04-19
forum: General Help
---

### Post by greavette on 2016-04-19
Hello,

I'm hoping this community can help me find a good alternative!

I'm using cryptsync on windows.  It's a slick little app that works as folows:

[LIST]
[*]You assign the first folder for Cryptsync to read.  This is your unecrypted folder.
[*]You assign a second folder for Cryptsync to copy all files from the first folder into as zipped and encrypted.  So each and every file in the first folder is copied to the second folder as a zipped encrypted file.  The encryption uses 7zip Method: LZMA 7zAES.  [/LIST]

I use the above method whereby I copy the zipped and encrypted files from the second folder to my offiste (cloud) storage.  In this way I own the encryption key for offiste backup in case my cloud storage is hacked.  I know it means double the space is used within my LAN to have two copies of each file...but it also means that my offsite storage backup only backs up files that have changed so offsite copy is quicker. :)

I'm looking for a Linux alternative to the above though.  Cryptsync runs as a service on Windows.  I'm running it in a Windows virtual machine.  I'd like to move away from using Windows for this one purpose for backup and instead drop in an Ubuntu Server to run my backup/encryption task using the Ubuntu VM.

Is there a linux system/app built that will allow me to do this in a similar fashion?

Thank you.

---

### Post by frostschutz on 2016-04-19
Are you using for a one click solution? Then I don't know. Maybe something with encfs?

If you're familiar with the CLI, dar (disk archive) is an alternative to tar that can create compressed (depending on file type), incremental, encrypted archives. [http://dar.linux.free.fr/doc/Features.html](http://dar.linux.free.fr/doc/Features.html)

But it may be even more complicated to use than tar. Basically it's nigh unuseable until you wrap it into a script that does just the thing you want it to do.

---

### Post by greavette on 2016-04-22
Thanks very much for the reply frostshutz.  I've heard of encfs...I will definitely check this out as well as dar.

---

