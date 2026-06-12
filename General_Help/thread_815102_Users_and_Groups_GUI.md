---
title: "Users and Groups GUI"
date: 2008-06-01
forum: General Help
---

### Post by Zill on 2008-06-01
Clean installation of Xubuntu 8.04 Hardy.

Users Settings GUI dialog is blank even after pressing "Unlock" button.

Groups Settings GUI dialog also remains blank and so cannot be edited.

New users can be added via the GUI but no home directory is created and they are not added to /etc/passwd or /etc/groups.  No users ever appear in GUI.

Live CD has same behaviour as installed version.

This *may* be a Policy Kit problem as I am also unable to change the Time and Date GUI to internet updates even though NTP is installed.

Has anyone seen these problems or should I raise bug reports?

---

### Post by lil_elvis2000 on 2008-06-26
I had the same problems. Exactly the same problems. I also have problems creating Samba shares in the GUI. It does nothing as well. Did you find the solution to this.

I've now gone to the command line. I'm used to that as I was previously on FreeBSD.

Now I wish I could trim Xfce even more!

---

### Post by Zill on 2008-06-26
lil_elvis2000:  No solution found yet so, like you, I have added new users via the adduser command.  I have discovered that, worryingly, using the GUI **deletes** most existing users and groups from /etc/passwd and etc/group.  I don't use MS Windows so can't comment on the Samba GUI.

I have raised bug report [240437]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/240437") to flag up this problem.  You will see that I have only experienced this problem with the AMD-K6 500MHz CPU.  Is your CPU the same?

I know that this is an ancient processor but Xubuntu *should* work correctly with old hardware :-|

---

### Post by chrisccoulson on 2008-06-26
Zill, I commented on your bug report. Could you attach the information I requested to the bug report?

---

### Post by Zill on 2008-06-27
> **chrisccoulson said:**
> Zill, I commented on your bug report. Could you attach the information I requested to the bug report?
Requested info added to bug report.  Thanks for your help.

---

### Post by lil_elvis2000 on 2008-07-02
The only thing that seemed to work is a reboot.

---

### Post by Zill on 2008-07-02
lil_elvis2000:  Looks like we have different problems.  In my case, some data is permanently deleted from /etc/passwd and /etc/group after using the GUI. A reboot does not cure this.

Glad you found a fix for your problem.

---

