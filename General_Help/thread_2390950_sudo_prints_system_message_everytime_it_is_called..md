---
title: "sudo prints system message everytime it is called."
date: 2018-05-04
forum: General Help
---

### Post by mcparty2 on 2018-05-04
Description:    Ubuntu 16.04.4 LTS Server Edition.
Kernel: 4.4.0-122-generic


Every time I call sudo as my user account or the root account, I get the log on system summery.

Examples

```
sudo su
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-122-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.
```


```
sudo touch file1
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-122-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.

```



```

sudo echo "WTF?"
Welcome to Ubuntu 16.04.4 LTS (GNU/Linux 4.4.0-122-generic x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

0 packages can be updated.
0 updates are security updates.


WTF?
```


No idea why this is happening - Can anyone help, it's really annoying? 


Many thanks

Adam

---

### Post by steeldriver on 2018-05-04
Hmm... I wonder if your /etc/pam.d/sudo is (either directly or indirectly) including pam_motd?

---

### Post by mcparty2 on 2018-08-24
Ahhhh, turns out i had copied the /etc/pam.d/ssh file to the sudo file.
Thanks for your help and sorry for the dealyed response.

---

