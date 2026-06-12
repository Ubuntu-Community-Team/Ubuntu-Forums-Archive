---
title: "Unable to log in as root"
date: 2007-12-01
forum: General Help
---

### Post by FDDave on 2007-12-01
I'm pretty much a noob to Ubuntu and Linux in general. I have a basic knowledge of computers, but I still need guidance.

I got through the Ubuntu installation without much hassle. However, I was never asked for a root password, as I was told I should have been. So I went into the administration menu and set the root password. When I tried to log in as root, I was simply told "The system admin is not allowed to log in from this screen".

Does anybody know anything about this? I'm pretty well lost. I was told I needed to go into the root account in order to work with bin files. (I'm trying to update my AVG anti-virus that I just installed. The program told me I didn't have permission to upgrade it, so I went to the website and downloaded the upgrades manually. Now I'm completely lost on what to do.)

---

### Post by scxtt on 2007-12-01
by default, you can preface any command on the CLI w/ **sudo** (using the account you created @ install) and gain root privs ...

***sudo su -*** would get you a root prompt, using your user password when prompted.

once you're root, typing **passwd** and entering a new password should set it (if there was some problem earlier).

---

### Post by FDDave on 2007-12-01
That let me do what I needed. Thanks for the help!

---

### Post by BrianR on 2008-01-11
What if I have lost the root password? I will be booting up with a Live CD so I can get to a command line.  What file can I delete to remove the root password so I can go back in and use the passwd command?

---

### Post by p_quarles on 2008-01-11
You don't want to delete anything. Use the "recovery mode" option in the GRUB boot menu to login as root, and then reset any passwords that have been lost:
```
passwd *username*
```

---

