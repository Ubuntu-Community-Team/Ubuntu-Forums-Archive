---
title: "how do you log into swat with all options?"
date: 2007-01-01
forum: General Help
---

### Post by mark076h on 2007-01-01
i got swat installed and when i go to [http://localhost:901/](http://localhost:901/)  it works fine but when i login in i only have the HOME , STATUS, VIEW , PASSWORD options , i read that i need to login as root how do i do that? the user i login as has admin capabilities and same password i use for SUDO?

---

### Post by mark076h on 2007-01-01
anyone?

---

### Post by floydian on 2007-01-08
I ran into the same problem.  You have to log in with the root password to make full use of SWAT.  The problem is that the root password in Ubuntu is disabled by default, which is why you have to use sudo to perform administrative tasks with your primary logon.

Sudo doesn't work in SWAT, so you'll have to enable the root password by entering the following at the comand line:

**sudo passwd root**

Follow the prompts to enable the root account and set a password.  Make this a good password!

Once you've enabled the root account you should be able to login to SWAT with it.  All of the SWAT functions should now be available.

---

