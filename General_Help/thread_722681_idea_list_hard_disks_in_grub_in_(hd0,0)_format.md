---
title: "idea: list hard disks in grub in (hd0,0) format"
date: 2008-03-12
forum: General Help
---

### Post by komputes on 2008-03-12
I'm not too sure where I should place this, but I was thinking of a novel idea for grub if it hasn't been done already. A way for the user to know which hard drives/partitions are available to the computer in a "(hd0,0)" format which can then be used in a menu.lst file. Am I wrong or is there no current way to list all  hard disks in this way. 

I'm guessing this would greatly save time and confusion in the grub configuration process.

---

### Post by Jimmey on 2008-03-12
I might be wrong, but I think the device.map in /boot/grub/ does this?

---

### Post by Shazaam on 2008-03-12
You can add anything you want in the "title" section of menu.lst. I used to have my Win XP title named Crap (pardon the vulgarity) so that when the grub list came up it looked like this.....
```
DSL
Puppy
Mepis
Ubuntu
Other Operating Systems
Crap
```
:)

---

### Post by komputes on 2008-03-12
@Jimmey- close, but no cigar... this shows your the drives but not the partition, grub requires (as it says in the subject) it to be "** in (hd0,0) format**".

```
$ cat /boot/grub/device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb
```What I am explaining would look like this:

```
$ grub --list-my-drives-in-your-language #this command doesn't exist
Checking disks...

                                 Mem  Used
(hd0)      /dev/sda
           (hd0,0)   /dev/sda1  50GB  25%
           (hd0,1)   /dev/sda2  50GB  25%

(hd1)   /dev/sdb
           (hd1,0)   /dev/sdb1  50GB  25%
           (hd1,1)   /dev/sdb2  50GB  25%
```--

@Shazaam : really? I call mine Windoze, with a Z because it puts me to sleep. i'll see if i can put a dollar sign in there and make it m$ windoze.... but, ah, how I do digress, that's off topic, seriously.

---

### Post by logos34 on 2008-03-13
> **komputes said:**
> @Jimmey- close, but no cigar... this shows your the drives but not the partition, grub requires (as it says in the subject) it to be "** in (hd0,0) format**".

```
$ cat /boot/grub/device.map 
(hd0)   /dev/sda
(hd1)   /dev/sdb
```What I am explaining would look like this:

```
$ grub --list-my-drives-in-your-language #this command doesn't exist
Checking disks...

                                 Mem  Used
(hd0)      /dev/sda
           (hd0,0)   /dev/sda1  50GB  25%
           (hd0,1)   /dev/sda2  50GB  25%

(hd1)   /dev/sdb
           (hd1,0)   /dev/sdb1  50GB  25%
           (hd1,1)   /dev/sdb2  50GB  25%
```--

Something like that would be nice.  Or at least a passing mention in menu.lst that Grub starts counting from 0 not 1 in its drive/partition designations--i.e. (hd0,1) = /dev/sda2, etc.  That confuses a lot of noobs.

---

### Post by komputes on 2008-03-13
Everyone who is new to linux would appreciate a command that will help them select or at least see how to correctly transport hard disk "locations" from a shell to a menu.lst.

Has something like this been done. If not, who would like to help me? How would I go about contacting the GRUB developers to see if this can be included in an upcoming version of the the grub shell.

---

### Post by logos34 on 2008-03-13
You might want to check the Grub2 project--wiki and development pages. Get on the mailinglist too.
[http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

Or contact Herman, author of the [grub page]("http://users.bigpond.net.au/hermanzone/p15.htm") (look for his posts in the Ubuntu Forums)

---

