---
title: "special characters in filenames"
date: 2007-09-08
forum: General Help
---

### Post by DiGiTY on 2007-09-08
I'm FTP'n files from my Windows box to my Ubuntu 7.04 box and I notice files with special characters like ò, è, `, à, etc. in their filenames failed to transfer. I'm assuming Ubuntu simply doesn't accept those characters. Or maybe the fact the drive on the Ubuntu box is formatted as FAT32 and mounted with the "iocharset=utf8 " option.

Are one of those things the problem? Do I have to mount using a different charset?

TIA

---

### Post by fragos on 2007-09-08
I believe file names are stored as 8 bit characters.  The ones you mention are 16 bit characters.

---

### Post by DiGiTY on 2007-09-09
so is there a way to get it to 16 bit or at least get it to accept these characters?

---

### Post by fragos on 2007-09-09
It appears that the first 256 characters in the 8 and 16 bit versions are the same.  There must be a way because Asian languages in particular are stored as 16 bit characters.  It relatyes to the "SCIM Input Method Setup".  If you look there you may be able to figure out how to do this.  When you solve this, be sure to post the solution here.

---

### Post by DiGiTY on 2007-09-26
SCIM Input Method Setup appears to have nothing to do with it. I didn't really see any options that strictly relate to this.

this Windows FAT32 drive i'm trying to mount is simply my media storage drive and stores my music library as well so there's a number of world character sets in some titles and naturally file names (French, Spanish, etc.)

any ideas how to make this work universally?

---

### Post by MaestroTech on 2008-04-07
.

---

### Post by ghostdog74 on 2008-04-07
try zipping the files up before transfering.

---

