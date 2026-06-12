---
title: "File corruption after copy"
date: 2016-08-11
forum: General Help
---

### Post by James_S on 2016-08-11
Hi all, 

Something very strange happened to me on my Toshiba Chromebook 13 (Gen 1). I have ubunutu installed with XFCE4, am not sure if is xubunutu or not, I followed the instructions to install linux using crouton from this page: 

[http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/](http://www.howtogeek.com/162120/how-to-install-ubuntu-linux-on-your-chromebook-with-crouton/)

I was copying (using windows manager copy) some photographs from an SD card to an external hard drive when something went wrong with the copy. An error message came up and in my stupidity I just dismissed it thinking nothing of it. I actually found that is corrupted the whole directory structure which I was copying into. For example I was copying into this directory: 

E/Photos/backup 

It corrupted everything in Photos. 

Using windows repair disk tool I was able to recover all my files in Photos apart from backup. I have also tried using my mac disk utility to repair the disk and although it detected errors, repaired them and worryingly freed up some space it didn't recover the backup directory. Before running the disk utility I also ran a program called recuva (it detects deleted files for recovery) to see if I could get anything, although that didn't see to work. 

So my questions after quite a long post: 

1. Does anyone know why this has happened? 
2. Any ideas on how to fix it and get my data back? 
3. Is there any way I can see the error message that popped up? maybe stored in a log file? 

Thanks for everyone's help in advance

Many thanks 

James

---

### Post by coldraven on 2016-08-11
> I was copying (using windows manager copy) some photographs from an SD card to an external hard drive

I'm a bit confused, what has the Chromebook got to do with a Windows error? Also E/Photos/backup is not a valid Windows pathname.

---

### Post by James_S on 2016-08-11
> **coldraven said:**
> I'm a bit confused, what has the Chromebook got to do with a Windows error? Also E/Photos/backup is not a valid Windows pathname.

Apologies for the confusion:

1. When I said windows manager - I meant the GUI as in XFCE interface (apologies windows manager is a incorrect way of stating this)
2. With regards to path that was just an example not a valid path, so that I could properly explain the that the corruption of the directory was both to the directory which the files were to be copied in and the directory above that

---

### Post by coldraven on 2016-08-11
OK we are getting nearer a fix. AFAIK the file manager in XFCE is called Thunar. You can find out by launching the file manager and then in the file menu click on "Help > About".
As for recovering your photos you could try PhotoRec. It is installed as a pair of utilities by this command:
```
sudo apt install testdisk
```
Be aware that this is a command line program, there are no pretty windows. Its also a super powerful tool.
So open a terminal (ctrl+alt+T) and type "photorec".

It's a bit technical but here is the link to the author's web-site.
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

---

### Post by James_S on 2016-08-12
Thanks @coldraven.

I downloaded photorec for windows 10 and I ran the qphotorec tool which seemed to be a GUI for the photorec tool. 

I left it running overnight and it had done 0% of the recovery so I was little worried it wasn't working.

---

### Post by coldraven on 2016-08-12
> I left it running overnight and it had done 0% of the recovery so I was little worried it wasn't working.
That does not sound very good. Any luck?

---

