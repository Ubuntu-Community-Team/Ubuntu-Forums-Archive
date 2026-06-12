---
title: "Run software in tar files"
date: 2015-09-18
forum: General Help
---

### Post by ckrles on 2015-09-18
Hi I have a couple of programs which are packed into a tar file. I've decompressed each of them and I have a folder containing the name of the software. I open it and I find no instructions or ./configure o ./make file. I've googled for an answer but everything I found was mostly related to .tar.gz and tar.bz. One of the programs I'm trying to run is flashtool to flash my sony xperia z1. I've decompressed it rightclicking and extracting, and usinf tar xvf filename,tar. THe same folder is created.

This is the link to the software [http://www.flashtool.net/downloads.php](http://www.flashtool.net/downloads.php)

In the case of flashtools, I could run it using Windows 7, but I have another software which I have to run on linux.

I would really appreciate your help.

Thank you very much.

---

### Post by ian-weisser on 2015-09-18
Please show us the listing of your decompressed folder contents.

---

### Post by VMC on 2015-09-19
Did you notice the "FAQ|Linux installation link" found [here]("http://www.flashtool.net/lininstall.php"). ?

---

### Post by ckrles on 2015-09-19
I have found out how to run it, but only as root. I type sudo ./FlashTool in the terminal and enter my password. I'm surprised I have to run it as root or can't create a launcher (direct access)

Is there some rule or procedure to run other decompressed tar software?

---

### Post by oldos2er on 2015-09-19
Please provide the information requested in post #2. Tar files are simply archives that can contain anything.

---

### Post by ian-weisser on 2015-09-19
The same rules or procedures apply to run ALL software:
 The binary must be in an expected location.
The file must be owned by the appropriate user/group.
The file must have executable permission.
 
All of this (and much more) is done automatically by the package manager when you install deb packages.
None of this is done automatically by untarring. Tar files are merely file containers, tar files are not software packages.

---

