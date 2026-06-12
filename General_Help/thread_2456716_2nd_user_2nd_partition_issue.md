---
title: "2nd user 2nd partition issue"
date: 2021-01-17
forum: General Help
---

### Post by ttwettlaufer on 2021-01-17
Alright gurus, 
Background: Ubuntu 20.04 base installation on 128Gb SSD with Home and Data on 4TB spinner. Did a generic install, but forgot to assign home drive to 4TB, no problem modified /etc/fstab. Works fine.

Problem: need to add a second user, added user, added to sudoers, login fine. Goto add new program "Can't create .foldername". Odd, Terminal pwd, returns "/". Ok, "ls" returns root folder no user or anything. Got it, temp user. Apparently it's not creating the users home folder on the second partition. Can someone tell me why? What am I doing wrong?

thanks,
tom

---

### Post by yancek on 2021-01-18
In what directory on the system were you when you got the error "Can't create .foldername"?  How did you try to create it?  Were you in the terminal using mkdir?  Your new user should have a directory in the /home directory with the user name.  As a user even with root/sudo privileges, you can't create new folders without sudo outside the user /home/user direcctory.

>  terminal pwd, returns "/". Ok, "ls" returns root folder no user or anything. 

The above indicates that you are in the root of the filesystem where users need sudo to do anything.  Your new user with sudo permissions won't be in the /root directory but in the /home directory.

>  Apparently it's not creating the users home folder on the second partition

Not sure why you would expect it to create the users home folder on another partition.

---

### Post by ttwettlaufer on 2021-01-18
Answers: I was in the home folder where the system has not created the user folder. sudo mkdir. yes, I like to use Cool Retro Term (cause I'm that old). no the system won't create the user folder, I'm guessing it's because the system is trying to create the user on the boot drive and that drive doesn't have enough space, therefore it logs me in with a tmp config. I can confirm this because any settings I change are not saved.
/ yes, I know this. 
second partition: I edited the fstab to point the home folder to the second partition, therefore it should create user folders there.

---

### Post by ttwettlaufer on 2021-01-19
OK, so I got it working. For some reason, I had to manually create the user folder and then chown it to the new user. But, some things are not quite working yet. Still investigating.

---

### Post by CelticWarrior on 2021-01-20
> **ttwettlaufer said:**
> But, some things are not quite working yet. Still investigating.

No surprise there, at all.
Moving /home isn't easy and has several steps that must be done, precisely.
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
After being successfully moved it should work as before, i.e., creating a new user automatically creates that new user's folder under /home with the correct permissions and all. Users shouldn't need to be hacking their way into it.
Please check the instructions above and compare them with what you did and didn't do.

---

### Post by TheFu on 2021-01-20
There are 2 commands to create a new userid. High-level ad low-level.  The low-level version only makes the paswd and group fle entries. It doe notng else. The high-level command creates a userid, groups, directory and copies the skel files into each HOME.

Alas, missed which command you ran. I always have to check the manpage to ensure I get the right cmd.  But if I get it wrong, manually doing those things isn't hard.  mkdir,cp, chown,chmod are the tools/skills needed.

---

