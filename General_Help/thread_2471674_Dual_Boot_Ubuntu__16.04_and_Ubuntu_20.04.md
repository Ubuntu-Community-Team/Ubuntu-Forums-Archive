---
title: "Dual Boot Ubuntu  16.04 and Ubuntu 20.04"
date: 2022-02-06
forum: General Help
---

### Post by rsteinmetz70112 on 2022-02-06
I have a desktop computer running Ubuntu 20.04, it works just fine. It also had 16.04 installed on it in a completely different partition. The gurb menu correctly identifies the 16.04 as being on /dev/sda1 and allows me to select it. The boot process starts but the splash screen drops out and I get a terminal screen with a login in prompt. I know the user names and password for some of the users but they don't work. It appears to accept the password and the initial login message flashes up but I immedistely get another login prompt.

Any idea whats happening?

---

### Post by grahammechanical on 2022-02-06
> and I get a terminal screen with a login in prompt

At  the login screen we can login as different users if they are registered  on the system and we know the passwords. At that terminal screen we can  only log in as the user with administrative privileges (sudo). You do  not seem to have the password.

It also seems that the desktop  environment is not loading. At the Grub menu choose Advanced options for  Ubuntu and select an older Linux kernel and see what happens.

But  you have another problem. Ubuntu 16.04 reached the end of its standard  support life during April 2021. You will not be able to update that  system. You will need to get Extended Security Maintenance (ESM) to  continue safely using 16.04

[https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)

Regards

---

### Post by rsteinmetz70112 on 2022-02-06
I've tried several different kernels with the same result. I have the correct password for at least 2 users with sudo privileges.  What is happening is not like entering the incorrect password, the login seems to start but is aborted somehow. I don't know why the desktop is not loading. I'm aware 16.04 has reached EOL, I was trying to see if there was anything there I need to recover.

---

