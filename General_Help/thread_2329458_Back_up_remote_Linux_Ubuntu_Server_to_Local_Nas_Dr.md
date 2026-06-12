---
title: "Back up remote Linux Ubuntu Server to Local Nas Drive"
date: 2016-07-02
forum: General Help
---

### Post by nighttraindb on 2016-07-02
Hello, I attempted to ask this question earlier.  However it appears I somehow did not post it correctly.
I am -- completely-- new to Ubuntu and desperately need the instructions to do a -- single-- backup
of my remote server to my nas drive.

I can log in through terminal or ftp   just don't know what to do after the terminal log in.

The commands...

Thanks for any help anyone can provide

---

### Post by HermanAB on 2016-07-02
And as usual, the answer is not simple.

With a server one needs to see what services are running and back them up separately, since for each one the process will be different.  You need to be especially careful when there are paid services running on it.  If you can halt a whole server to do a backup, then it isn't really a server...

---

### Post by nerdtron on 2016-07-02
> **nighttraindb said:**
> Hello, I attempted to ask this question earlier.  However it appears I somehow did not post it correctly.
I am -- completely-- new to Ubuntu and desperately need the instructions to do a -- single-- backup
of my remote server to my nas drive.

I can log in through terminal or ftp   just don't know what to do after the terminal log in.

The commands...

Thanks for any help anyone can provide

As stated by HermanAB, the is no single answer to your question because the answers can vary depending on your setup.

Some question which you can answer to help find direction to your question.
What is the OS version? Is it a Physical or Virtual Machine? Is it located on your local network or on the cloud? 
Does the local NAS have direct connection to the Ubuntu Server?
What part of the server do you want to backup? Some data files/folder only or the whole server?
Do you want to automate the backup to run it regularly or you just want to run it manually?

---

### Post by steeldriver on 2016-07-02
Hello and welcome to the forums

I assume by "single" you mean this is a one-off (or at least, not regularly scheduled) operation.

Probably one of the things you should be looking at is the **rsync** program. You could mount the NAS on your local machine (if you have not already done so) and then use rsync (which uses SSH under the hood) from the local machine to connect to the remote server and copy the content

However as others have noted, you will first need to decide exactly what files/directories you want to back up

---

