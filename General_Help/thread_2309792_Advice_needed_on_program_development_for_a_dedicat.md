---
title: "Advice needed on program development for a dedicated system"
date: 2016-01-13
forum: General Help
---

### Post by arunb on 2016-01-13
Hi,

I am trying to design a program that will be run on a dedicated computer having lubuntu OS. Ideally only this program (or several associated programs) will be run on the computer which is a kiosk type PC. The system would be used by people who have very little knowledge of computers, and linux.

Is it better to 

1. design one program that handles all the tasks, same program would also be used to configure system settings like, network setup, printers etc. This makes the system simple and easy to use, as users are restricted to just one screen, but I would have to add extra program features for basic tasks like network setup, printer setup etc. Teh system would be like a kiosk PC found in airports...However some method of system recovery or backup would have to be provided.

2. Remove all non-essential programs from the lubuntu installation, then break up the program into several components, user accessible components are available from the system menu or the desktop like any other application. Important tasks would be run in the background, system tools like network configuration, printers etc will be available from the system tools menu of lubuntu. However The computer would have to be locked (using software) to prevent users from installing non-essential stuff, also some means to prevent USB data transfers would also be required.

This approach would use the existing software features available in lubuntu, which is an advantage as the OS is well documented and is easy to learn. 

Backup and recovery should be easy as the system is like any other lubuntu installation, but with some special programs.

I was hoping if anyone could point out the best approach and the advantages.


thanks
a

---

### Post by bobk48 on 2016-01-13
a.:
Do you want to run 1) a "turnkey" system under Ubuntu, or 2) a program that is Ubuntu? In other words, 1) the turnkey system appears to the user like some application that doesn't allow access to actual Ubuntu at all, or 2) an Ubuntu "look-alike'  that is a shell running on top of Ubuntu and gives a very minimal set of access privileges to the user. If you can clarify that top level design specification a bit more, that would help.
b.

---

### Post by arunb on 2016-01-13
I prefer the second solution, in this case most of the applications would be removed from the installation, and allow minimal access to the system. The first solution seems exhaustive.

I have attached screenshot of the desktop, the panel on the left contains the applications to be used by the user, while the panel on the right shows the system based tools like network configuration, printer setup, internet browser etc.

thanks for the reply

---

