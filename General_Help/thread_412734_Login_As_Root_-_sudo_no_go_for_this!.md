---
title: "Login As Root - sudo no go for this!"
date: 2007-04-18
forum: General Help
---

### Post by Lifeboat on 2007-04-18
Thanks in advance!

i have a new program (OPManager) - free, but it's big brother is $800 US! 

I NEED to run this program, but it keeps telling me to login as root, first. My administrative account is not good enough. 

I've tried working with sudo, but I can't get the program running that way either.. Ditto with gksudo.
(which I don't know much about).

So, one more time from the top: How do I login as root?  :confused: 

I've read several posts on the matter, and The Official Ubuntu Book, but no dice, yet.

Security is NO problem. I'm the only one anywhere near my computer.

---

### Post by akshaysrinivasan on 2007-04-18
There is a option to enable the root account in the 'Login Window' menu in administration

---

### Post by Perfect Storm on 2007-04-18
gksudo is used by opening graphical applications, like if you use sudo gedit you can mess up the permission of that program.


On topic:
Have your tried with
sudo su

---

### Post by UbuntuniX on 2007-04-18
Administration ~> Login ~> Enable local root login

Then logout or su, login as root with your root password.

You shouldn't need this, though.

---

### Post by earobinson on 2007-04-18
try sudo -s, then run the command from the terminal. If that dont work you should be able to do sudo passwd to set up the password for the root user

---

### Post by Lifeboat on 2007-04-18
No, I thought sudo was what Ubuntu used for su. I'll give that a shot.

Administration ~> Login ~> Enable local root login: I have no such option (Edgy Eft default install).

I did find an "Enable accessible login" under the "Accessibility" tab of the Login Window.
System>>Administration>>Login Window>>Accessibility tab.

Thanks

---

### Post by Lifeboat on 2007-04-18
OK, I used the sudo -s command in Terminal and wound up after a login as 

root/myname:

But I still keep getting the  "You account has insufficient privileges to run this program. Please 
login as root"

I've looked at the properties for the file, and everything has been changed to allow all user to read and write.

Didn't see an option to run, except "Allow this file to execute", which I checked.

Any other idea's? 

Oh, I tried this:
adak@adak-0:~$ sudo passwd
Password:
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

But what does that really do? I still can't run the program when I return to root with "sudo -s", or if I try it from right where I gave it the new UNIX password.

Oh, I'm stuck!


Thanks for your help, all responders.

---

### Post by earobinson on 2007-04-18
you should now be able to log out and log in as root with the password you chose.

---

### Post by Devilotx on 2007-04-18
what about says sudo su in terminal?

that will give you a root terminal, should be able to run it from there

---

### Post by vlad_x2 on 2007-04-18
try "sudo -i", you will be in a root terminal, so you can run your program

---

### Post by spankymasterc on 2007-04-18
like Devilotx said try to use sudo su it gives you root in terminal then try to run your command

---

