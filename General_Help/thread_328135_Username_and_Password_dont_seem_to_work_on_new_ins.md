---
title: "Username and Password dont seem to work on new install"
date: 2006-12-30
forum: General Help
---

### Post by dalepearson on 2006-12-30
Hiya All, 

I am new to Linux and ubuntu.

I have just installed ubuntu on my laptop, it has now rebooted and asked me to login using the info I specified at install.

However its not working. Can anyone help or do I need to install again?

Thanks in advance.

---

### Post by taurus on 2006-12-30
Did you use the LiveCD or the alternate CD to install?  What's the error message when you try to log in with your username and password (and what is your username anyway)?

---

### Post by Solver on 2006-12-30
To start with the simple things: usernames and passwords are case-sensitive. So you need to type them like you did during install, exactly.

Also, you might have accidentally had Caps Lock on when typing the password during installation. So if you thought you typed in "pAss13", your actual password would be "PaSS13" if you had Caps on at that point.

---

### Post by dalepearson on 2006-12-30
Hiya I have tried with caps and caps off, and possible mistakes I think I might have made.

The error is - Incorrect username or password. Letters must be typed in the correct case.

Is there not a root default I can use to get in and modify my account?

---

### Post by dalepearson on 2006-12-30
> **taurus said:**
> Did you use the LiveCD or the alternate CD to install?  What's the error message when you try to log in with your username and password (and what is your username anyway)?

I used the LiveCD I believe.

---

### Post by Solver on 2006-12-30
Does your password contain the " (double quotes) or @ (at) characters? These characters are different between, if I recall correctly, UK and US keyboard layouts. As such, if you changed your keyboard layout during the install, it's possible for you to think you type one of those characters but type the other. What did you set the keyboard layout to anyway?

---

### Post by taurus on 2006-12-30
Boot into recovery mode from GRUB menu and paste the last few lines of this command here?  Just want to see if you actually have a username on your machine!  Then, we can reset the password again...

```
cat /etc/passwd
```

---

### Post by dalepearson on 2006-12-30
> **Solver said:**
> Does your password contain the " (double quotes) or @ (at) characters? These characters are different between, if I recall correctly, UK and US keyboard layouts. As such, if you changed your keyboard layout during the install, it's possible for you to think you type one of those characters but type the other. What did you set the keyboard layout to anyway?


I have the @ sign in my password and I set it to UK keyboard before and UK now, I tried it on US just incase no change.

---

### Post by dalepearson on 2006-12-30
> **taurus said:**
> Boot into recovery mode from GRUB menu and paste the last few lines of this command here?  Just want to see if you actually have a username on your machine!  Then, we can reset the password again...

```
cat /etc/passwd
```

Ok I have done that, loads of text has filled lots of the screen. What am I looking for, is there a way to page scroll it?


Thanks.

---

### Post by taurus on 2006-12-30
What's your login name?  Again, boot into recovery mode from GRUB menu and change the password to something that that doesn't require a special character...

```
passwd **dalepearson**
<new passowrd>
<re-type new password>
(assuming **dalepearson** is your login name...)
```
Then, reboot and see if you can login with the new password!

```
shutdown -r now
```

---

### Post by dalepearson on 2006-12-30
> **taurus said:**
> What's your login name?  Again, boot into recovery mode from GRUB menu and change the password to something that that doesn't require a special character...

```
passwd **dalepearson**
<new passowrd>
<re-type new password>
(assuming **dalepearson** is your login name...)
```
Then, reboot and see if you can login with the new password!

```
shutdown -r now
```

worked a treat. Many Thanks for the support. Really appreciated.

---

### Post by taurus on 2006-12-30
> **dalepearson said:**
> worked a treat. Many Thanks for the support. Really appreciated.

Glad to hear that you can now log in to your machine.

Have fun.

---

### Post by mercenary on 2007-01-01
I too forgot the user/login I had on my internet connection sharing machine.  Could not believe getting in was this easy.  Doesn't seem very secure.

---

### Post by taurus on 2007-01-01
> **mercenary said:**
> I too forgot the user/login I had on my internet connection sharing machine.  Could not believe getting in was this easy.  Doesn't seem very secure.

It will never secure if somebody has a physical contact with your machine.  And if you want to be save, you can also create a password for GRUB!!!  But then a person with a LiveCD can get into your machine anyway...  ](*,)

---

