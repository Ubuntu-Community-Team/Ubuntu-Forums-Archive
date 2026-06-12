---
title: "How to create a compressed file that's encrypted and password protected"
date: 2018-08-21
forum: General Help
---

### Post by waltd on 2018-08-21
Hi all, I just installed Ubuntu 18.04.1 I ran in the terminal  ```
sudo apt-get install p7zip p7zip-rar
``` .        
When I right click a file and choose the "compress" option, I get three options: zip, 7zip, and tar.xz.  But I don't see any options to create an encrypted and password protected compressed file. In the past I could create password protected compressed files with 7zip.  
How can I create a compressed file that is encrypted and password protected?

---

### Post by oldrocker99 on 2018-08-22
If you right-click the file and select "Compress," you can compress with rar (which is by far the most-used compressor for files to be password-protected), and select "Other Options," which allows a password to be entered. If it's a big file, you can split it into, say 10MB per file, and the files will be named```
name,of.file.part01.rar
name,of.file.part02.rar
name,of.file.part03.rar
etc.
```

You might also enter this:```
sudo apt install rar unrar
```
If you have them, no harm. You do have to have them for this. p7zip-rar, AFAIK, will not work.

For encryption, check this page:[https://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html](https://www.cyberciti.biz/tips/linux-how-to-encrypt-and-decrypt-files-with-a-password.html)

---

