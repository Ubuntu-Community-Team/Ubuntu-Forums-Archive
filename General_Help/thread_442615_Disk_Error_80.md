---
title: "Disk Error 80"
date: 2007-05-13
forum: General Help
---

### Post by nathan3013 on 2007-05-13
downloaded Ubuntu Copied to a CD RW and Ubuntu wont install I get a error message saying 
Error reading boot CD am i not using the right kind of disks? Is it my system I have a Hewlett
Packard XL 766 with a 40 GB Hard Drive and im using Windows 98 SE OEM came with the
HP Recovery Program I would love to get Ubuntu up and running so i dont have to use
Windows 98 any ideas on how to fix this:confused:

---

### Post by Ken_Lewis81 on 2007-05-14
There's a number of things you might have done wrong.

The most obvious is that you "copied to a CDRW" which isn't actually the right thing to do.  The .iso files are disk images -- that is, they represent what the file layout on the CD should be -- and so you need to write that information directly to the CD, not copy it there as if it was a file.  If your CD writing software supports it, choose 'Burn CD from CD image'.  That should make it work.

There's also the possibility that the download has errors in it, or that writing the CD has errors.  There are tools to check the integrity of the download (google for a MD5sum and SHA1sum checkers, if you're concerned) and the standard recommendation for burning CD's reliably involves burning them as slowly as you can tolerate.

Hope this helps.
Take care.
Ken.Lewis

---

