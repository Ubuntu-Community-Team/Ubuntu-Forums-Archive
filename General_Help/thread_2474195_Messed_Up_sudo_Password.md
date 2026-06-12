---
title: "Messed Up sudo Password"
date: 2022-04-23
forum: General Help
---

### Post by Quarkrad on 2022-04-23
Fresh install of 22.04 (fixed graphics error in 20.04).  Have separate / and /home - done this (re-install) a number of times so I'm familiar with the danger of not keeping the same sudo password.  Currently everything appears OK except that I have to enter my sudo password in upper case in order for it to work.  So .... if my sudo password was ***boo*** before the re install I now have to use ***BOO***.  If I try boo then I get:

```
dad@dadubuntu:~$ sudo apt update
[sudo] password for dad: 
Sorry, try again.
[sudo] password for dad: 
Hit:1 http://gb.archive.ubuntu.com/ubuntu jammy InRelease
Hit:2 http://gb.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://gb.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Hit:4 https://linux.teamviewer.com/deb stable InRelease                        
Hit:5 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up-to-date.
```

In order to complete the command above I had to enter BOO.  I would like to be able to enter boo rather then BOO - any advice on why this has happened and how to get back to my lower case password would be appreciated. (I have tried sudo passwd root)

---

### Post by deadflowr on 2022-04-23
I'm guessing boo is short for whatever the actual password is.
No need to set root's password, you wanted to set your own user's password.
switch out root for the user.
```
sudo passwd usernamehere
```
and double check the caps lock key isn't on.

---

### Post by coley9225 on 2022-04-23
Hello quarkrad. No need to fear, should be an easy fix. open a terminal and enter the command 'passwd'. From there, it will tell you it is changing password <user>, ask for your old password, ask for your new password, then to confirm new password. If all goes well, it will tell you password successfully changed. And just like that, your password is what you want.

---

### Post by westie457 on 2022-04-23
I believe this should work. 

[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

### Post by Quarkrad on 2022-04-23
boo is not my actual password - I used that as an example.  My real password is alpha numeric 13 characters.  When using that command I get:

```
dad@dadubuntu:~$ sudo passwd xxxxxxxxxxxxx
[sudo] password for dad: 
passwd: user 'xxxxxxxxxxxxx' does not exist
```

---

### Post by Quarkrad on 2022-04-23
#4  when I tried that I eventually got the same result - passwd: user 'xxxxxxxxxxxxx' does not exist

#3 Thank you coley9225 - that worked.  Phew ......

---

### Post by grahammechanical on 2022-04-23
You have a useable password but not the one you want. You can change this through System Settings>Users.

Unlock the dialog with the password that works, (the one that you do not want). Click Password and in the box that appears type in the current password and then the new password and then confirm the new password. Click Change and that should give you the password you want.

Edit: I just notice that you are on Ubuntu Mate. That flavour should have something similar to Ubuntu system settings

Regards

---

### Post by TheFu on 2022-04-23
If you are logged in as 'dad', then use 
```
$ passwd dad
```
Enter "BOO", then you'll be asked for the new password to use, twice.

I strongly suspect the capslock was on during the install.

There's no such thing as a 'sudo password'. It is just a normal login password for any userid that is part of the sudo Unix group.  Since encrypted HOME directories were deprecated and LUKS has been the main method of performing encryption of storage, changing any user's password has no negative impacts that I've ever seen.  LUKS encryption doesn't use passphrases tied to any users.

If the current userid is NOT the same as the username you need to change a password for, use 
```
$ sudo passwd other-name
```
That will ask for sudo authentication, then it will ask for the new password to be used for "other-name", twice.  other-name must be a valid, existing, username on the system. The passwd command doesn't create new users.

---

### Post by Quarkrad on 2022-04-24
Thank you all - old password back and working.

---

