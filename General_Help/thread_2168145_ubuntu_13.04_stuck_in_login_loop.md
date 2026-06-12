---
title: "ubuntu 13.04 stuck in login loop"
date: 2013-08-16
forum: General Help
---

### Post by samsamsam2 on 2013-08-16
So my installation is stuck in a login loop. When I enter the correct password it goes blank and acts as if it is logging me in but reverts back to the same screen. When I enter any random password it tells me that my password is wrong. The guest session is working fine. I tried to use the solution that is given here([http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop/223634#223634](http://askubuntu.com/questions/223501/ubuntu-12-10-gets-stuck-in-a-login-loop/223634#223634)) but it did not help .

The last command i used was sudo chown xxx /home. I don't remember it exactly but since then the terminal had an extra line added on top regarding something related to bash.rc and then from the next restart this problem is occurring.

Thanks for help!!!

---

### Post by bibble235 on 2013-08-17
Not sure if this helps but try 

Ctrl+Alt+F1 to get to the console
log in
sudo bash  (Login as root)
mv /home/<username> /home/<username>_old
mkdir /home/<username>
chown <username>.<username> /home/<username>
reboot

---

### Post by samsamsam2 on 2013-08-18
bible235 sir thank you.
 you just saved my day. The solution worked perfect.
Now how can I use /home/<username_old> as my /home/<username> directory again? Do i just need to copy paste?
Thank you again.

---

