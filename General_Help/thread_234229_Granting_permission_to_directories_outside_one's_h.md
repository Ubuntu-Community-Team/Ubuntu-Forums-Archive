---
title: "Granting permission to directories outside one's home"
date: 2006-08-11
forum: General Help
---

### Post by okok on 2006-08-11
Can I grant a normal (non-root) user full permissions to access some directory (and all its content) outside  its own home directory without making the directory 777?

---

### Post by zxee on 2006-08-11
You could change ownership of the directory and it's contents.
From terminal> sudo chown /somdirectory
See wiki chown: [http://en.wikipedia.org/wiki/Chown](http://en.wikipedia.org/wiki/Chown)
That might cause problems with some directories though.
You could add the user to the group the directory belongs to.
[http://www.linuxcommand.org/man_pages/useradd8.html](http://www.linuxcommand.org/man_pages/useradd8.html)

---

### Post by okok on 2006-08-11
Thanks. It seems that I don't understand something very basic. My actual problem is this.

In addition to the normal root and home directories, I have additional partitions. Their entire content belongs to group root and user root. I can change these files only as root, and would like to be able to access them freely as a normal user.

when I type as root

[FONT="Courier New"]chown -R someuser /mountpoint[/FONT]

for each file I get the following message: 

[FONT="Courier New"]chown: changing ownership of `/mountpoint/somedir/somefile': Operation not permitted
[/FONT]

What am I doing wrong?

---

### Post by patbuntu on 2006-08-11
Did you try:

> 
**sudo** chown -R someuser /mountpoint


-pat

---

### Post by MrHorus on 2006-08-11
You have to specify the user's group AND their username.

The username and group are generally the same so try:

```
chorn -R someuser:someuser /somedir
```

---

### Post by Ramses de Norre on 2006-08-11
Are this linux filesystems on the partitions? Otherwise this method wont work..
And defining the username only should do it too.. But you definately have to use sudo.

---

### Post by okok on 2006-08-11
Thanks. I did not use sudo because the first thing I do when I instaled ubuntu was to enable normal root access.

The filesystem on the partition I am trying to access is not a linux filesystem. This is a fat32 partition, which must also be accessible from a windows OS installed on the same computer. Does this mean it can only belong to root?

---

### Post by Ramses de Norre on 2006-08-11
No, that means you need to include ```
umask=0000
``` as option in the line for the partition in /etc/fstab to make it rwx for everyone.

---

### Post by okok on 2006-08-11
Thank you! this is exactly what I was looking for. Problem solved.

---

