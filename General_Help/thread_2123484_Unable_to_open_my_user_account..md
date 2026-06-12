---
title: "Unable to open my user account."
date: 2013-03-08
forum: General Help
---

### Post by aayus on 2013-03-08
I edited the .profile file of my account and then logged out of the account. Since then I am unable to open my account whenever I enter the password, again the login screen shows up. It is maybe due to the syntax error in the .profile. 
How can I bring the .profile to default or remove that line so as to be able to open my acocunt??
 
I tried to get the access of my user account through the guest account using the sudo and su command but i am unable to do so.
It shows the following error:
 sudo aayush
sudo: unable to change to sudoers gid: Operation not permitted

Please anyone help me with this so that i can open my user account.

---

### Post by aayus on 2013-03-08
I edited the .profile file of my account and then logged out of the  account. Since then I am unable to open my account whenever I enter the  password, again the login screen shows up. It is maybe due to the syntax  error in the .profile. 
How can I bring the .profile to default or remove that line so as to be able to open my acocunt??
 
I tried to get the access of my user account through the guest account using the sudo and su command but i am unable to do so.
It shows the following error:
 sudo aayush
sudo: unable to change to sudoers gid: Operation not permitted

Please anyone help me with this so that i can open my user account.

---

### Post by plucky on 2013-03-08
> **aayus said:**
> I edited the .profile file of my account and then logged out of the account. Since then I am unable to open my account whenever I enter the password, again the login screen shows up. It is maybe due to the syntax error in the .profile. 
How can I bring the .profile to default or remove that line so as to be able to open my acocunt??
 
I tried to get the access of my user account through the guest account using the sudo and su command but i am unable to do so.
It shows the following error:
 sudo aayush
sudo: unable to change to sudoers gid: Operation not permitted

Please anyone help me with this so that i can open my user account.

At the login window type ```
Ctrl+Alt+F1
``` and it should take you to a login prompt.

Type in your username and password and you should then be able to edit your .profile file.

Good Luck

---

### Post by varunendra on 2013-03-08
Threads merged.

Please do not create multiple threads for same issue. It dilutes community efforts to help.

Thanks, and Welcome to the forums ! :)

---

### Post by aayus on 2013-03-08
I am able to open my account in the terminal appearing after pressing 

Ctrl+Alt+F1

but when i try to open the .profile through gedit .profile or vi .profile, its shows this kind 
of error the command is available but the /usr/bin is not added to the environment path etc etc. I am totally new 
to ubuntu, the problem started when i entered the line 
   export PATH=:/your/root/path/bin:
I have no idea what to be able to open my user account again. whether i have to re-edit the .profile or bring back to it's default code or anything!!

---

### Post by Warren Hill on 2013-03-08
take a look here: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Its a tutorial on resetting your password.  You don't want to change your password  so stop just before you get to
```

passwd *username*
```

You should now be able to edit the .profile file

cd to your home directory and enter 

```
nano .profile
```

edit the file to be as it was and reboot to test.

If you need to know what file contains ask again and one of us can give you the output of 

```
cat ~/.profile
```

on an unmodified machine.  I would but I'm not using Ubuntu at the moment

---

### Post by aayus on 2013-03-08
again the same problem when i enter the cmd
nano .profile
error:
command 'nano' is available in the following places
/bin/nano
/usr/bin/nano
the command could not be located because the '/usr/bin:/bin' is not included in the path environment variable.

---

### Post by aayus on 2013-03-08
Finally I am able to do it and is able to open my user account.
this time around 
used the cmd
/usr/bin/nano .profile and was able to edit the file.
Thanks dude.

---

### Post by Warren Hill on 2013-03-08
If now fixed please mark the question solved.

---

