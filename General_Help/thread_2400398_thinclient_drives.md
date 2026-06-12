---
title: "thinclient_drives"
date: 2018-09-05
forum: General Help
---

### Post by cmcanulty on 2018-09-05
several of the computers I administrate have a ?bug since upgrading to 18.04. A drive shows up mounted as thinclient_drives and when it does the home folder for the user is empty. Then I do sudo umount /home/librarian/thinclient_drives and it unmounts and goes away and then the home folder files are back. Upon reboot the same thing happens. I hope someone has an answer as it is time consuming

---

### Post by TheFu on 2018-09-05
What do the log files show?
Using **journalctl** is how I'd look at the boot looks.

I know notingabout thinclients ... unless you mean nfs mounting user home directories using autofs ... and I don't have 18.04 anywhere.

---

### Post by cmcanulty on 2018-09-05
it just shows as a mounted drive on the left of thunar or nautilus owned by root

---

### Post by TheFu on 2018-09-05
> **cmcanulty said:**
> it just shows as a mounted drive on the left of thunar or nautilus owned by root

Sorry. You lost me by using GUI programs and ignoring my log file suggestion.

Hopefully someone else will be able to help. Good luck.

---

### Post by cmcanulty on 2018-09-07
I did run journalctl but on a search for thinclients it showed no items

---

