---
title: "how to backup full ubuntu system"
date: 2018-03-02
forum: General Help
---

### Post by christon74 on 2018-03-02
Good evening fellow Ubunters :)
I have just mounted a 160 Gb external hard disk and I am trying to back up my whole system. A little earlier on I downloaded Clonezilla. But I find myself unable to run it. It's here and it's not. When I search my computer, I cannot find it. So I am trying another solution: "Rsync"
Now, my question is this, can I try this when the PC is connected to the web? Well, to be honest, I have already copy/pasted the command line.  I am asking because I have found a page where I read this: 
"Please be mindful that this is suitable for local and stand-alone  systems only. If your system is being actively accessed by some other  systems on the network, it isn’t better solution. Because, the contents  of these systems might be constantly updated every minute, and some  files may change during the rsync process. Say for example, when rsync  will reach the file 2, the contents of the previous file (File 1) might  be changed. This will leave you with a dependency error when you will  need to use that backup. In such cases, a snapshot-based backup is the  better approach. Because the system will get “froze” before the backup  process starts and get it “unfreeze” when the backup process finishes,  so all the files are consistent."
If I need give the source: [https://www.ostechnix.com/backup-entire-linux-system-using-rsync/](https://www.ostechnix.com/backup-entire-linux-system-using-rsync/)
Thanks.

---

### Post by HermanAB on 2018-03-02
Hmm, firstly, Linux is very easy to install and the longer you use it, the easier it is to install.  One day, when your HDD breaks (which should take about 3 to 7 years), you will want to install the latest version, not an old and tired version from backup.

Therefore, only backup your data.  A simple home user who is not running any servers, will not have a problem as described in the above mentioned page.  If you do run a server, then you will have to stop it first, but if you are, then you will not be asking these questions - you'll already know...

---

### Post by christon74 on 2018-03-02
Good piece of Advice, thank you Herman;-) Think I will just do that. Only back up my documents and files.

---

### Post by raleigh3 on 2018-03-02
> **christon74 said:**
> Good evening fellow Ubunters :)
I have just mounted a 160 Gb external hard disk and I am trying to back up my whole system. A little earlier on I downloaded Clonezilla. But I find myself unable to run it. It's here and it's not. When I search my computer, I cannot find it. So I am trying another solution: "Rsync"
Now, my question is this, can I try this when the PC is connected to the web? Well, to be honest, I have already copy/pasted the command line.  I am asking because I have found a page where I read this: 
"Please be mindful that this is suitable for local and stand-alone  systems only. If your system is being actively accessed by some other  systems on the network, it isn’t better solution. Because, the contents  of these systems might be constantly updated every minute, and some  files may change during the rsync process. Say for example, when rsync  will reach the file 2, the contents of the previous file (File 1) might  be changed. This will leave you with a dependency error when you will  need to use that backup. In such cases, a snapshot-based backup is the  better approach. Because the system will get “froze” before the backup  process starts and get it “unfreeze” when the backup process finishes,  so all the files are consistent."
If I need give the source: [https://www.ostechnix.com/backup-entire-linux-system-using-rsync/](https://www.ostechnix.com/backup-entire-linux-system-using-rsync/)
Thanks.

You have to install Clonezilla to a CD or pen drive.

It can't be run from hard drive.

---

