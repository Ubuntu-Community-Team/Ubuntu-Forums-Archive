---
title: "Move data to External drive"
date: 2006-10-22
forum: General Help
---

### Post by boris357 on 2006-10-22
I am trying to copy or move some data files to an external USB hard drive but with no success. Do I have to chage permissions to do this? When I try to copy data to the drive I get the following message, " You do not have permissions to write to this disk". How do I chage the permissions? Do I have to go to the terminal and use chomod? If so, what switches do I use as I have not used linux in some time and have forgotten some of the commands.

Thank you.

---

### Post by DaveBorealis on 2006-10-22
Hello Boris,

One way is to open a terminal, cd to the mount directory, and chmod 777 <mount directory>.  Now anyone will be able to read/write to the hard drive.

A second way, still in the terminal, is to 'sudo cp <files> /path/to/<mount directory>

Best regards,
Dave

---

### Post by boris357 on 2006-10-22
Hello Dave.

It worked. Just trying to remember all of those commands in terminal mode is a bit trying. By the way. How do I lock out the drive for write access? Just thought I would ask. I might need to in a moment of decision.

Thank you and best regards

Larry (boris357)

---

### Post by DaveBorealis on 2006-10-23
> **boris357 said:**
> How do I lock out the drive for write access? Just thought I would ask. I might need to in a moment of decision.

There are a couple ways to keep people from writing to the drive.  The quickest is to

sudo chmod 755 <mounted directory>

and everyone would be able to read from it, but only root would be able to write to it.  If you want absolutely no one to write to it, but for everyone to read from it, then

sudo chmod 555 <mounted directory>

Dave

---

