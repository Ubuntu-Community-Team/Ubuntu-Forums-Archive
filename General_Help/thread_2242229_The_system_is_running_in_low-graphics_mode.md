---
title: "The system is running in low-graphics mode"
date: 2014-08-31
forum: General Help
---

### Post by sim085 on 2014-08-31
Hello,

I have a VM I use mostly for development. After I shut down the Host PC in a not proper way I got the message "The system is running in low-graphics mode".

I have gone through several threads on the net. Some suggest to press CTRL+ALT+F1 to enter in "Terminal". I did this, but when I enter my username and password I get the message "Login incorrect". I am sure that the Username and Password are correct!

That said, the next thing I tried is to reset the password for the account I had. I press Shift at start up. Selected the option "recovery mode". Selected the option "root (Drop to root shell prompt)". I remount the filesystem to read/write using the following command "mount -o rw,remount /". I then tried to reset the password of my account (which can be found under /home) using the command "passwd <username>". Here I get an error "passwd: Permission denied". 

Is this VM no longer recoverable?

---

### Post by sim085 on 2014-09-02
At least can someone tell me why I got this problem? Just by shutting down the PC should not have corrupted files on disk!?

---

