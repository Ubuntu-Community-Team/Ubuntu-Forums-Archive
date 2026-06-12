---
title: "After activating firewall of remote server I can not login with ssh"
date: 2020-08-05
forum: General Help
---

### Post by petrogromovo on 2020-08-05
Hello,
On ubuntu 16 I have php/laravel app installed under appache .
I have firewall inactive and I decided to activate it and rebooted the OS
```

 sudo ufw status numbered
Status: inactive
root@ubuntu-server/app# sudo ufw default deny incoming
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)
root@ubuntu-server/app# sudo ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)
root@ubuntu-server/app# sudo ufw status numbered
Status: inactive
root@ubuntu-server/app# sudo ufw status verbose
Status: inactive
root@ubuntu-server/app# reboot
Connection to NNN.NNN.NN.NN closed by remote host.
Connection to NNN.NNN.NN.NN closed.


```But after that I can not to log unto the system with ssh:

```
ssh root@NNN.NNN.NN.NN
ssh: connect to host NNN.NNN.NN.NN port 22: Connection timed out

```
If my commands were invalid and if there is a way to enter into it now ?

Thanks!

---

### Post by petrogromovo on 2020-08-05
I can not  enter into the system with ssh but also in the browser site is not opened. 
Looks like problems on restarting. That is Ubuntu under Digital Ocean and I have access to  Digital Ocean account.
Which steps have i to tale to fix server ?

---

### Post by ActionParsnip on 2020-08-05
You will need to reboot the server and hopefully this will help. You may be able to use the console in the DigitalOcean web interface but you forgot to allow the SSH traffic both ways so you severed your own connection.

If this is a brand new server with little to no configuration I suggest you destroy the droplet and make new (I use Digital Ocean myself).

---

### Post by TheFu on 2020-08-05
On a normal Ubuntu install, ssh access with the root account would be disabled. In fact, the entire root account is disabled except through sudo.  IaaS providers may enable root access, I suppose.

If the firewall rules are wrong for your needs, then you'll need a different method. Usually the console method is the easiest because that bypasses any networking. Go in through the console and disable the firewall.  Then re-look over the rules.  Always best to have an **ssh allow** rule at the top.
```
$ sudo ufw allow ssh
$ sudo ufw enable
$ sudo ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW IN    Anywhere
```
I disable IPv6, otherwise there would be another IPv6 rule added from the first command above.

BTW, the fail2ban tool will dynamically block brute force ssh attacks. Just install the **fail2ban** package. The defaults aren't too bad for ssh protection, especially if following best practices and using ssh-keys for all authentication, never passwords after the first 2 minutes on a new system.

---

