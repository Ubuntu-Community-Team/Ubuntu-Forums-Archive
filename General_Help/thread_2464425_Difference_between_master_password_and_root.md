---
title: "Difference between master password and root?"
date: 2021-07-01
forum: General Help
---

### Post by thorbs on 2021-07-01
I was trying to install an hp printer and was asked for my master password. I just typed my normal root password, but kept getting errors. Is there a difference between master passwords and root?

---

### Post by grahammechanical on 2021-07-01
What were the error messages? What command was you running? Your password may be correct but your command may be incorrect. The problem may be caused by an inaccurate path to the printer driver.

Regards

---

### Post by ajgreeny on 2021-07-01
And you say "typed my normal root password".

what exactly do you mean by that as Ubuntu does not use a root password; we use sudo with our user password to temporarily raise our permissions and carry out such activities.

Occasionally users do set a root password and then find problems related to this, then ask questions here about this.
Is this what you have done?

---

### Post by thorbs on 2021-07-02
I apologize for being unprecise just shows I do not know what I am talking about. I was trying to install my printer using this guide [https://askubuntu.com/questions/1056077/how-to-install-latest-hplip-on-my-ubuntu-to-support-my-hp-printer-and-or-scanner](https://askubuntu.com/questions/1056077/how-to-install-latest-hplip-on-my-ubuntu-to-support-my-hp-printer-and-or-scanner) . After succesfully going through it and connecting my computer to printer with usb, it asks me for masterpassword/root and I type my sudo password and get three errors. I can not get the precise printout, as I dont know how to run it again. 
Thank you for the help.

---

### Post by dragonfly41 on 2021-07-02
Reading that linked article .. have you tried running the command in terminal

```
hp-doctor
```
to run through the configuration?

This asks for your normal sudo password.

There is also CUPS to try ..

[http://localhost:631/admin](http://localhost:631/admin)

---

### Post by coffeecat on 2021-07-02
Let's clear up a few points.

[list=1][*]I've not come across the term master password in relation to Ubuntu. I guess you mean the user password for the administrative account. The first created account in any Ubuntu installation has administrative privileges. These privileges can be invoked when prompted for the password by certain GUI apps that need root permissions. You use your user password. Similarly you can temporarily elevate yourself to root privileges in the terminal by the use of sudo and your user password. Your user password is not the root password.
[*]Root has its own account. In Ubuntu, the default is for the root password not to be defined. You can create a root password, but there is no real need. Please - pretty please - do **not** be tempted to enable the root password.
[*]If you get repeated errors when typing in a password, you are either typing it in wrongly (is caps-lock on?), or typing in the wrong password. Or, possibly, using a non-administrator account when trying to use sudo.[/list]

As far as hplip is concerned, the likelihood of needing to follow the guide you linked approaches zero. Hplip comes as default in any Ubuntu installation. The only time you need to install hplip is when you need a later version than that in the Ubuntu repositories because you have the latest and shiniest model from HP that needs a later driver. In my experience, over several years, HP printers are just plug in and use. I have very rarely had to do any configuration or fiddling about at all. If you are experiencing difficulty getting your HP machine to work with Ubuntu, I suggest you start a new thread with an appropriate title, describing the problems you are encountering, and not forgetting to specify the flavour and release of Ubuntu that you are using, and the model number of the HP machine, and whether this is a network machine or connected via USB.

---

### Post by him610 on 2021-07-02
Don't know if this applies to the posted problem, but one can access some manufacturers printers by just typing in the IP address. My Brother printer has settings for both the User and the Administrator (password required for both).  I also have access to a Dell printer that has way to set a password for the Admin account.
Never heard of 'Master' password, nor have I ever seen reference to it except in this thread.

---

