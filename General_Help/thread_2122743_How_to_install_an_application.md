---
title: "How to install an application"
date: 2013-03-06
forum: General Help
---

### Post by fanzio12 on 2013-03-06
Hello everybody,

I have the following problem which I wish to solve using ubundu.
 I have a server application which is running in SCO UNIX. Every time I need to install it to a new server I just copyning (tar cvf /app) it and then (tar xvf /app).
DO you have any sujestion on how I can use ububtu and install there my applicayion?

tanks

---

### Post by r-senior on 2013-03-06
Do you have the source code of this application or just the binaries? Do you know which language it is written in?

Are there other steps that you take after unpacking the archive? Where do you normally unpack it?

What does the application do?

---

### Post by codemaniac on 2013-03-06
Hi fanzio12,

Welcome to the Ubuntuforums!!

Your thread is not about "Programming Talk", hence it is moved to "General Help" sub-forum.

Please provide more information about the application you are trying to install. If it is source tarball there should be a README file or something similar that contains information about how to install and configure.

However you can avoid installation from source if the software is already available in repositories.

Best of Luck!!

---

### Post by fanzio12 on 2013-03-06
thanks r-senior,

the application is called fids (flight information display system).
The server runs SCO Unix 2.1.2. 
So I have the server runnig the application (name "Greek18"). I do not have the source code. It is installed under root/app. Everytime I need to transfer it in an onother system which runs SCO Unix I am following the steps:
- going to /app and tar cvf /app
- then in the new server tar xvf /app

the application runs when typing "fids", calls upa shell procedure contained in the directory /app/tools

Do you have the source code of this application or just the binaries? NO
 Do you know which language it is written in? NO
Are there other steps that you take after unpacking the archive? no
 Where do you normally unpack it? /app

---

### Post by r-senior on 2013-03-06
OK, so it sounds like you have binaries. I don't think they will work.

This might be of interest, although it looks like it's not being maintained.

[http://linux-abi.sourceforge.net/](http://linux-abi.sourceforge.net/)

---

