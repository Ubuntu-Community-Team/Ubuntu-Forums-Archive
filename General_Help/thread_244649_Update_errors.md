---
title: "Update errors"
date: 2006-08-26
forum: General Help
---

### Post by taekwondodogoof on 2006-08-26
Hi, my update, or synaptic package manager won't work. When I try to update manually I get this error.

```
jared@MeinKampf:~$ sudo apt-get update
sudo: /etc/sudoers is mode 0777, should be 0440

```

Thanks for any help!

---

### Post by taekwondodogoof on 2006-08-26
Anyone?

---

### Post by ifokkema on 2006-08-26
What happened with the file? Did you try and mess with chmod or something? The permissions on the sudo file are wrong, and now you're locked out of sudo. Reboot into recovery mode and fix the permissions on /etc/sudoers/.

---

### Post by taekwondodogoof on 2006-08-26
I don't think I changed anything, at least not on purpose. How do I boot into recovery mode and change the permissions? Thanks for the help =D

---

### Post by ifokkema on 2006-08-27
You know when you boot up, you get several options for how you want to boot up? There's usually a kernel, recovery mode, and memtest at the very least.

After you boot into recovery mode, you should be logged in as root. Or, if you set a root password in your installation, you'll be prompted for your root password. Either way--password or not--you'll end up logged in as root. 
(text taken from [http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo))


After following the instructions above, run:
```
chmod 440 /etc/sudoers
```

That should fix it :)

---

