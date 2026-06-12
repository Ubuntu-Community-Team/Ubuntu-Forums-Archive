---
title: "Passwords"
date: 2013-02-22
forum: General Help
---

### Post by Matt92HUN on 2013-02-22
Ubuntu is asking my password more often, than it's comfortable, after some reading I've seen that a lot of people thinks it would be dangerous to disable it. My question would be what are the possible risks of removing it, if I'm not doing financial things on it, I just use it for browsing my usual sites, playing and maybe programming in the future. I'm connected through a TP-LINK router and a Cisco modem, each of these have their own security solutions and I saw NOD 32 is available for Linux too.

---

### Post by mike555 on 2013-02-22
There are many threads about the password , you can set it to auto log you in , but don't set the password to nothing or blank because then you would not be able to update or install anything .you need a password.

---

### Post by Matt92HUN on 2013-02-22
> **mike555 said:**
> There are many threads about the password , you can set it to auto log you in , but don't set the password to nothing or blank because then you would not be able to update or install anything .you need a password.

And can I disable it for starting programs?

---

### Post by slickymaster on 2013-02-22
> **mike555 said:**
> There are many threads about the password , you can set it to auto log you in , but don't set the password to nothing or blank because then you would not be able to update or install anything .you need a password.

Big +1

The password prompt is indeed a good indicator of the severity of your actions. Nullifying the use of a password is a security risk. While entering your password every time is cumbersome, it is possible to set the password timeout higher (add Defaults passwd_timeout=10 to /etc/sudoers using the command sudo visudo). This would dissuade intrusion, unless the attacker has physical access.

---

### Post by zhaozhou on 2013-02-22
If you are starting programs such that a password is required, you are probably doing something you shouldn't be doing.

When Ubuntu asks you for a password it is because it needs to run an application as root (administrator), and this user will have full access to your data and hardware, and if the application is misbehaving - or worse yet, some kind of malware, then the application can cause a lot of harm to you and your computer. Examples include keyloggers, which can snoop up bank information, or adware.

Generally, you should be able to run applications as 'you', your user, not as root, and not have Ubuntu ask you for passwords for anything but installing packages or performing certain types of settings (such as user control).

---

### Post by Matt92HUN on 2013-02-24
> **zhaozhou said:**
> If you are starting programs such that a password is required, you are probably doing something you shouldn't be doing.

When Ubuntu asks you for a password it is because it needs to run an application as root (administrator), and this user will have full access to your data and hardware, and if the application is misbehaving - or worse yet, some kind of malware, then the application can cause a lot of harm to you and your computer. Examples include keyloggers, which can snoop up bank information, or adware.

Generally, you should be able to run applications as 'you', your user, not as root, and not have Ubuntu ask you for passwords for anything but installing packages or performing certain types of settings (such as user control).

Initially it was a lot, because I was installing a lot, but now it still asks for password, when I open a browser, or some other programs.

---

### Post by matt_symes on 2013-02-24
Hi

> **Matt92HUN said:**
> Initially it was a lot, because I was installing a lot, but now it still asks for password, when I open a browser, or some other programs.

Then it sounds like you have a problem with your setup as it should not ask for a password when opening a browser.

What browser do you use ?

Kind regards

---

### Post by sudodus on 2013-02-24
> **Matt92HUN said:**
> Initially it was a lot, because I was installing a lot, but now it still asks for password, when I open a browser, or some other programs.
Maybe something is wrong. Ubuntu does not ask for password, when I open a file browser, unless I would open it with
```
gksudo nautilus
``` because I want to to some system task. But I do my system tasks with terminal window commands, so I hardly ever start the file browser with root privileges.

If your internet browser asks for password, you might be owned. I would never do that (connect to the internet with root privileges).

---

### Post by mike555 on 2013-02-24
Sounds like it is asking password for your password remembering program keyring , you can set it to a blank password if you want .....

---

### Post by matt_symes on 2013-02-24
Hi

> **mike555 said:**
> Sounds like it is asking password for your password remembering program keyring , you can set it to a blank password if you want .....

Good call. That could well be it.

Kind regards

---

