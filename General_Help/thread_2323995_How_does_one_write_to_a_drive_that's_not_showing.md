---
title: "How does one write to a drive that's not showing?"
date: 2016-05-10
forum: General Help
---

### Post by chris-burmajster on 2016-05-10
Hello,

How does one write to a drive that's not showing?

Chris Burmajster

---

### Post by Bucky Ball on 2016-05-10
*Thread moved to **General Help**.*

!?!? Hmm. Good question, and with so little detail hard to give much assistance. 

Internal or external drive? If external, how is it connected to the machine? How are you trying to find it? Please post back with this information and more, thanks. Please have a scan of the pink link in my signature at the bottom of this post.

---

### Post by chris-burmajster on 2016-05-10
OK, so it's an internal drive, connected to the machine, it's been formatted by Darik's boot and nuke. I'm trying to copy some backup stuff onto it.

---

### Post by Bucky Ball on 2016-05-10
I know nothing about Darik's boot or 'nuke', sorry. Which release of Ubuntu are you using? Do you have Gparted installed? Does it show in that? 

Please give the output of the following command

```
lsblk
```

* Just had a look at the Darik's Boot and Nuke page. Any reason you went that way? Easy way to wipe a drive for data storage, although may not do such a thorough job of eradicating all info if you wanted to retrieve it I suspect, is to use Gparted to erase all partitions then rewrite the partition table.

---

### Post by chris-burmajster on 2016-05-10
I'm using 16.04 and have Gparted installed. I'll check if it appears.

---

### Post by chris-burmajster on 2016-05-10
OK, it appears and I have formatted it. Now I need to copy stuff to it and it won't let me. What should I do?

---

### Post by Bucky Ball on 2016-05-10
Provide whatever message you are getting telling you you can't copy files. When you state you have formatted the drive, presuming  you mean you have created partitions on it? If so, I'm guessing permission on the partition are the problem.

If you have created partitions, open a file manager and they should show in the right hand column. Click one. Try to drag and drop a file into that folder. Report any error messages.

---

### Post by chris-burmajster on 2016-05-10
There are no error messages. If I try to drag and drop files from the drive onto the backup drive, it refuses them. I have just checked the permissions tab, it's all root. How do I change it to me?

---

### Post by Bucky Ball on 2016-05-10
Try this:

```
sudo chown -R username:username /path/to/folder
```

For instance, if your username is 'chris' and the partition is mounted at /media/chris/data, then:

```
sudo chown -R chris:chris /media/chris/data
```

---

### Post by chris-burmajster on 2016-05-10
Thank you, Bucky Ball. That's just what I needed!

---

### Post by Bucky Ball on 2016-05-10
Excellent news. ;)

Glad it worked and thanks for marking as solved.

---

