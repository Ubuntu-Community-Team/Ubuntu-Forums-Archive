---
title: "Can I set a password after installing 14.04LTS?"
date: 2018-04-17
forum: General Help
---

### Post by Richard_York on 2018-04-17
We have Ubuntu 14.04 LTS on both desktop & laptop machines. At the time of installation I didn't set the need for a password to be required before booting up. Now I'd like to put that requirement in, retrospectively, without having to go back & reinstall everything.

Can this be done, please, and if so, how?

Thanks.

---

### Post by #&amp;thj^% on 2018-04-17
> **Richard_York said:**
> We have Ubuntu 14.04 LTS on both desktop & laptop machines. At the time of installation I didn't set the need for a password to be required before booting up. Now I'd like to put that requirement in, retrospectively, without having to go back & reinstall everything.

Can this be done, please, and if so, how?

Thanks.

Enter the following command in a terminal or bash window.

```
sudo passwd 
```

And Enter your password (sudo user password admin)

---

### Post by deadflowr on 2018-04-17
What do you mean?
You can't install without setting a password.

Are you meaning you set it to autologin?

or
> I didn't set the need for a password to be required before booting up.
do you mean setting up a crypto-something passphrase?
Used for full disk encryption setups.

I'm confused as to which password at boot you are referring to.

---

### Post by kerry_s on 2018-04-17
could you mean you want to disable auto login?

---

### Post by #&amp;thj^% on 2018-04-17
> **deadflowr said:**
> What do you mean?
You can't install without setting a password.

I'm confused as to which password at boot you are referring to.

+100 :D i did not even consider that ! I'm betting OP wants to disable auto login.

---

### Post by yancek on 2018-04-17
To repeat what was said above, in all the years I've used/installed Ubuntu it has been impossible to complete the install without creating at least one user with one password.  This would be the primary user with root/admin privileges.  You can easily create a password for another user.  Clarify your situation please.

---

### Post by Richard_York on 2018-04-17
> **1fallen said:**
> +100 :D i did not even consider that ! I'm betting OP wants to disable auto login.

I do apologise for using the wrong term. I reveal my lack of computeracy! Yes, there is of course a password which I set when installing, but it's not needed to login - switch on the power & the machine opens up without further need for password, and that's what I want to change.
Thanks for your patience!

---

### Post by #&amp;thj^% on 2018-04-17
> **Richard_York said:**
> I do apologise for using the wrong term. I reveal my lack of computeracy! Yes, there is of course a password which I set when installing, but it's not needed to login - switch on the power & the machine opens up without further need for password, and that's what I want to change.
Thanks for your patience!
You will need to edit as root this file: "/etc/lightdm/lightdm.conf"
 

```
sudo -H gedit /etc/lightdm/lightdm.conf 
```

It displays some text as follows:

```
[SeatDefaults]  
greeter-session=unity-greeter  
user-session=ubuntu  
autologin-user=username

```
This <username> would be your particular user name that is automatically logged in with or without password. Delete this username and type in the administrative username **or leave it blank.**
I would just delete the username.

Reboot the system. It will boot to the login selection screen with the password needed.

---

### Post by deadflowr on 2018-04-17
Simple:
Open User Accounts Either through the dash search or inside system settings.
Click the unlock at the top right corner.
Then toggle the Automatic Login from on to off.
Do not mess with anything else.
Close the window and you should now require a password to login.

---

### Post by Richard_York on 2018-04-18
> **deadflowr said:**
> Simple:
Open User Accounts Either through the dash search or inside system settings.
Click the unlock at the top right corner.
Then toggle the Automatic Login from on to off.
Do not mess with anything else.
Close the window and you should now require a password to login.

Wow - as you say, simple. Thank you, that's much easier than I was expecting :-)

---

