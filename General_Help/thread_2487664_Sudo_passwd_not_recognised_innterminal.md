---
title: "Sudo passwd not recognised innterminal"
date: 2023-06-12
forum: General Help
---

### Post by dalpets on 2023-06-12
I have just installed the latest version of Ubuntu on a Raspberry Pi 400. When I try to sudo my user installed password in the terminal it is not recognized.
Some help on this would be appreciated.
thank You

---

### Post by ajgreeny on 2023-06-12
Can I just check that you know that no password that you type is echoed on screen; type it carefully and hit Enter.

---

### Post by dalpets on 2023-06-12
> **danielpage-976 said:**
> First of all Verify user privileges, Double check the password, Use the correct user, Check for typos and reset password using recovery mode.

Well, the password works for logging into the operating system- why doesn't it work in the terminal? I have no problem with privileges to login. Am I to believe that the terminal has a different set of privileges.
I's not a typo. That would have shown up by now after 10 or more tries. Surely it must be another issue.

---

### Post by dalpets on 2023-06-12
> **ajgreeny said:**
> Can I just check that you know that no password that you type is echoed on screen; type it carefully and hit Enter.

Really?

---

### Post by ActionParsnip on 2023-06-12
> **dalpets said:**
> Really?
It covers a base, worth mentioning

---

### Post by dalpets on 2023-06-12
Are these extant user privileges sufficient to use sudo for this one & only user.? Do I need  a 'wheel' entry?

uid=1000(brenton) gid=1000(brenton) groups=1000(brenton),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),100(users),118(lpadmin),131(sambashare)

---

### Post by Impavidus on 2023-06-12
What's the exact symptom you see? Does sudo complain that the password is incorrect? Does sudo tell you that you don't have permission to do something as root? Does the tool you use with sudo not run as root? Does sudo do nothing at all (after typing the password blindly and hitting enter)?

---

### Post by TheFu on 2023-06-12
> **dalpets said:**
> Are these extant user privileges sufficient to use sudo for this one & only user.? Do I need  a 'wheel' entry?

uid=1000(brenton) gid=1000(brenton) groups=1000(brenton),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),100(users),118(lpadmin),131(sambashare)

Being a member of the 'sudo' group should be sufficient, but there could be something funny in your sudoers file or sudoers.d/ directory which is non-default.  For ubuntu x86-64 systems, sudo is the group membership which conveys the ability to use sudo with the privileges provided in the sudoers config file.  If you've screwed with it, hopefully, you made a backup of the config file before modifying it and can restore the default.

Permissions aren't different between GUIs and CLI.  However, if you modify group membership, then you can have those changes see in 1 terminal session using the newgrp command, or across the entire login session by logging out and logging in again.  

There is a bug against systemd where group changes aren't always picked up with a logout/login cycle. The fix is a system reboot.  Maybe that bug has been fixed. IDK.

---

