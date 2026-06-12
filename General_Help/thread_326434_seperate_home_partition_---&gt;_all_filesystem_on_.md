---
title: "seperate /home partition ---&gt; all filesystem on same partition"
date: 2006-12-27
forum: General Help
---

### Post by Portable_Jim on 2006-12-27
During installation, I chose my /home folder to be on a different partition. Does anyone know how to get it back to being on the same partition as the rest of my file-system??

---

### Post by KenSentMe on 2006-12-27
There might be a way to do it.

Copy all the files in /home to a folder on the main partition (not home).

Type sudo unmount /home in console

Edit fstab with: gksudo gedit /etc/fstab

Remove the line on which the partition is mounted on /home

Now create a new home folder with: sudo mkdir /home

Copy all the files from you original homedir (stored somewhere on the main partition) to the new /home.

If i'm right your system will work as before. However, BE SURE TO MAKE BACKUPS!

Question:

Why do you want to remove the partition and move /home to the main partition?

---

### Post by Portable_Jim on 2006-12-27
> **KenSentMe said:**
> There might be a way to do it.

Copy all the files in /home to a folder on the main partition (not home).

Type sudo unmount /home in console

Edit fstab with: gksudo gedit /etc/fstab

Remove the line on which the partition is mounted on /home

Now create a new home folder with: sudo mkdir /home

Copy all the files from you original homedir (stored somewhere on the main partition) to the new /home.

If i'm right your system will work as before. However, BE SURE TO MAKE BACKUPS! 
Thanks.I'll try that. 
> **KenSentMe said:**
> 
Question:

Why do you want to remove the partition and move /home to the main partition?
TO have the full partition available - I am experimenting with VMware, but also free for the system to take if it gets too bloated.

---

### Post by Portable_Jim on 2006-12-28
Look at that (pause) it works!! :) Thanks

---

