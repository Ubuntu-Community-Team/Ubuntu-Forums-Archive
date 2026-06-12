---
title: "Password and Keys probalem"
date: 2014-05-16
forum: General Help
---

### Post by PiotrIr on 2014-05-16
Hi,

I've installed Ubuntu 14.04 and play with Remmina to save mine support passwords for SSH connections. I followed instruction from link below:
[http://technologyflirt.blogspot.ie/2013/02/how-to-save-ssh-password-in-remmina.html](http://technologyflirt.blogspot.ie/2013/02/how-to-save-ssh-password-in-remmina.html)
but unfortunately when I connect from terminal (still prompts about password) or using Remmina it doesn't work. 

Could you advise please?

---

### Post by deadflowr on 2014-05-16
Did you set up a passphrase for the key?
If so, then it will always ask for it.

You can create keys without a passphrase, and then it won't prompt you for a password.
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Choosing_a_good_passphrase](https://help.ubuntu.com/community/SSH/OpenSSH/Keys#Choosing_a_good_passphrase)

---

### Post by PiotrIr on 2014-05-16
Thank you for your reply.

I've tried without Passphrase and it doesn't work as well. I just wander, maybe there is a bug in Ubuntu 14.04 or it requires additional configuration?

---

### Post by deadflowr on 2014-05-16
Does the terminal post anything about authentication failure when trying to connect to the ssh-server?
Or is it simply asking for the password, and nothing else?

---

### Post by PiotrIr on 2014-05-19
It does only prompt about user name and password...

---

