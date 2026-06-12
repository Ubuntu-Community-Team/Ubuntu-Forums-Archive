---
title: "Unable to change my password!"
date: 2013-03-26
forum: General Help
---

### Post by mijab on 2013-03-26
When I am turning my laptop on, I hold shift, and then I can choose the "recovery mode". Then I choose "root", and as I'm supposed to I type in passwd (my user name), and then opens a field enter your new password, **but I can't write anthing!** I have literally tried every single button on my keyboard, only enter works, so I press enter, another field that says retype passwod opens, and again I can't press anything, so I press enter and the it says : "authentication token manipulation error" and in another field : "cannot lock /etc/shadow". What am I supposed to do?? Please help me! :(

---

### Post by ManamiVixen on 2013-03-26
As a security measure, linux terminal NEVER shows what is being typed as the password. So just type your password and hit enter. 

Anyways, what happened? Why are you in recovery mode?

---

### Post by steeldriver on 2013-03-26
2 things

1) the screen does not 'echo' what you type in the password field - not even as asterisks like ****** that's for security reasons - but it **is** being entered

2) if you are working in the recovery shell, you will need to remount the filesystem to make it writable else the system can't save your new password i.e.

```
mount -o remount,rw /
passwd username
```

Note that there is no space between the [FONT=courier new]remount,rw[/FONT] command options

---

### Post by mijab on 2013-03-27
Thank you sooo much! I feel so stupid... Well I forgot my password, so I was trying to change it! Thank you, thank you, thank you!!!!!!

---

