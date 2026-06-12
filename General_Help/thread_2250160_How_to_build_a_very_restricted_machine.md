---
title: "How to build a very restricted machine ?"
date: 2014-10-27
forum: General Help
---

### Post by Spear on 2014-10-27
Hi, we're still running a few Windows XP computers, and as I said to the boss, I'll dismantle these at the end of the year. But I won't get moneyto have all these replaced. Hopefully, I can use these as some kind of " thin clients ".

To make it simple : I want a computer that starts running Ubuntu, when the user is connected, he can start a RDP session to our TSE servers, or surf the internet (and eventually print), that's ALL.

Is there any application that helps to build that kind of setup very easily by only allowing those two apps to be started by a simple user (and hiding the rest) ?

Thanks in advance

---

### Post by mastablasta on 2014-10-27
kiosk mode?

Webconverger is debian based project for kiosks.

or you can setup ubuntu and lock it down

---

### Post by nerdtron on 2014-10-27
Create a normal user account.
Uninstall all apps on the computer except those you need. Then they won't be able to install anything since they don't have admin privileges. They will just use the programs installed.

---

