---
title: "Root password problem"
date: 2013-09-20
forum: General Help
---

### Post by gilad2 on 2013-09-20
Hey all,
I installed ubuntu and set a password, after some use I decided that I don't want to type password every log in to my comp so I desabled the password completely
now when I try to do something that require root premissions and type the password I setup ubuntu with it doesn't work..
I tried the common way to reset pass, [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
press shift while rebooting the comp and in GRUB choose linux in rescue/recovery mode, but I doesn't have the option

any option other then re-install ubuntu?

thx for help

---

### Post by sudodus on 2013-09-20
Welcome to the Ubuntu Forums :-)

What option is there and what option is not there?

Can you come to the grub menu with the left shift button (you might need to press it at once or even slightly before you boot. Try with cold boot.

Have you edited the grub menus? If not, there should be an entry Advanced options. Select it and press Enter. Then you should arrive at a second grub menu, where you can select recovery mode and press Enter.

---

### Post by grahammechanical on 2013-09-20
First of all for the sake of others that might want to do this, there is a simple way to to achieve this. Open System Settings>User Accounts and there is a switch for switching automatic login on and off.

Second at the Grub menu select Recovery mode. At the Recovery menu select Network. That will establish a connection to the router and give an internet connection. It will also put the file system in Read/Write mode which is necessary for editing system files. When this script has done its job it will return to the Recovery menu. Now select Root and you can do what you need to do to reset the password. You will be at a command prompt. When you are finished type Exit to return to the Recovery menu and now select Resume to load to a desktop.

Regards.

---

### Post by deadflowr on 2013-09-20
The timing to get the grub menu is key.
Alternatively, you can use a livecd to run recovery options like resetting a password
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)

But +1 to running networking first from recovery mode.(when using recovery mode)
It might take a while, and might seem like it hangs, but it does return you to the recovery screen window with read/write access rather then read-only.

---

