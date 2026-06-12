---
title: "root auto-login in ubuntu"
date: 2008-02-07
forum: General Help
---

### Post by Mr.Johnny on 2008-02-07
Hi!

Is there a way of enabling root auto-login in ubuntu?

Thanks.

---

### Post by jrib on 2008-02-08
that's a terrible idea.  Why would you want to do this?

---

### Post by seventhc on 2008-02-08
You can make it so you don't have to login at the login screen, but thats for the user account. Having root do an auto login is insane.

---

### Post by Mr.Johnny on 2008-02-08
Hi...

I wouldn't say it's insane or a bad idea, I would say it's not recommended in some cases, but in this case I really need not to care about permissions. Not everybody uses linux for the same purposes, but I understand that that is the main philosophy of it.  ;) But I don't want to discuss that, I assure you that even being a linux newbie, I know what I want to do and I am sure I (don't) need this.

(just to explain, in this case it's not a networking machine, it will only be operated by me, with a very specific purpose - In fact, once setup I intend that my only physical interaction with it will be only pressing the power button for on and off :lolflag:)

I found a workaround, which allows me to run my configuration scripts with the sudo command without being asked for a password, that is editing the /etc/sudoers file, but I still have to login with a different user and I would still love to have the auto-root login. 

Thanks

---

### Post by jrib on 2008-02-08
If you tell me the exact use-case that requires it, and it is clear that it actually does require it, I will find out how to do so and tell you.  What exactly would make you think this is necessary?

---

### Post by bodhi.zazen on 2008-02-09
> **Mr.Johnny said:**
> Hi!

Is there a way of enabling root auto-login in ubuntu?

Thanks.

The short answer is yes, it is possible. You will need to edit some source code and recompile some things.

There is no need to do this on Ubuntu and it is not directly supported on these forums. AS you can see it is discouraged.

If you want to run as root, use sudo. You can use sudo -i to get a root shell.

A solution was posted here : [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=669785](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=669785)

I am going to close this thread to prevent further flaming ...

---

