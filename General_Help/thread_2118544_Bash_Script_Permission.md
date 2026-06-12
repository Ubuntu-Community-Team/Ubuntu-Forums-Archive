---
title: "Bash Script Permission"
date: 2013-02-21
forum: General Help
---

### Post by Quarkrad on 2013-02-21
Sorry - got to the stage where I cannot see the wood for the trees.  I've created a .sh script called gnomesuspend.sh and applied the following: **sudo chmod a+x /home/user/Documents/suspend/gnomesuspend.sh**.  I've also done **gksudo nautilus** and made sure the file is executable and the owner/group is the username.   I've created a desktop launcher using **gnome-desktop-item-edit ~/Desktop/ --create-new** where the Exec= line is ./ /home/user/Documents/suspend/gnomesuspend.sh    When I click on the desktop icon I'm told  **Details: Failed to execute child process "./" (Permission denied)**.  I **can** execute the file via the terminal by navigating to the relevant directory and typing ./gnomesuspend.sh.  Any help appreciated - head hurting.

---

### Post by prodigy_ on 2013-02-21
> **Quarkrad said:**
> ./ /home/user/Documents/suspend/gnomesuspend.sh
I think you should remove the "./" part.

---

### Post by Quarkrad on 2013-02-21
That did it - many thanks.

---

