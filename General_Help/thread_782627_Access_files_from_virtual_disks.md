---
title: "Access files from virtual disks"
date: 2008-05-05
forum: General Help
---

### Post by dcomsa on 2008-05-05
Hi everybody,

I have searched the forums, but didn't find info on this matter.

My question: Can I access Linux (installed with Wubi) files from Windows?

Thank you,
Daniel.

---

### Post by Arasfang on 2008-05-05
Yes there are applications for windows that adds support for Linux drives. But I think it depends a little on what FS type the linux partitions are.

[http://www.fs-driver.org/](http://www.fs-driver.org/) 

There you can find some app to read ext2 at least as I understand.

/Mattias

---

### Post by dcomsa on 2008-05-05
Hi Mattias,

Thanks for your reply. The type of software you've mentioned is for an dual boot environment, where Linux has his own partition(s). In my case, Linux is installed on an NTFS partition, in an virtual disk file (eg: D:\Ubuntu\disks\root.disk). I would like to know if I could "mount" this virtual disk file under Windows, and access files from it.

Thanks,
Daniel.

---

### Post by Arasfang on 2008-05-05
Hmm I think that can be a problem to do. Do you mean you are running some kind of virtual machine ( VMware etc. )?

/Mattias

---

### Post by dcomsa on 2008-05-05
No, it's a standard install using Wubi. See more here: [http://wubi-installer.org/](http://wubi-installer.org/)

Daniel.

---

### Post by Arasfang on 2008-05-05
Oh, I have never tried such an installation so I guess I cant help you then :(

Good luck!

/Mattias

---

### Post by dcomsa on 2008-05-05
No problem. Thanks anyway :)

Daniel.

---

### Post by ago on 2008-05-05
Yes there are applications and were suggested here before (do not remember the thread though).

Wubi uses ext3 but whatever app you use has to be able to work off a real device as well as off a file.

---

### Post by Arasfang on 2008-05-06
Hmm when reading around about wubi I found a link to an application which seems to be able to read .disk-files.

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

Hope it helps.

---

### Post by dcomsa on 2008-05-06
Thanks mate, this could be what I was looking for. After reading the info about that software, this line sounds very promising "The program can create and open images of Ext2/Ext3 disks."

I will give it a shot later, right now I'm on Linux and have some work to do, but I will post the end result here.

Thanks again,:)
Daniel.

---

### Post by ago on 2008-05-06
If it works well please feel free to add a reference to the WubiGuide.

---

### Post by dcomsa on 2008-05-18
Sorry it took so much to answer, but I was quite busy and didn't user Windows lately.

So the program suggested by Mattias ([http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)) does work.

@ago: I don't really know how to add it to WikiGuide.

---

### Post by help_me_please on 2008-05-18
related question:
is it possible to access the windows directories and files from within wubi?

---

### Post by dcomsa on 2008-05-18
Theoretically wubi should recognize your windows partitions. The should be under Places menu.

---

### Post by help_me_please on 2008-05-18
i do have a drive called WINRE in places that contains windows folders, but its a mock drive, somewhat similer to wine's C:\ drive.

---

### Post by ago on 2008-05-18
windows files should be available under /host

---

### Post by burnfreak on 2008-05-19
[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

This one also works, though it only allows reading.

---

