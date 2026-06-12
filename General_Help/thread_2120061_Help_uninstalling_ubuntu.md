---
title: "Help uninstalling ubuntu?"
date: 2013-02-25
forum: General Help
---

### Post by ngrant on 2013-02-25
I installed ubuntu so i could get the tux penguin in tf2. i found an install on the ubuntu webpage that said i should be able to easily install and uninstall ubuntu, so i tried it. and i prefer windows over ubuntu, and i want to uninstall ubuntu. but i dont have the slightest clue how to switch back. Please, can someone help me? And is there a way i can do this so i can get all my applications that were on windows back? Please, I need help

---

### Post by KnownSyntax on 2013-02-25
When you installed Windows did you:
A) Remove the whole partition that had Windows on it
B) Dual booted Ubuntu and Windows 
C) Installed Ubuntu but overrode Window's GRUB so that Ubuntu would automatically boot if turned on and it wouldn't say anything about having Windows installed?


If you did A or C then you'll need to grab a copy of a Windows .iso, (for option C) burn it to reinstall Window's default GRUB manager, or (for option A) reinstall Windows completely and if you don't want Ubuntu anymore then erase it's partition. 

If you did B, then you can boot up Windows and then go into the Disk Manager and remove Ubuntu's partition to erase everything Ubuntu related on your system.

---

### Post by ngrant on 2013-02-25
well i dont know if i did any of those things. all i know is that i installed it from this link 
[http://www.ubuntu.com/download/desktop/windows-installer?distro=wubi&release=&bits=](http://www.ubuntu.com/download/desktop/windows-installer?distro=wubi&release=&bits=)
and i just want to get it back to windows 7. when the installer popped up, the only thing i did was the username and password, and switched it to the 5 gb version and clicked install.

---

### Post by KnownSyntax on 2013-02-25
This should solve your problem, didn't notice you were using the Wubi installation method: [https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_uninstall_Wubi.3F)

---

### Post by ngrant on 2013-02-25
o thx.
but how do i get there? (note, i dont know if this will help, but i dont know how to go back to windows, i am stuck on ubuntu)

---

### Post by ajgreeny on 2013-02-25
I've never used wubi (don't even have windows to use it in!) but at bootup you should see a menu option giving you the choice of using Ubuntu or Windows; choosing Windows should take you to the Windows OS from where you uninstall Ubuntu just like you uninstall any other application.

If you don't get that first choice of Windows or Ubuntu, I have no idea what to offer as a solution for you, but at least you can be certain that your Windows OS is still on the computer; if it were not, it would be impossible for Ubuntu to run as it is installed within Windows.

---

### Post by Mark Phelps on 2013-02-25
How is it that you are "stuck on Ubuntu"? When you install using Wubi, it only adds an entry for Ubuntu to the Windows boot men; it doesn't force you into Ubuntu by default.

Need to know what else you did to get there.

Also, need to know what version of Windows you are running -- XP? Vista? Win7? Win8?

---

