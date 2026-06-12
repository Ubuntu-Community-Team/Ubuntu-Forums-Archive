---
title: "Help installing Truecrypt to de-crypt HDD from a windows installation of TC"
date: 2016-02-21
forum: General Help
---

### Post by PsychedelicWonders on 2016-02-21
So I have a HDD that I originally encrypted with Truecrypt on Windows 7

I could have sworn I searched Ubuntu software center and there was a TC version to be installed?

Now There is something call Free and Simple Truecrypt implementation?

So how can I de-crypt my TC HDD so I can gain access to all of my files?

I plan on moving all of my data (songs/pics/videos/files etc) from the HDD to a Samsung SSD shortly and plan on enabling Samsungs built in hardware encryption via bios with an ATA password.

---

### Post by PsychedelicWonders on 2016-02-24
Bump...

---

### Post by PsychedelicWonders on 2016-03-18
Anyone at all?

---

### Post by LukeMorrison on 2016-03-18
Here are some links to the last full-featured version of TrueCrypt:

[http://andryou.com/truecrypt_orig/downloads/](http://andryou.com/truecrypt_orig/downloads/)
[https://www.grc.com/misc/truecrypt/truecrypt.htm](https://www.grc.com/misc/truecrypt/truecrypt.htm)

---

### Post by SuperFreak on 2016-03-18
You might be better off using Veracrypt which is still being updated and maintained. It can decrypt Truecrypt containers and partitions
[https://veracrypt.codeplex.com/](https://veracrypt.codeplex.com/)
It is a fork of Truecrypt

---

### Post by PsychedelicWonders on 2016-03-18
> **SuperFreak said:**
> You might be better off using Veracrypt which is still being updated and maintained. It can decrypt Truecrypt containers and partitions
[https://veracrypt.codeplex.com/](https://veracrypt.codeplex.com/)
It is a fork of Truecrypt

Ok, this might work then.  Am I able to add/delete files off of the drive while using Veracrypt?

I don't plan on using software encryption much longer, will move over to SSD hardware encryption, so it's just a temporary situation until I migrate all data from my truecrypt HDD to a new Samsung SSD

---

### Post by PsychedelicWonders on 2016-03-18
Ok so I downloaded Veracrypt, any help on getting it installed?  I'm new to being back to Ubuntu so rusty...

Seems there's 4 files within the download

---

### Post by SuperFreak on 2016-03-18
Extract the files from the tar file using Archive Manager, then open Terminal and drag veracrypt-1.17-setup-gui-x64 file into terminal(assuming your PC is 64bit). It should be straightforward from there.

---

### Post by PsychedelicWonders on 2016-03-18
Hmm, getting this error message:

There was a problem opening the file &#8220;/home/jxxxxxxx/Desk&#8230;acrypt-1.17-setup-gui-x64&#8221;.
The file you opened has some invalid characters. If you continue editing this file you could corrupt this document.
You can also choose another character encoding and try again.

I had this same error/problem when trying to open/install truecrypt as well.

---

### Post by SuperFreak on 2016-03-18
Not sure what the problem is. What version of Ubuntu are you using and is it 64bit?

You are using the Linux version of Veracrypt right?

EDIT: I think I see the problem. When you extract the files use Extract Here by right clicking on the tar file rather than using Archive manager. I think it is a permissions issue

---

### Post by SuperFreak on 2016-03-18
Are you opening the file or as I suggested dragging it into the terminal interface?

---

### Post by psychedelicwonders2 on 2016-04-08
Hey sorry, didn't see you reply to this thread.

I extracted the  file to my desktop originally, now I have a veracrypt-1.17.setup folder  on my desktop and inside of that there are these 4 files:

[ATTACH=CONFIG]268256[/ATTACH]

So you're saying I need to right click on that 3rd file or drag it into the terminal?  

The last time I tried to drag it into the terminal it ran a sequence for a few minutes but then gave me the error message of:

There was a problem opening the file “/home/jxxxxxxx/Desk…acrypt-1.17-setup-gui-x64”.
The file you opened has some invalid characters. If you continue editing this file you could corrupt this document.
You can also choose another character encoding and try again.

---

### Post by SuperFreak on 2016-04-08
Sorry I do not know why it won't run in terminal

---

