---
title: "I keep getting this error message when i try to install something"
date: 2006-11-06
forum: General Help
---

### Post by computerman0101 on 2006-11-06
Hi im new here and i have Ubuntu 6.10 (edgy eft) and every time i go to the synaptic package manager to install something i get this error message "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem". 

Since im a NOOB to the linux world i have no idea what this means. again this happens when i go to the synaptic package manager and the error i get is "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem." (without the quotes at the end and beginning) 


Can anyone tell me what to plz do!!!!!!!!!!!!!!!!!!!!!!!!! 

This also happens when i go to the temainal and type a command to install something!

THNX FOR ANY HELP! :)

---

### Post by dbott67 on 2006-11-06
You need to enter the command at a terminal:
```
sudo dpkg --configure -a
```

-Dave

---

### Post by chalex on 2006-11-06
and the terminal is in Appications->Accessories->Terminal

---

### Post by Maverick888 on 2006-11-23
Hello,
I got to the point of entering the ```
sudo dpkg --configure -a
```
into the terminal but it asks for a password and i dont know how to enter it.:-k 

Help would be greatly appreciated.

-Mav

---

### Post by PrinceArithon on 2006-11-23
The password is your login password.  When you type it you wont see anything happen, it's part of the security.  Just type in your login password and hit enter.  If you make a mistake the system will tell you, and all you have to do is try it again until you type the password correctly.

---

### Post by Maverick888 on 2006-11-23
yes thank you... i realized my mistake actualy shortly after posting. Thanks for helping anyway.

---

