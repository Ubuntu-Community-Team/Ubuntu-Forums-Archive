---
title: "login problems"
date: 2022-10-18
forum: General Help
---

### Post by Don DeGregori on 2022-10-18
Using 32 bit  Lubuntu 18.04. Haven't used machine for awhile. I boot up OK. Password not needed. That's how it has been.
Now, I see 400 MB of updates that can be downloaded. I try but system needs authorization password. I don't remember the password and
if it was needed before. Anyway can't do the updates. I understand 32 bit machines are not supported anymore by Ubuntu.
Question is why was I able to login without a password, and now I need a password for updates, or maybe I did need a password. Right now I would like to  get rid of all passwords, for the machine is used just by me. I have read 10's of answers on the web with no real answers. I'm even having trouble getting into grub, going in circles. Please help ... Thanks, Don

Adding:  Can't find UNIX password either

---

### Post by MAFoElffen on 2022-10-18
The auto-login feature tells the system to login (using the main User's credentials) straight to the Windows Manager...

If you do not remember the passwords., then reset it... At the Windows manager, open a terminal session and type
```

whoami

```
Copy down the UserName it returned as output... Reboot the computer... After the BIOS messages, hit the <Esc> key repetedly to bring up the Grub Boot Menu. When that comes up, arrow down to "Advanced". Select.

At that menu, select an Option containing "Recovery"... Select

When it boots to the Recovery menu, select "drop to root prompt."

At the root prompt, enter
```

passwd UserName

```
Changing UserName with the UserName you copied down... Reneter the passsword to confirm it.

Type 'reboot' to reboot the computer...

---

### Post by grahammechanical on 2022-10-18
> Question is why was I able to login without a password, and now I need a password for updates, or maybe I did need a password.

When you installed Lubuntu, as with any flavour of Ubuntu, you were required to set a user name and password. You then set Lubuntu to automatically log you in. Some software updates such as kernel updates require user authentication which means entering the password we set during the installation process. Authentication is often required when we want to change certain system settings.

Nothing has change during this period of time that you have not been using Lubuntu. I doubt that is possible to do without passwords entirely. Using an operating system that has not been updated while connected to the internet will open that machine to attack by malicious software.

I am guessing that a kernel update is part of that 400 MB update. That is why you are being asked to provide a password. I also think that after you enter the password you will still not be able to update that system because Lubuntu 18.04 has reach the end of its support life. And the software repositories have been moved to servers with a different address compared to the addresses that Lubuntu 18.04 will look for.

[https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

To keep using that machine with an up to date Linux OS you will need to choose another distribution of Linux. Here are some distributions that still support 32 bit versions of \linux.

[https://itsfoss.com/32-bit-linux-distributions/](https://itsfoss.com/32-bit-linux-distributions/)

[https://www.debugpoint.com/32-bit-linux-distributions/](https://www.debugpoint.com/32-bit-linux-distributions/)

Regards

---

