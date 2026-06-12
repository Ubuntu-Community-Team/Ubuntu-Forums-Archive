---
title: "Need Help With Xubuntu login"
date: 2007-05-04
forum: General Help
---

### Post by Jamidell on 2007-05-04
This is the first time i have used linux i downloaded Xubunu 6.06.1 LTS. When i first started it up all looked good untill it came up with the blaock screen with 2 line of text one saying the version number and what i had named the PC and the second saying dell02 login:

I do not rember entering any user name at all in the install i only entered a password!! so what do i do? and even if i jsut write and login name i cant type in a password afterwards what is wrong!!

Please help

Jamie

---

### Post by taurus on 2007-05-04
Use **oem** as your login name and the same password that you created during the installing process.  Once you log in, run this command to create an actual account for you to use from now on.

```
sudo oem-config-prepare
```

---

### Post by BujinMakoto on 2008-03-08
I have the exact same problem. However, when I enter that command, it says, "sudo: oem-config-prepare: command not found"

What do you advise?

---

