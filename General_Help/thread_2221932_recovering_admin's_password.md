---
title: "recovering admin's password"
date: 2014-05-04
forum: General Help
---

### Post by Robbyx on 2014-05-04
The person who sold me an old Dell GX620 had put Ubuntu 12.10, but ommitted to give me the password. 

I have set up a new password using the method at [http://naveenubuntu.blogspot.co.uk/2012/05/recover-login-password-of-ubuntu-1204.html](http://naveenubuntu.blogspot.co.uk/2012/05/recover-login-password-of-ubuntu-1204.html)

which in effect explains how to change the password by the root in the recovery mode.

It all went well and I was able to set up a new password for the main  admin user,  and yet when I get into the desktop and try to login with the new password it is not recognised.

Does anyone know what I should do next?

---

### Post by grier-devon on 2014-05-04
The issue I see with the guide you posted is people are calling him out for syntax error's and claiming it does not work. Here is the official documentation and you should always try to use the official Ubuntu Documentation where possible.
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

EDIT: I just noticed you said it has 12.10 installed. You are not using a supported version of Ubuntu right now anyway so I would consider downloading and installing 14.04 as this is a LTS and will give you five years of support and then you can set a new password in the installer.

---

### Post by Robbyx on 2014-05-04
I have looked at your referal and it is what I did. Did you notice that I successfully changed the password at the root but it is not recognised when I login! By successful I mean that it reported that I had successfully changed the password.

---

### Post by grier-devon on 2014-05-04
Here is a way to do it through a live cd
[http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/)

Though if you have never had access to the machine which means non of your data is on there then it is silly to not do a fresh install with a supported version of Ubuntu as 12.10 will have security flaws not being fixed, old software and less hardware support out of the box.

---

### Post by deadflowr on 2014-05-04
Since you've enabled the root password, which is normally a no-no here, try this.

when you boot into Ubuntu, as you get to the login screen, press ctrl + alt + F1(or F2)
You will get tty1,or tty2.
login in as root,  with the newly made root password.
when logged in run
```
passwd username
```
changing username here for you normal username.

now enter 
```
reboot
```
When you reboot the new password for your user should work to log you in.

After to log in open a terminal and run this
```
sudo passwd -dl root
```

This will re-disable the root password.
Which is the preferable state.

Good luck.

---

### Post by Robbyx on 2014-05-04
Deadflowr: Thank you I have now been able to login. For me the ilogical part was that I was changing username's password  at root level, but a login I could not use the same password. I did not enter "root" when I changed the password for username.

---

### Post by deadflowr on 2014-05-04
> **Robbyx said:**
> Deadflowr: Thank you I have now been able to login. For me the ilogical part was that I was changing username's password  at root level, but a login I could not use the same password. I did not enter "root" when I changed the password for username.

Did you simply use passwd, without a username?
I think it defaults to root.
Like su, where simply su moves you into root, su username will move you into the other username.
I'm guessing, though.

---

### Post by Iowan on 2014-05-04
> **deadflowr said:**
> Did you simply use passwd, without a username?
I think it defaults to root.
Like su, where simply su moves you into root, su username will move you into the other username.
I'm guessing, though.As mentioned in the Wiki:
>  This procedure gives you a full root shell! You can damage your system if you are not careful! So, as root, if you didn't specify a username, the system changed the root password.

---

### Post by sammiev on 2014-05-04
Any computer I would of bought from another person would have been wiped and installed with the OS I wanted afterwards. I hope you trusted the person you bought it from. :shock:

---

### Post by nothingspecial on 2014-05-04
What you need to do is download the latest ubuntu, install it, and set it up for yourself.

[http://www.ubuntu.com/download/desktop/](http://www.ubuntu.com/download/desktop/)

---

### Post by deadflowr on 2014-05-04
I'll 4th(or 5th, or 6th) the recommendation of a fresh install, if at all possible.

For the record 12.10 isn't EOL until May16.
[https://lists.ubuntu.com/archives/ubuntu-security-announce/2014-April/002488.html](https://lists.ubuntu.com/archives/ubuntu-security-announce/2014-April/002488.html)
FWIW

---

