---
title: "I can't even login, black screen! [SOLVED]"
date: 2014-08-22
forum: General Help
---

### Post by elisa3 on 2014-08-22
Hi
I wanted to fix something, and I followed the advice given by someone on the #ubuntu IRC chat. I don't think I did it properly, because now, I cannot even login and I have a black screen. Ii must be a Gdm / Lightdm issue... I am writing this from another computer. Is there a way I can solve this without formatting and losing all my files? All I have is the GRUB menu. I don't even have the recovery mode on the GRUB menu...

---

### Post by Bashing-om on 2014-08-22
elisa3; Hi !

It's ubuntu, 
It is always fixable  if you have a liveDVD, easier if you can boot to a terminal;
Let's see if you can boot to that terminal:

At your grub boot menu with the latest kernel highlighted press the 'e' key for edit mode -> boot options screen;
arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes;
key combo ctl+x to continue the boot process to a text terminal (TTY1).
Log in here with username and password ( no response to the screen, enter pass word blindly and hit the enter key).
Once logged into the system, what results from terminal command:
```

sudo service lightdm start

```

Gotta start trouble shooting somewhere
[INDENT][INDENT][INDENT]looks like a good place to me
[/INDENT][/INDENT][/INDENT]

---

### Post by elisa3 on 2014-08-22
Thanks, it worked!

---

