---
title: "[SOLVED] [LinuxMint]Problem to install customized LiveCD"
date: 2008-05-29
forum: General Help
---

### Post by Cariboo1938 on 2008-05-29
Hi everybody!



With command 'sudo remastersys backup' I made a liveCD/DVD backup 
of my existing Daryna System using the information from [HERE]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

I want to install this system on another computer.
The booting/loading from the new CD works and when I select "Install" by clicking the desktop icon 
or by the path -->Daryna -->Administration -->install
I'm asked to 'Enter your password to perform administrative tasks'.

I learned from "man sudo_root" pages that the root password is locked 
and that the installer will allow me to set a password.

But I can't get to the install process without a password.

What can I do a install without knowing the password?
How can I create a password?
What is the right procedure to install the selfmade LiveCD?

PS.: This maybe valid for Ubuntu 7.10 too.

---

### Post by angry_johnnie on 2008-05-29
If you chose the **backup** option, then it did, in fact, back up everything.  It  should be **your** password it's asking for, not root's.  Try that.  It should work.  I use remastersys a lot, and it's alwasy asked me for my own password.

---

### Post by Cariboo1938 on 2008-05-29
> **angry_johnnie said:**
> If you chose the **backup** option, then it did, in fact, back up everything.  It  should be **your** password it's asking for, not root's.  Try that.  It should work.  I use remastersys a lot, and it's alwasy asked me for my own password.
Yes, I used the **backup** option but if I enter the original password I always get the message : 
"Incorrect password...try again."


EDIT:

It seems that after boot only 'root' is logged in.
I have to switch users:
--->Daryna --->Quit --->Switch User or Logout
Than I can login with my username and password as usual.
Thanks for the hint. Case closed.

---

