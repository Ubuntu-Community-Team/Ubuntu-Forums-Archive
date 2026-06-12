---
title: "The computer ask me twice for the password."
date: 2013-03-05
forum: General Help
---

### Post by FerBravo on 2013-03-05
Hello,

I have installed Ubuntu 12.10 and when I start the system the screen goes black --> I have to press scape so letters resembling MS-DOS type appear and then the system ask me for my password --> I imput the password and then the graphic interface appears and I have to imput my password again. Is this normal? Thank you :)

---

### Post by FerBravo on 2013-03-06
up

---

### Post by grahammechanical on 2013-03-06
No, it is not normal. Linux is a command-line OS and Ubuntu sits on top of it. So, when we boot we get Linux loaded. Sometimes we may see a black screen with a command-line prompt but we should not need to enter a password there. The loading process should then jump to the login screen. I cannot think of a reason why this is happening. Do you allow enough time for the loading process to continue? When you enter your password at the graphical login do you get to a working desktop?

Sometimes if there is a fault with the video driver we get stuck at a black screen with a flashing cursor but I doubt if entering a password at that point would fix the problem. You would need to run some command to possibly get to the desktop. I do not know what to suggest, except to boot into Recovery Mode and select the Resume option and see if that avoids this problem.

At the Grub boot menu select Advance Options for Ubuntu and select Recovery Mode. Then at the menu that appears select Resume. We really need more information. If this is a very new install of 12.10 you may want to think about installing 12.10 again.

Regards.

---

### Post by MyTinFoilHat on 2013-03-06
I'm wondering if OP perhaps elected for full disk encryption during installation. If so, I believe the user would be prompted twice: once for access to the drive itself and another time for regular desktop login. I could be wrong, I'm a newbie here myself, but I know I've seen this before and thought I'd contribute this idea - just in case. If someone could back this up (as a potential candidate for OP's cited issue), perhaps this would help OP a bit further. (Not that I think grahammechanical is wrong - I'm just contributing another idea toward a possible solution).

---

