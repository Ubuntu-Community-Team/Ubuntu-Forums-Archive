---
title: "Passwd issues"
date: 2012-12-17
forum: General Help
---

### Post by marcoZazza on 2012-12-17
Hey Everybody, 
I'm new to this community and I'm so exited about Ubuntu!!!

I installed for the fisrt time an Ubuntu desktop on my computer and I'm having a little problem.

It seems like is not recognizing my passwd for authentication on installing new software :sad:

is there a way to reset the passwd ?

I tryed to look into ect/shadow to double check that my passwd was correct ( you know most of the time the error is from the user!!! ) but I couldn't open the shadow file... it seems like it's a binary file!!!!

is there a way I can fix this ?


a little background of what happened :
    I installed Ubuntu from the Windows installer, everything went well, I choose username and passwd and the installation went well.
    After I loged in in Ubuntu, I installed a couple of app (gnome mail for gmail!!) and on the installation it asked the password. I entered the passwd and the installation went well.
    Then I went to change my user settins, choosing to not have a password for my administratoor account, and after I made this choice I can't install any software ( the error is that the passwd is not correct)

---

### Post by steeldriver on 2012-12-17
Hello and welcome

See this tutorial for resetting the primary user password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Please don't mess with the /etc/shadow file - it's not binary, but ordinary users don't have read permissions (for good reasons!)

---

### Post by lisati on 2012-12-17
When you're installing software from the command line, it is normal for your password to not be shown on the screen: just type it in as usual.

---

### Post by marcoZazza on 2012-12-17
Hey guys, 

thanks a lot it worked :) I really appreciate it !!!!

---

