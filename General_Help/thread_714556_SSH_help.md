---
title: "SSH help"
date: 2008-03-03
forum: General Help
---

### Post by shijirou on 2008-03-03
Hi guys. I'm fairly new to SSH stuff and I need a bit of help. I've got the ssh client/server installed on a machine running Xubuntu. I was able to confirm that it was working by accessing it from a Windows machine using putty. I just used the IP address of the PC in the network. But how do you do this over the internet? I've tried accessing this machine when I went home using the IP address of our office and it gives me a connection error. Am I missing something in the ssh setup or do I need to do extra stuff on the putty program on Windows? Thanks a bunch!

---

### Post by jcwmoore on 2008-03-03
you need to inable port forwarding, ssh uses port 22 (i think) to you need to forward all port 22 requests to your local machine, the one with ssh installed...

how you enable port forwarding depends on what router you have

---

### Post by shijirou on 2008-03-03
Oh thanks for the reply! How do I change the port of SSH on the xubuntu machine though? Is there a config file? Port 22 is currently being used by our NTOP monitor so that means I need an open port for it.

---

### Post by jcwmoore on 2008-03-03
yes, if port 22 is used by some other app you need to change it, the file that controlls which port ssh listens to is

/etc/ssh/sshd_config

so run 

```
sudo vim /etc/ssh/sshd_config
```

to edit the file, chage port 22 to what ever port you want.
now when you run ssh from the client there is a syntax you need to use...

```
ssh -p PORT user@host
```

i think....

---

### Post by shijirou on 2008-03-04
Cool! Thanks for the help! Got it working!

---

