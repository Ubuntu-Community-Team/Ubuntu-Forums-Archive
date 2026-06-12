---
title: "Feisty: missing /dev/hdc"
date: 2007-04-24
forum: General Help
---

### Post by mdurham on 2007-04-24
Hi, after a clean install I have the following line in my fstab file
> /dev/hdc 	/media/cdrom0   udf,iso9660 user,noauto     0       0
But, I don't have a /dev/hdc
Has anyone else had this problem or is it just me?
Do you have a /dev/hdc?  A simple 'yes' or 'no would suffice.
Cheers, Mike

---

### Post by dcstar on 2007-04-24
> **mdurham said:**
> Hi, after a clean install I have the following line in my fstab file

But, I don't have a /dev/hdc
Has anyone else had this problem or is it just me?
Do you have a /dev/hdc?  A simple 'yes' or 'no would suffice.
Cheers, Mike

/dev/hdc is an IDE Master device on the Secondary IDE channel on your MB, possibly a CD or DVD drive.

---

### Post by mdurham on 2007-04-24
> **dcstar said:**
> /dev/hdc is an IDE Master device on the Secondary IDE channel on your MB, possibly a CD or DVD drive.

Thanks for replying dcstar, but I knew that. What I wanted to know is do you actually have a FILE "/dev/hdc". I do have a DVD on the secondary IDE master but no "/dev/hdc" file. I wonder why the clean install would create an fstab file with a reference to a non existant file.

---

### Post by asipi on 2007-04-26
tip:
should be there if your optical drive acts like hdc but in some cases it will be used through udev and got another device in normal runtime like /dev/sdc but you can remove it from fstab in that case

could be an installation bug though

---

### Post by exoasol on 2007-05-02
I am having this same issue with feisty.  I dont have the /dev/hdc/ but my fstab is referencing it anyways.  Weird part for me is that it worked when I first installed feisty but not it doesnt work after I reinstalled feisty.  I know my drive is good because I just used it to install Ubuntu, and it worked fine under edgy

---

### Post by mdurham on 2007-05-02
I've noticed other posts with similar problems, some, like me,  had an LG drive. Is there a common factor here?

---

### Post by exoasol on 2007-05-03
im using an AOpen drive

---

