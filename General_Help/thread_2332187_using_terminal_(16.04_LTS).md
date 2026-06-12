---
title: "using terminal (16.04 LTS)"
date: 2016-07-29
forum: General Help
---

### Post by JAST20 on 2016-07-29
The terminal to paste commands for 16.04 LTS is different than 14.04 LTS. How do you use it and what is different ? Need help  :confused:.

to run a command as administrator (user"root"), "use sudo <command>".
see "man sudo_root for details 

I don't understand what this means .:(

---

### Post by howefield on 2016-07-29
It just means that you need to use sudo to preface any command that requires administrator privileges, that message should only be shown the first time you load the terminal after installing. The terminal works in the same way as it did before.

---

### Post by JAST20 on 2016-07-29
Ok thanks !! I added sudo  and it asked for password as normal  and the message disappeared when I reopened it again. 
Can you give me a simple command to paste into it to test ?

---

### Post by alexandr-kaprizkin on 2016-07-29
```
sudo apt-cache policy firefox
```

It will display if Firefox is installed, and what version is installed.

---

### Post by JAST20 on 2016-07-29
Yep everything is familiar again !! Works fine ! Thanks for help :P

---

### Post by howefield on 2016-07-29
> **JAST20 said:**
> Yep everything is familiar again !! Works fine ! Thanks for help :P

Cool, once you run the terminal for the first time and then close it, a hidden file is created in your home folder called "*.sudo_as_admin_successful*". Deleting this file would make the sudo message reappear. Just for your info :)

---

