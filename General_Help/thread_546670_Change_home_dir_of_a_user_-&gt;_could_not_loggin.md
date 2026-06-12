---
title: "Change home dir of a user -&gt; could not loggin"
date: 2007-09-09
forum: General Help
---

### Post by vhv_alex on 2007-09-09
Hi there !

First of all, I have to say that Ubuntu is the best choice of Linux Os for me right now. Because I am new with Ubuntu so I have some questions about it:

I have installed Ubuntu 7.04 on my PC, it worked very smoothly until I changed the home dir of my user account ( a main account created when Ubuntu was being installed )

The original home dir is : /home/xxxyyy/

So I changed to /  and then I could not log to Ubuntu anymore.

It said that the home dir was wrong and need to be corrected ( I can not remember the exact error message, but it meant that )

How can i reset the home dir ? 

Any suggestions are very appreciated, thank you in advance 

P/s: please forgive me if there are some similar threads about this.

---

### Post by jocko on 2007-09-09
I'm not absolutely sure about this, but I'm sure its worth a try.
First boot into recovery mode (press escape when grub loads to see the boot menu, select a line that ends with "(recovery mode)" and press enter).
Now you should get a command line interface and logged in as root.

Type this command (change "username" to your real username):
```
adduser --home /home/username username
```If I understood the adduser manual, this should fix things for you.
To avoid this in the future:
Your home directory needs to be somewhere where you have read/write acces, otherwise you'll not be able to login or store any settings, that's why it should always be in a subdirectory in /home/.

---

### Post by bettlebrox on 2007-09-09
U have to change /etc/passwd to point to the new location of the home directory. If you edit the file, make a backup copy first because if you make a mistake no-one will be able to login.

---

### Post by rbprogrammer on 2007-09-09
> **vhv_alex said:**
> 
...
The original home dir is : /home/xxxyyy/

So I changed to /  and then I could not log to Ubuntu anymore.
...


lol, i have not heard of anyone trying to make the home directory [FONT="Courier New"]/[/FONT], but since you said you were new, i will let that one slide :lolflag:

but **jocko** is correct when he said that you need read/write permissions and to make the home directory in [FONT="Courier New"]/home/[/FONT].  to me it not only provides the read/write access permissions, but it also help organize the system..

---

### Post by vhv_alex on 2007-09-09
Thank you all

@jocko : thank you for your suggestion, I will try to follow 

> lol, i have not heard of anyone trying to make the home directory /, but since you said you were new, i will let that one slide

Thanks, make the errors occur and then find a way to fix them, I think that one of the good ways to learn new thing :guitar:

---

### Post by vhv_alex on 2007-09-09
It worked.

After added new user, I maked it a new admin by this command

udo usermod -a -G admin username

Thanks all.

---

### Post by jhollett66 on 2007-10-16
I did a similar thing, I changed my home directory from john to johnathan in user properties and couldn't log in on reboot.  The problem was fixed by going into the failsafe terminal and editing /etc/passwd, changing /home/johnathan back to john.  Thanks for the info in this thread!

---

