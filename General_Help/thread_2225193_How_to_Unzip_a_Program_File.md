---
title: "How to Unzip a Program File"
date: 2014-05-20
forum: General Help
---

### Post by abacki on 2014-05-20
Hi everyone. Well I'm not doing everything possible with this Zip file, obviously. It is a program, and it unzips well enough, the files are there. How do I assemble/run the program? The readme gives no helpful information. And, I've not found an answer on the forum that I can use. Thanks, in advance for any help.

Ubuntu 12.04

---

### Post by christo3 on 2014-05-20
what zip file? check filetype in filemanager or using file in terminal using the file command

---

### Post by buzzingrobot on 2014-05-20
Installable and ready-to-run programs are seldom distributed as zip files in Linux.  A very few are, however. So, it would be helpful to know the identity of your zip archive and the program you want to install.

---

### Post by Frogs Hair on 2014-05-20
If the program isn't available as a .deb which will open from the software center with a double click then you will have to build as a _last resort_. Check the software center for the program or the site for a .deb 32 or 64 appropriate package. Make sure the program is compatible with the Ubuntu version you are using  and if not don't try to install. Here is a guide for a tar.gz but methods vary and the read me file should include special instructions. I would strongly suggest an alternative program in .deb package archive.  


[http://www.cyberciti.biz/faq/install-tarballs/](http://www.cyberciti.biz/faq/install-tarballs/)

---

### Post by abacki on 2014-05-20
Sorry for the delay. The program is open source and has no system requirements: [http://activequran.codeplex.com/](http://activequran.codeplex.com/)  But why am I getting the impression that it was made for MS Windows.

---

### Post by coffeecat on 2014-05-20
> **abacki said:**
> But why am I getting the impression that it was made for MS Windows.

You are quite right. The main executable file is a Windows-only .exe file and there are a number of .dll Windows libraries in the zip. This application will not run on Ubuntu.

---

### Post by buzzingrobot on 2014-05-20
The image at that link shows a Windows program, and the notes in the Source Code section say it is written in C#, which is almost exclusively  used as a Windows development language, and the utility files listed are intended for Windows.

So, yes, this is a Windows program.

---

### Post by abacki on 2014-05-20
O.K., then I was getting a sound impression. Thanks, everyone, for your help.

---

### Post by coldcritter64 on 2014-05-20
> **coffeecat said:**
> You are quite right. The main executable file is a Windows-only .exe file and there are a number of .dll Windows libraries in the zip. This application will not run on Ubuntu.

If the actual program for windows is completely standalone on Windows, it may possibly work in Wine. A lot of small self contained Windows utiilities/programs have for me in the distant past. It may be worth giving Wine a go with this in my opinion.

Though you should note OP that there are no guarantees any particular Windows app will work in Wine (a code compatibility layer for Windows applications on Linux), this may do so **if** it supplies all the dlls it needs to run.

---

### Post by abacki on 2014-05-22
> **coldcritter64 said:**
> If the actual program for windows is completely standalone on Windows, it may possibly work in Wine. A lot of small self contained Windows utiilities/programs have for me in the distant past. It may be worth giving Wine a go with this in my opinion.

Though you should note OP that there are no guarantees any particular Windows app will work in Wine (a code compatibility layer for Windows applications on Linux), this may do so **if** it supplies all the dlls it needs to run.


Thanks for the info. Wine, however, is a bit too large for my disk just now. I'm actually having trouble with zip files. I watched a video, but couldn't duplicate the results in Windows XP.  I spent most of my time with word processing software, so now I'm trying to catch-up, concerning the applications that I've missed.

---

