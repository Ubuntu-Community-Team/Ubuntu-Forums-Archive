---
title: "Lost administrative privileges after becoming standard user"
date: 2014-02-13
forum: General Help
---

### Post by michael2009 on 2014-02-13
Just finished reinstalling Ubuntu 12.04 on my HP laptop. I only have one 'first user' account, and for the purpose of better security I changed my account from 'administrator' to 'standard'. When I came to use the terminal I found my sudo password is not working anymore. I am guessing this is because I am now a standard user and therefore no longer a member of the administrator, or sudoers, group? 

I tried to change my account back to an administrator in user accounts, but I cannot unlock using the root password. I am locked out with no apparent solution. I have been looking at the documentation but haven't found anything that tells me how to regain administrative priviledges. Please help, someone?

---

### Post by Bucky Ball on 2014-02-13
*Thread moved to **General Help**.*

You might be able to fix things by booting the 'recovery' kernel (second on the list). When you get to the options choose 'drop to terminal as root' or whatever it is labelled as. 

You can change your permissions and groups there.

---

### Post by deadflowr on 2014-02-14
Yep, follow Bucky Ball's advice and boot into the recovery mode.
Then from there you'll need to remount the file system as rw(read/write)
(if you've ever done the [reset password]("http://www.psychocats.net/ubuntu/resetpassword") before, it is the same way)
```
mount -o rw,remount /
```
otherwise it'll be mounted read-only.
then from here simply run
```
adduser username sudo
```
change username to the user's name.
.Once done, you'll be back in.

---

### Post by michael2009 on 2014-02-14
OK thanks. Do you have the codes for resetting the user account as administrator?

---

### Post by michael2009 on 2014-02-14
> **deadflowr said:**
> Yep, follow Bucky Ball's advice and boot into the recovery mode.
Then from there you'll need to remount the file system as rw(read/write)
(if you've ever done the [reset password]("http://www.psychocats.net/ubuntu/resetpassword") before, it is the same way)
```
mount -o rw,remount /
```
otherwise it'll be mounted read-only.
then from here simply run
```
adduser username sudo
```
change username to the user's name.
.Once done, you'll be back in.

deadflowr thank you (I have a very slow connection and I did not see your post until I had posted mine). I'll let you know how I get on.

---

### Post by deadflowr on 2014-02-14
> **michael2009 said:**
> deadflowr thank you (I have a very slow connection and I did not see your post until I had posted mine). I'll let you know how I get on.

No worries, my command above will at least get you back into sudo.
Any other groups needed can be added later.
you can run the command
```
id
```
to see what groups you are in.

---

### Post by michael2009 on 2014-03-03
Hi deadflowr (nice name but makes me sad :( ... ) 

My deepest apologies for not getting back to you like I promised. Too many current computer issues made me forget. Many thanks for your helpful and easy step by step instructions. Best Regards.

---

