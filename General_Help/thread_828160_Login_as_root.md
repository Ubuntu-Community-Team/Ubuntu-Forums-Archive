---
title: "Login as root"
date: 2008-06-13
forum: General Help
---

### Post by omega17 on 2008-06-13
i want to login as root but it says I can't but it lets me in tty1.


thanks in advance!


P.S. in tty1 login as root works bot startx dosent

---

### Post by wootah on 2008-06-13
> **omega17 said:**
> i want to login as root but it says I can't but it lets me in tty1.


thanks in advance!


P.S. in tty1 login as root works bot startx dosent

You shouldn't be able to login with root in any console with Ubuntu. The password isn't even set for root! It has been disabled as a security feature.

Whatever you need to do, use sudo and gksudo. Don't run X with root, as that will screw your authority files up (setting their permissions as root) and the next time you login with your normal account, it will not allow you.

---

### Post by aysiu on 2008-06-13
You don't need to log in as root. Tell us what you're really trying to accomplish by logging in as root, and we'll help you do it the proper way.

---

### Post by omega17 on 2008-06-13
i installed in expert mode and set a pass for root bou inexpert i selected no to allow login as root. is there a way to change file permissions in a console? is there a way to give my user root permission, and when i go to change permission in user manager and unlock it says unexpected error and dosent let me change my permissions.

p.s. i installed LILO boot loader, is there a way to switch to grub?

---

### Post by aysiu on 2008-06-13
> **omega17 said:**
> i installed in expert mode and set a pass for root bou inexpert i selected no to allow login as root. is there a way to change file permissions in a console? is there a way to give my user root permission, and when i go to change permission in user manager and unlock it says unexpected error and dosent let me change my permissions.

p.s. i installed LILO boot loader, is there a way to switch to grub?
I don't know what you mean about expert mode, etc.

To change permissions, just do ```
sudo chmod ### /path/to/file
``` where ### are the permission parameters you want. For example, if you want to change a text file to be executable, readable, and writable for the owner but totally off-limits for everyone else, it'd be ```
sudo chmod 700 /path/to/file
``` Be careful, though. Changing permissions on system files can render your system unusable.

What file are you trying to change permissions on?

---

### Post by omega17 on 2008-06-13
ect/apt/sources.list and in the ubuntu installer main menu press F6 twice and you can get to expert mode for advanced users to chose everything.

---

### Post by wootah on 2008-06-13
> **omega17 said:**
> i installed in expert mode and set a pass for root bou inexpert i selected no to allow login as root. is there a way to change file permissions in a console? is there a way to give my user root permission, and when i go to change permission in user manager and unlock it says unexpected error and dosent let me change my permissions.

p.s. i installed LILO boot loader, is there a way to switch to grub?

Yes you can switch to grub. Should be available in the repositories, as grub-pc

```

sudo apt-get install grub-pc

```

That should do everything automatically for you.

You can change permissions with chmod and ownership with chown and group with chgrp OR you can use chown to change the owner and the group:

```
chown theuser:thegroup thefile
```

To get a person to be able to have 'root' style access to the system (by using sudo) you add them to the admin group.

```

adduser existinguser admin

```

The above code adds **existinguser** to the **admin** group. Now existinguser can use sudo to accomplish admin tasks:

```

sudo mkdir /a_root_directory

```

:)

---

### Post by omega17 on 2008-06-13
```
grub-pc not found
```

---

### Post by wootah on 2008-06-13
> **omega17 said:**
> ```
grub-pc not found
```

... whoooooops

```
sudo apt-get install grub
```

... hehe ...

---

### Post by simonasambler on 2008-06-13
BTW it is posibble to log in as root.  ctrl+alt+1 and than login as root /first you have to log with your normal account/ and than type su and write you root pass, than type ```
startx
``` and you are log in as root with xserver but i dont adwise you this :) .


[to set root pass write ```
sudo passwd root
``` ]

---

### Post by Ender305 on 2008-06-13
if you boot into recovery mode, log in as root, and add /usr/bin to your PATH, you can have a gui as root without screwing up the authority files

I figured this out after my /home partition had been corrupted and I needed to log in with a GUI

---

### Post by malath on 2008-06-13
hello all

by mistake i issued the command

set passwd su

and now my password is not working athentication failure.

i tried 'su' also the same thing..what to do?

---

### Post by simonasambler on 2008-06-13
to set root pasword type command ```
sudo passwd root
```

---

### Post by billy_bob666 on 2008-06-19
> **simonasambler said:**
> 

[to set root pass write ```
sudo passwd root
``` ]

Thanks worked for me :)

---

### Post by chrisccoulson on 2008-06-19
Guys, please remember that forum policy forbids log-in-as-root tutorials (please read [http://ubuntuforums.org/showthread.php?t=765414]("http://ubuntuforums.org/showthread.php?t=765414"))

---

### Post by VMC on 2008-06-19
This always gets dicey when someone want to circumvent the system and use root.

To use root on more then one command then investigate and read this commentary:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ians1 on 2008-06-20
Being new to this I take the advice and can see its equivalent to being logged in as administrator in windows, so easy to do much damage if you dont know what your doing!

So using sudo is executing as if you were root but with limitations?

ian

---

### Post by wootah on 2008-06-20
> **ians1 said:**
> Being new to this I take the advice and can see its equivalent to being logged in as administrator in windows, so easy to do much damage if you dont know what your doing!

So using sudo is executing as if you were root but with limitations?

ian

Yes! It is the somewhat the same as CTRL(or shift.. whatever)-RightClicking something and going 'run as' and then using admin privs.

Sudo is much more secure because you have to be apart of the admin group to even use it. It is also logged and you can change and 'tune' the access to sudo. I believe you can even make it so you can't sudo from remote connections?

As well, if you want a root terminal, use sudo -i instead of sudo su.

---

### Post by sapient2003 on 2008-06-20
> **omega17 said:**
> i want to login as root but it says I can't but it lets me in tty1.


thanks in advance!


P.S. in tty1 login as root works bot startx dosent



You can change the root password easily. First click on Applications-->Accessories and choose Terminal. Type in "sudo /bin/bash" without the quotations and then enter in your password for your user account. You are now logged in as root. If you want you then can change the root password by using the "passwd" command.

Example:
sapient@sapient-desktop:~$ sudo /bin/bash
[sudo] password for sapient:
root@sapient-desktop:~# passwd
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
root@sapient-desktop:~# exit
exit
sapient@sapient-desktop:~$ su
Password: 
root@sapient-desktop:/home/sapient#

---

