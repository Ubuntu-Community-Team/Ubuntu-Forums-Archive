---
title: "friend screwed with my sudo - now broken :("
date: 2008-06-01
forum: General Help
---

### Post by halfmike on 2008-06-01
[I]running ubuntu 8.04 on a gateway m-6848 - very new computer
[/I]
ok, so my friend tried to install pamusb but because of a bug, it didn't work. now, when i try to sudo <command>, the terminal just says: "Sorry, wrong password" three times and then "three incorrect password attempts."
```
<user>@<user>laptop-hardy:~$ sudo nautilus
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
```
I'd love to gedit my /etc/pam.d/common-auth file (because i had to comment some stuff out of said file earlier because of pamusb - it took forever to try to read the flash drive and it ended up just wasting like 20 seconds) but i can't without sudo!

What do I do? I already reinstalled sudo from recovery console.

---

### Post by Xiong Chiamiov on 2008-06-01
Can you reset your password using
```

passwd

```
?
There also might be something odd with your sudoers file.

---

### Post by halfmike on 2008-06-01
```
halfmike@halfmikelaptop-hardy:~$ passwd
Changing password for halfmike.
(current) UNIX password: 
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
halfmike@halfmikelaptop-hardy:~$ 

```

```
halfmike@halfmikelaptop-hardy:~$ sudo apt-get
Sorry, try again.
Sorry, try again.
Sorry, try again.
sudo: 3 incorrect password attempts
halfmike@halfmikelaptop-hardy:~$ 

```

edit - worked to reset password but not fixed problem

---

### Post by y-lee on 2008-06-01
You might want to read [Troubleshooting Sudo]("http://www.psychocats.net/ubuntu/fixsudo")

---

### Post by halfmike on 2008-06-01
```
halfmike@halfmikelaptop-hardy:~$ sudo example
* pam_usb v0.4.0
* Authentication request for user "halfmike" (sudo)
* Device "MyDevice" is connected (good).
* Performing one time pad verification...
* Probing volume (this could take a while)...
* Access denied.
[sudo] password for halfmike:
sudo: example: command not found
halfmike@halfmikelaptop-hardy:~$

```

so the sudo works but i have no idea how to get rid of the buggy pamusb

---

### Post by y-lee on 2008-06-01
> **halfmike said:**
> 
so the sudo works but i have no idea how to get rid of the buggy pamusb

it depends on how pamusb was installed. You can try opening synaptic and searching for pamusb and if it was installed thru the repos check for complete removal and remove it that way.

---

### Post by sdennie on 2008-06-01
It's possible (actually, likely) that pamusb messed with files in /etc/pam.d.  If y_lee's idea of completely purging the package doesn't work, you may need to grab fresh versions of /etc/pam.d config files.  The way I do things like this is to pull them off of a freshly installed VM.

---

### Post by halfmike on 2008-06-02
thanks so much you guys. you are what make the linux community the best... err... community.

---

### Post by sdennie on 2008-06-02
Out of curiosity, what finally fixed your problem?

---

