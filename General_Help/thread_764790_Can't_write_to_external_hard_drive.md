---
title: "Can't write to external hard drive"
date: 2008-04-24
forum: General Help
---

### Post by ebp on 2008-04-24
Hi i have formated my external hard drive to ext3. When i try to write to it, this error comes:

[IMG]http://www.myupload.dk/showfile/44340fb81b.png[/IMG]

What can i do?

---

### Post by justleen on 2008-04-24
can you write to it as root?
```
sudo touch /media/disk/testfile
```

---

### Post by sweeneytodd on 2008-04-24
i don't know what i'm talking about, but i would of formatted it as ext2 as i think ext3 is for the root system, hope someone who knows can back that theory up for u. if not couldn't u make an extended logical partition out of it

---

### Post by ebp on 2008-04-24
> **justleen said:**
> can you write to it as root?
```
sudo touch /media/disk/testfile
```

I ran the command and a text file was created, so yes.

---

### Post by ebp on 2008-04-24
> **sweeneytodd said:**
> i don't know what i'm talking about, but i would of formatted it as ext2 as i think ext3 is for the root system, hope someone who knows can back that theory up for u. if not couldn't u make an extended logical partition out of it

OK, is ext2 better for storage? Because that's what I'm going to use i for.

---

### Post by rjl6591 on 2008-04-24
It's complicated, but essentially ext3 is better than ext2 because it has 'journaling', which assists recovery from an unclean shutdown (such as a crash or power failure). Ext3 is not just for root partitions - you can use it for your external disc drive. This is perfectly normal.

---

### Post by ebp on 2008-04-24
I've got another question, does the lost+found folder need to be there? And how do i "name" the hard drive?

---

### Post by AcerGemstone on 2009-05-07
First make a dir using sudo mkdir command
than copy data into hard disk
it works....................

:P:P:P:P:P:P

AcerGemstone
2 ghz, 3db ram

---

