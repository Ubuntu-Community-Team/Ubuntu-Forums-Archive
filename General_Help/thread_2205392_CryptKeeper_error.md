---
title: "CryptKeeper error?"
date: 2014-02-13
forum: General Help
---

### Post by Andras_Kiss on 2014-02-13
Hey all,

To start off with, I am quite the Linux noob having never used it before I started my graduate studies. I am familiar with Mac OSX.

I am trying to install CryptKeeper to handle encryption of some folders. I installed it no problem, but when I try and create an encrypted folder it gives me the following error

[IMG]http://i.imgur.com/d0fntrs.png[/IMG]

I have confirmed that the folder did not previously exist before CryptKeeper made it. I also checked that encfs is installed and it seems to be working fine. I am on Ubuntu 12.04.

Thanks and sorry if this question is silly or if I left out any info.

Thanks!

---

### Post by mbuell on 2014-02-24
Not sure how much help I can be, but I'll give it a shot, since nobody else has. 

I really like cryptkeeper, btw. It is reliable, and does what it is supposed to do. Normally. 

The first thing I would look at here are the permissions for the folder where you are trying to create the destination folder. You also need to make sure fuse is installed and working. 

When cryptkeeper doesn't work, I find the first and best next answer is to try and do the same thing using encfs from the command line. [I hate it when people tell me to use the command line, but I'm just being honest here. In this case it is very useful, and not very complicated.] Using encfs from the command line will give you a more verbose error message - or it may even work. At any rate, if you get an error, you will probably have a better error message then what cryptkeeper gave you. A more useful error message. 

Check those things. Permissions, for both the directory where you are creating the encrypted folder, and the directory where you are creating the target.

---

