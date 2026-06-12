---
title: "Help with password!"
date: 2015-01-16
forum: General Help
---

### Post by aidas2 on 2015-01-16
Hello guys I have small problem, I have my account without a password, when you log off, you don't need to enter your password.
But now without a password i can't use terminal it because my user account does not have a password.

Can I somehow set a password when using a terminal, but still use no password when i want to log in into my account?

---

### Post by deadflowr on 2015-01-16
You set a password during install, unless you made a new user post install using the user account method.
(That method sets the user name but leaves the password disabled until you set it)

You  can reset your password by rebooting the system into recovery mode and then opening the root shell option, then run these commands
first
```
mount -o rw,remount /
```
The root shell opens read-only, so the above command will reset it read/write; important if you want to have the next command stick:
and then the command to change the password
```
passwd username
```
change username to your username
then type exit and then resume to desktop, or whatever it's called.
Good reference guide here w/ pictures
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Note that this does not and will not change the auto login option you have set.
Nor does it mean you will have to enter a password to shutdown/reboot.

---

### Post by ajgreeny on 2015-01-16
You can easily set up a system to use autologin for one particular user, but that user will still need to use the password to carry out activities such as installing or removing packages, etc etc; ie, anything that normally needs root permissions using sudo, for example ```
sudo apt-get install *packagename*
```
It means that the user still has a password used for sudo command root permissions but the system will login to that user automatically.

Let us know if that is what you want and we can tell you which files to edit, though if you can't use the terminal with sudo, you may have to reset the user password with recovery mode first, then make the system autologin to that user.

---

### Post by aidas2 on 2015-01-17
> **deadflowr said:**
> You set a password during install, unless you made a new user post install using the user account method.
(That method sets the user name but leaves the password disabled until you set it)

You  can reset your password by rebooting the system into recovery mode and then opening the root shell option, then run these commands
first
```
mount -o rw,remount /
```
The root shell opens read-only, so the above command will reset it read/write; important if you want to have the next command stick:
and then the command to change the password
```
passwd username
```
change username to your username
then type exit and then resume to desktop, or whatever it's called.
Good reference guide here w/ pictures
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Note that this does not and will not change the auto login option you have set.
Nor does it mean you will have to enter a password to shutdown/reboot.


Ok so I tried to enter rescue mode 
> 

[LIST=1]
[*]Switch on your computer.
[*]Wait until the BIOS has finished loading, or has almost finished. (During this time you will probably see a logo of your computer manufacturer.)
[*]Quickly press and hold the Shift key, which will bring up the GNU GRUB menu. (If you see the Ubuntu logo, you've missed the point where you can enter the GRUB menu.)
[/LIST]


The second I see HP Logo i quickly press Shift but it's not loading to rescue mode. Tried 7 times in a row, no luck :D

---

### Post by deadflowr on 2015-01-17
I think if running a system with uefi, then you tap the esc button, instead of the shift button to access the grub menu...

---

