---
title: "Changing user's password"
date: 2008-06-19
forum: General Help
---

### Post by HpZ on 2008-06-19
How do I change my login password?

---

### Post by jakupl on 2008-06-19
write in terminal:

```
passwd <your username>
```

To change the sudo password:

```
sudo passwd
```

---

### Post by sisco311 on 2008-06-19
> **jakupl said:**
> write in terminal:

```
sudo passwd <your username>
```

to change your own password you don't need sudo
```
passwd
```

---

### Post by jakupl on 2008-06-19
sorry I will edit.

---

### Post by sisco311 on 2008-06-19
> **jakupl said:**
> sorry I Will Edit.
Deleted

---

### Post by jakupl on 2008-06-19
haha this became quite a mess :)

---

### Post by aysiu on 2008-06-19
Go to System > Administration > Users and Groups

Unlock

Double-click your username

Enter a new password

---

### Post by sisco311 on 2008-06-19
:)

lets start again

you can change your own password with:
```
passwd
```You can't set up a weak password(to short or similar to the old one)

you can change your password to anything you want with:
```
sudo passwd $USERNAME
```NOT RECOMMENDED!!!

you can change other users password with:
```
sudo passwd <username>
```or you can use the gui (Users and Groups)

---

### Post by sisco311 on 2008-06-19
> **aysiu said:**
> Go to System > Administration > Users and Groups

Unlock

Double-click your username

Enter a new password

Sorry to be a nag, but why do you need to click the Unlock button in order to change your own password?

---

### Post by jakupl on 2008-06-19
you dont need to press unlock for your own password, but it will prompt for it later when you press ok.

this is just a security feature, obviously for preventing unauthorized people from snatching your profile... or something like that.

---

### Post by aysiu on 2008-06-19
> **jakupl said:**
> you dont need to press unlock for your own password, but it will prompt for it later when you press ok.

this is just a security feature, obviously for preventing unauthorized people from snatching your profile... or something like that.
It's true. If you don't unlock before you change your password, you'll still be prompted with this message *after* you change your password.

---

### Post by sisco311 on 2008-06-19
> **aysiu said:**
> It's true. If you don't unlock before you change your password, you'll still be prompted with this message *after* you change your password.
yes, but not to become root.

---

### Post by aysiu on 2008-06-19
> **sisco311 said:**
> yes, but not to become root.
Point taken.

---

### Post by chrisccoulson on 2008-06-19
Also, System -> Preferences -> About Me, and then click 'Change Password...';)

---

### Post by aysiu on 2008-06-19
> **chrisccoulson said:**
> Also, System -> Preferences -> About Me, and then click 'Change Password...';)
Thanks for sharing. That probably is the simplest way.

---

### Post by bodhi.zazen on 2008-06-19
> **sisco311 said:**
> :)

lets start again

you can change your own password with:
```
passwd
```You can't set up a weak password(to short or similar to the old one)

you can change your password to anything you want with:
```
sudo passwd
```NOT RECOMMENDED!!!

you can change other users password with:
```
sudo passwd <username>
```or you can use the gui (Users and Groups)

The command :

```
sudo passwd
```

sets the password for root and is not advised.

To lock root again :

```
sudo passwd root -l
```

that is a small "L"

---

### Post by sisco311 on 2008-06-19
> **bodhi.zazen said:**
> The command :

```
sudo passwd
```sets the password for root and is not advised.

To lock root again :

```
sudo passwd root -l
```that is a small "L"

You're right. Sorry.

Can somebody explain me why *sudo echo $USERNAME* prints my user name and *sudo passwd* sets the password for root.

---

### Post by chrisccoulson on 2008-06-19
> **sisco311 said:**
> You're right. Sorry.

Can somebody explain me why *sudo echo $USERNAME* prints my user name and *sudo passwd* sets the password for root.

Yes, sudo executes passwd as the root user, but passwd still inherits your environment, where $USERNAME equals your own user name.

If you do 'sudo whoami', it will come back with 'root'

---

### Post by bodhi.zazen on 2008-06-19
> **sisco311 said:**
> You're right. Sorry.

Can somebody explain me why *sudo echo $USERNAME* prints my user name and *sudo passwd* sets the password for root.

It has to do with two things.

First is security features of sudo and environmental variables. $HOME, $USER , $USERNAME, $SHELL are all environmental variables.

*any command you place after sudo is treated from your environment.*

so when you echo an environmental variable 

sudo echo $ENVIRONMENTAL_VARIABLE

you get your users (and not roots)

============

passwd id different. If you do not enter a user passwd defaults to user invoking the command, in the case of sudo it is root (passwd checks the uid , which was set to "0" by sudo and not an envrionmental variable).

============

try :

id

sudo id

See ? id is not an environmental variable, it is a command like passwd

:lolflag:

---

### Post by Dutch70 on 2008-07-18
I think what everyone here is trying to say is...
"USE THE GUI" :)

And anyone else, like myself, that needs to ask this question, probably should too.
How often are you going to change your password anyway?

---

