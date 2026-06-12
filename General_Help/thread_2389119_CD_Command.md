---
title: "CD Command"
date: 2018-04-11
forum: General Help
---

### Post by ragedog on 2018-04-11
Hello! The CD command is not working I will post some text below! Please tell me how to fix this. 

 WHAT I AM IMPUTING: cd /root/Discord/PixelHostBot

What Console is saying: Reference Error: cd is not defined 

Directory for the file: /root/Discord/PixelHostBot 

Please help me fix!

---

### Post by steeldriver on 2018-04-11
Hello and welcome to the forums

What "console" are you typing this in, exactly? the error you mention sounds more like a javascript error than an error from a *nix shell

---

### Post by ragedog on 2018-04-11
> **steeldriver said:**
> Hello and welcome to the forums

What "console" are you typing this in, exactly? the error you mention sounds more like a javascript error than an error from a *nix shell

The Terminal (Bitvise xterm)

---

### Post by QIII on 2018-04-11
Which OS, release/version are you running?

Which shell are you using?  Have you modified your $PATH variable recently?

---

### Post by lisati on 2018-04-11
I see that your thread is marked "Solved" 

If you have found the answer, it would be appreciated if you share it here, so others who might experience a similar problem might be able to benefit.

---

### Post by ajgreeny on 2018-04-11
Normally you can not see anything in /root unless you are using command **sudo -i** as your user to open a root command-line in terminal, or have enabled and logged into the root account in Ubuntu, which is not something that is recommended.

For example this is what I see if I try to cd to /root
```
user@XubuntuXenial:~$ cd /root
bash: cd: /root: Permission denied
```
I do not know what that error you see means as I have never seen it before, but from which directory are you running that cd command?

---

