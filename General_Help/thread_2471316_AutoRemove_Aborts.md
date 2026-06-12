---
title: "AutoRemove Aborts?"
date: 2022-01-26
forum: General Help
---

### Post by wyattwhiteeagle on 2022-01-26
UPDATE

I rebooted the system and tried Autoremove again.

AutoRemove completed successfully.

------------------------------------------------------------

I'm running Ubuntu 20.04 LTS fully installed on a 128gb usb flashdrive. (not a "live with persistance")

What could be causing "sudo apt autoremove -y" to abort?

Or am I not understanding it correctly?

> wyatt@wyatt-Aspire-E1-532:~$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libmessaging-menu0 libsbc1
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 201 kB disk space will be freed.
Do you want to continue? [Y/n] -y
Abort.
wyatt@wyatt-Aspire-E1-532:~$ 


---

### Post by rsteinmetz70112 on 2022-01-26
Did you try it without the -y?

---

### Post by ajgreeny on 2022-01-26
Great news! 

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to other users searching the forum.

---

### Post by wyattwhiteeagle on 2022-01-28
> **rsteinmetz70112 said:**
> Did you try it without the -y?

If you actually look at the quote in my post, you would see that I didn't use the '-y' when I typed in the Terminal.

The Terminal asked if I wanted to continue and that's where the '-y' comes in.

Anyway, rebooting the system and running "sudo apt autoremove" again had successfully completed.

This is now solved, as a system reboot worked for me.

---

### Post by KBar on 2022-01-28
rsteinmetz70112 was correct.

Like many well-written programs, **apt** aborts if a user types anything but *y* or *Y*. It will continue only when explicitly receiving these confirmation letters. *-y* is not such a letter, so it refused to carry on.

Indeed *-y* was a typo that made **apt** abort. However, simply correcting the typo by removing the leading hyphen should have sufficed. No reboot required.

---

