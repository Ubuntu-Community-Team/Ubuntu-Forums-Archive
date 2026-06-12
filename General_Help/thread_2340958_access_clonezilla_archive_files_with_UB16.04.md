---
title: "access clonezilla archive files with UB16.04?"
date: 2016-10-23
forum: General Help
---

### Post by davehenson on 2016-10-23
Hello, 
I am manking the change back to Ubuntu 16.04 LTS from Fedora23.  I backed up my Fedora install using the default options in CloneZilla to an external USB drive. With Fedora I never had issues browsing the backups made before.  Now that I have UB16.04 installed, I go to access the backup files and cannot open them. I wouldn't think I would have to extract them (they appear to be gz files). 

Wondering what support I need to install to have the same functionality as I did when I was using Fedora. 

screenshot attached & thank you for your help and sharing 
[ATTACH=CONFIG]271765[/ATTACH]

---

### Post by davehenson on 2016-10-23
Here's the screenshot of the error when I try to open one of the archive files.
[ATTACH=CONFIG]271766[/ATTACH]

---

### Post by davehenson on 2016-10-24
polite bump.  

My guess is there is some type of file support missing but I am unsure how to determine which. Any ideas along that train of thought?

---

### Post by sudodus on 2016-10-25
I saw your thread, but I don't know any solution to your problem.

I have used Clonezilla for years but have not tried to use the Clonezilla backup files with any other tool (except Clonezilla itself).

I use a dual strategy for backup.

1. Once in a great while I make a complete image of the whole drive with ***Clonezilla***.

2. I backup my personal files in a data directory and also the home directory with its configuration files without compression (with ***unison*** and ***rsync***).

When I need a file from backup, I grab it directly from the backup, which is not compressed, so I can recover it very quickly.

---

### Post by davehenson on 2016-10-25
> **sudodus said:**
> I saw your thread, but I don't know any solution to your problem.

I have used Clonezilla for years but have not tried to use the Clonezilla backup files with any other tool (except Clonezilla itself).

I use a dual strategy for backup.

1. Once in a great while I make a complete image of the whole drive with ***Clonezilla***.

2. I backup my personal files in a data directory and also the home directory with its configuration files without compression (with ***unison*** and ***rsync***).

When I need a file from backup, I grab it directly from the backup, which is not compressed, so I can recover it very quickly.

Hey its ok if you don't know the answer!  Just that you replied helps me & maybe others think about a problem more and gets the the brainstorm going. 

I don't believe (but not positively certain) that the default backup settings use any compression. but then they are gz files.  hmmmm.......   This afternoon I'll restore a fedora image and see if I can then browse the backups. I'm thinking I could from Fedora. Will post my findings then.

---

### Post by davehenson on 2016-10-25
Update - restored Fedora and I cannot browse my clonezilla backups. I was incorrect before. Next plan is to change my backup scheme to backup only the /home dir from now on as others have mentioned.

---

### Post by sudodus on 2016-10-25
It may be a good idea to start a new thread with a good desciptive title to discuss or get help to select a good backup strategy and a suitable tool for it. You can start by looking at this link and links from it,

[Backup Your System](https://help.ubuntu.com/community/BackupYourSystem%20)

---

