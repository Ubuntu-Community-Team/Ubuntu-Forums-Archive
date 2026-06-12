---
title: "Username and Password"
date: 2007-08-11
forum: General Help
---

### Post by jhbroge on 2007-08-11
Okay, I installed wubi and installed the ISO onto the virtual drive. I have installed Ubuntu many times in the past onto dedicated partitions and have been prompted to enter a desired username and password for an account. I was not prompted during this installation for such. Is there a [I]default[I] username and password for this install? Or do I have to reinstall everything, including the virtual disk and ISO?

Thanks,

Jeff

---

### Post by ago on 2007-08-13
> **jhbroge said:**
> Okay, I installed wubi and installed the ISO onto the virtual drive. I have installed Ubuntu many times in the past onto dedicated partitions and have been prompted to enter a desired username and password for an account. I was not prompted during this installation for such. Is there a [I]default[I] username and password for this install? Or do I have to reinstall everything, including the virtual disk and ISO?

Thanks,

Jeff

Use wubi 7.04.04

---

### Post by ade52 on 2007-08-17
Hi to all,

I have got the same problem but I'm using the version refered to, if this was supposed to correct any problems could you please advise further, 
otherwise I can't use it.

Thanks.

---

### Post by ago on 2007-08-17
If you are using 7.04.04 try to use a simple username and password (you can change that later). Like: ubuntu

---

### Post by ade52 on 2007-08-17
Hi,

Thanks for replying.

I think what we have here is catch 22, we are being asked to login with details which should have been previously entered, we where unable to do this as  jhbroge had pointed out in his thread, cosequently we cannot satisfy the login proceedure becuse whatever we put in, it wiil not have those details to compare and verify are correct.

What I think should happen, is that the option given to enter the required details which is in the Live CDs, should be implemented in the Wubi installation problem solved, however this does not resolve this problem, so it looks like I will have to uninstall and download the Live CD, unless you can suggest a less time consuming alternative.

Thanks.

PS Could you please consider installing a spell checker in your forum.

---

### Post by ago on 2007-08-17
Hmmm not sure what you mean. You are asked to enter username and password by the wubi installation wizard

[img]http://wubi-installer.org/images/wubi.png[/img]

Then you login with username and password you used there. There used to be a bug in old version (it would stop during the installation process asking again for username and password). That has been fixed in 7.04.04.

---

### Post by ade52 on 2007-08-17
Hi

Thanks for replying, I must apologize for waisting every bodies time and the Wubi comments, :oops:

Thanks.

---

### Post by jwa2015 on 2007-08-18
I have another problem guys. I installed Ubuntu through Wubi. When I rebooted for the 1st time, the installer started.

In the middle of the process, I got a message in the Ubuntu Installer Main Menu that says "Invalid Username". 

I was never prompted to enter a password or a user name during this process. I know the user name I entered but never been asked.. escaping this takes me to a list of installation processes. Then back again to same screen. help!!!!!

---

### Post by ago on 2007-08-18
did you use version 7.04.04?

---

### Post by kuddo on 2007-08-28
sry for being a noob](*,)... i wasn`t very careful at the username in wubi...can u tell me what is the default username pls?#-o

---

### Post by tuxcantfly on 2007-08-28
> sry for being a noob... i wasn`t very careful at the username in wubi...can u tell me what is the default username pls?

It's whatever you typed in. There is no "default username". If you can't login, just boot up the recovery mode (press esc right after selecting the Ubuntu boot option), then do "adduser ubuntu" or whatever username you want, give it a password (passwd ubuntu) and you'll be able to log in afterwards.

---

### Post by kuddo on 2007-08-28
i did how u`ve said...but when i enter the command line the adduser command and passwd are not recognized :(

---

### Post by tuxcantfly on 2007-08-28
> **kuddo said:**
> i did how u`ve said...but when i enter the command line the adduser command and passwd are not recognized :(

That sounds weird... exactly what is the error message? Also, you DID boot into recovery mode right ("echo $USER" returns "root" right?), you're not trying to enter those commands into the grub prompt right? Also, you aren't entering the commands with the quotes right?

---

### Post by Eckes on 2007-08-29
If that of any help: I had some problems too concerning the password I entered in Wubi, till I remembered the differences in keyboards. For the german one, I just changes all "Y"s to "Z" and vice versa.

---

