---
title: "accidently got password for login screen"
date: 2013-09-04
forum: General Help
---

### Post by ankt90138 on 2013-09-04
[ATTACH=CONFIG]245983[/ATTACH]
hello
i dont know whether accidently i add a password to my ubuntu 12.10 login screen.and now i have changed the password many times my using diagnostic-->root shell-->passwd command...but login screen shows invalid password..wat should i do now...??

---

### Post by CharlesA on 2013-09-04
Try resetting your password again.

Try this:
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by ankt90138 on 2013-09-04
i have changed several times but still shows an error..

---

### Post by Pako Pako on 2013-09-04
I don't want to point out the obvious, but when you gave yourself a new password, did you accidentally hit any other keys? (Such as ALT, SHIFT, or CAPS LOCK?)

Can you remove the password altogether? (Or can you login via TTY1?)

To enter another terminal, hold ALT+CTRL+F1. (I forget which keys it was on an Apple; I think it was ALT and APPLE.)
This takes you a terminal screen where you can enter a user and password combo (that hopefully works)

---

### Post by ankt90138 on 2013-09-04
no sir i have tried several times

---

### Post by ankt90138 on 2013-09-04
please elaborate the second method u have just given

---

### Post by claracc on 2013-09-05
Have you tried the step by step method in the link [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword) provided by charlesA ?

have you logged in recovery mode? Have you follow all the steps?, what is the reponse obtained?, have you seen the "password: password updated successfully" text?

---

### Post by ankt90138 on 2013-09-07
yes sir....it says pasword updated successfully....but when i login with taht password it simple rejects that .....please see the pic i have uploaded in frst post...

---

### Post by bluefrog on 2013-09-07
in the terminal, write your password and make sure it is the one you want to use.
also, you could set a new password with characters that are sure not to change depending on the language of the keyboard.

---

### Post by chabons on 2013-09-07
I am experiencing a similar issue to this, which seems to have been caused by a software update. Like the original poster, I am certain that my password is correct, however, I receive an authentication error attempting to log in either at the login screen, or via TTY1. I have followed the instructions, and reset the account's password using the root shell in recovery mode to no avail. 

Here is the unique part of my problem though: I created (months ago) a simple script which takes a picture of the user attempting to log in if authentication fails and added it to the authentication process. When I type in the correct password, it does not take a picture (webcam does not power on), whereas if I type anything else, a picture is taken. Therefore I know for sure my user credentials are correct, yet I cannot log in. Does anyone have any suggestions?

EDIT: I am running Ubuntu 12.10 on a Lenovo W520 laptop. Also this picture taking script has been working for months, making it unlikely that it is the source of the problem.

EDIT 2: FIXED - The software update reset a line in the /etc/pam.d/common-auth to the default, which caused it to deny login regardless of login success.

---

