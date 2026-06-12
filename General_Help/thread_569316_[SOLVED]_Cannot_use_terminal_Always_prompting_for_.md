---
title: "[SOLVED] Cannot use terminal: Always prompting for password"
date: 2007-10-06
forum: General Help
---

### Post by TheSG on 2007-10-06
I'm trying to install Wine using the terminal for Ubuntu 7.0.4 but it keeps prompting me for a password but wont let me type anything in. I've tried setting the root password but it either tells me I can't or just keeps prompting me for one. I've tried editing it in Users&Groups but it wont let me type unless I enter to the next line and it STILL says its not right.

This is what it looks like. 
[IMG]http://img380.imageshack.us/img380/6456/screenshotmd7.png[/IMG]
I just got Ubuntu today and installed a graphics card after I installed it then it had some errors with the card so I reinstalled Ubuntu and it works fine but I can't figure out how I got it working before.

---

### Post by PmDematagoda on 2007-10-06
A fact about entering the password in the terminal in Linux is that you're not shown whether you are  or you are not entering the password but when you enter the password as normal and press enter it gets accepted if it is correct. This is a security measure(According to the developers) which is meant to make the cracking of a password difficult, so you better get used to it.

---

### Post by Old *ix Geek on 2007-10-06
It's asking for **your** password, not root's.  (You're using *sudo* to acquire root power for executing this command, and when you use *sudo*, you're prompted for your password.)

---

### Post by shad0w_walker on 2007-10-06
Just try using your normal password. You don't need to have a root password set to use sudo.

---

### Post by aysiu on 2007-10-06
> **PmDematagoda said:**
> A fact about entering the password in the terminal in Linux is that you're not shown whether you are  or you are not entering the password but when you enter the password as normal and fully and press enter it gets accepted if it is correct. This is a security measure so you better get used to it. If it were a security measure, it would apply to the GUI also (which it *doesn't*). It's an inconsistency that confuses new users for no other reason than tradition.

Read more about the bug here:
[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by PmDematagoda on 2007-10-06
But wouldn't it be thought that it is a security measure? I mean you enter the password so quick that anyone looking on your shoulder can't make out what is being entered so they turn to the password screen itself expecting it to help them by letting them find out the number of characters but can't(I believe I am being paranoid about this;)).

---

### Post by TheSG on 2007-10-06
Thanks Pm, that fixed it.

---

### Post by aysiu on 2007-10-06
> **PmDematagoda said:**
> But wouldn't it be thought that it is a security measure? I mean you enter the password so quick that anyone looking on your shoulder can't make out what is being entered so they turn to the password screen itself expecting it to help them by letting them find out the number of characters but can't(I believe I am being paranoid about this;)). Read [this thread](http://ubuntuforums.org/showthread.php?t=214393).

---

### Post by PmDematagoda on 2007-10-06
You have a point aysiu, I did support the inconsistency side but you are right when saying that we should have consistent UI especially for the terminal, but I guess the biggest reason the developers don't give the damn about it is that many people find it difficult at first but then get over it very quickly, so why try and repair something so trivial that total newbies can get used to and find a workaround in a matter of seconds.

---

