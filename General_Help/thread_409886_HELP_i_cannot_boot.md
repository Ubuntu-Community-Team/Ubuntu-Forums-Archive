---
title: "HELP i cannot boot"
date: 2007-04-15
forum: General Help
---

### Post by pappy on 2007-04-15
Hello 
I have a huge problem since i cannot boot to my system. When i try to boot i get this message

Cannot initialize /etc/mtab
/etc/rcS.d/S20checkroot.sh: 407: rm: permission Denied
init: Unable to execute "/bin/sh" for rc-default Permission Denied
init: rc-default process (3545) terminated with status 1
[17179603.916000] sdc: assuming drive cache: write through
[17179603.920000] sdc: assuming drive cache: write through

I can understand is something with mounting the hard drive.The problem is that i don't know how to fix! Please help as i need the pc to do some work!
BTW i have the Kubuntu Live CD if that can be of any help.
Thank you

---

### Post by pappy on 2007-04-15
Hello anyone can help please?

---

### Post by depu on 2007-04-15
looks like there is another discussion about the same error on the forums

[http://ubuntuforums.org/showthread.php?t=403083&highlight=init%3A+Unable+to+execute+%2Fbin%2Fsh+for+rc-default+Permission+Denied](http://ubuntuforums.org/showthread.php?t=403083&highlight=init%3A+Unable+to+execute+%2Fbin%2Fsh+for+rc-default+Permission+Denied)

---

### Post by pappy on 2007-04-15
I checked the thread but nothing useful! any ideas?
BTW I'm using Kubuntu 6.10 and i have a Live CD if this can be of any help.
At least someone tell me if there is a fix or i have to install again Kubuntu again and if this is the case
will i lose all my files i have from the previous installation?
thank you

---

### Post by Sef on 2007-04-15
> At least someone tell me if there is a fix or i have to install again Kubuntu again and if this is the case
will i lose all my files i have from the previous installation?

1) Have patience, please.  Sometimes the person who can answer your thread is sleeping or working now.

2) Are your files on a separtate home partition?  If they are then there should not be a problem.  If they are not, then you could use the Live CD to back them up to a Flash Drive.

---

### Post by pappy on 2007-04-15
My files are in my home folder which is (if i remember correctly) something like
home/user/
In there i have separate folders for work, downloads etc
The problem is that i have some very big files. Is it possible to copy them to a dvd with
live cd?
thx

---

### Post by pappy on 2007-04-15
I manage to copy all my files using SimplyMepis live CD which i think i'm going to install

---

### Post by confused57 on 2007-04-15
> **pappy said:**
> I manage to copy all my files using SimplyMepis live CD which i think i'm going to install

Glad you were able to recover your files, SimplyMepis is an excellent distro and you may also want to consider
PCLinuxOs(or at least the live cd).  I saw your initial post, but I wasn't sure what you needed to do to correct your /etc/mtab error...it's been my experience, if fstab is edited, mtab is automatically updated.

---

### Post by pappy on 2007-04-15
Ok i don't want to erase kubuntu since i like it very much. The problem is that i can't boot anymore. I get the message in the first post. Can you tell me how to fix this if there is a fix?

---

### Post by confused57 on 2007-04-15
> **pappy said:**
> Ok i don't want to erase kubuntu since i like it very much. The problem is that i can't boot anymore. I get the message in the first post. Can you tell me how to fix this if there is a fix?

Kubuntu would probably be the best choice, especially with the excellent community support here in the forum.
Since you have all your data backed up, you might want to reinstall, but create a separate /home partition...this way, you'll still have all your settings and data if you have to reinstall.

What do you think may have caused your system to fail to boot?  Maybe a recently installed program, a hard shutdown, power failure, or another change  could have caused it.

You can use the live cd to mount your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)
since you're using kde, you'd use kwrite instead of gedit

you could investigate your /etc/fstab file & /etc/mtab as well...I don't really have any specific advice that might help you...good luck.

---

