---
title: "Getting error messages when trying to update ubuntu feisty fawn"
date: 2007-06-23
forum: General Help
---

### Post by Margarete on 2007-06-23
Hello, I am new to Linux, and am having problems downloading the (6) updates and other things..  I can't seem to do too much on here... far as downloading things that are on Windows, such as Yahoo Messenger or a chat client.. I have obviously gotten Mozilla Firefox and I have Yahoo Messenger buddy list,, but not Messenger it self.


margarete@margarete-desktop:~$ sudo apt-get install gaim-encryption
Password:
Sorry, try again.
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
margarete@margarete-desktop:~$ 

margarete@margarete-desktop:~$ sudo dpkg --configure -a
Password:
Setting up java-common (0.25ubuntu2) ...

Setting up libltdl3 (1.5.22-4) ...

Setting up odbcinst1debian1 (2.2.11-13) ...

Setting up unixodbc (2.2.11-13) ...

margarete@margarete-desktop:~$ 





(These are the types of errors I keep getting when trying to fix things using the 'terminal'.


I would appreciate any help,,, I need all the advice I can get.

Thank you,
Margarete

---

### Post by jrusso2 on 2007-06-23
> **Margarete said:**
> Hello, I am new to Linux, and am having problems downloading the (6) updates and other things..  I can't seem to do too much on here... far as downloading things that are on Windows, such as Yahoo Messenger or a chat client.. I have obviously gotten Mozilla Firefox and I have Yahoo Messenger buddy list,, but not Messenger it self.


margarete@margarete-desktop:~$ sudo apt-get install gaim-encryption
Password:
Sorry, try again.
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
margarete@margarete-desktop:~$ 
(That is the error I keep getting when trying to fix things using the 'terminal'.


I would appreciate any help,,, I need all the advice I can get.

Thank you,
Margarete

Try again paste this into the terminal sudo  dpkg --configure -a

sudo will ask for password so give it your password and enter.

Then try again sudo apt-get update

Then what ever it is your trying to install.

---

