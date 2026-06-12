---
title: "Cannot login after install"
date: 2005-10-25
forum: General Help
---

### Post by Michael Matthews on 2005-10-25
I have installed 5.10 twice. First time on dedicated machine, no problems. Second time as a third boot-able OS shared with XP and SUSE. My partitions and booting is OK but I cannot login to ubuntu. I do not remember getting prompted for root password during install but was mostly concerned about doing partitioning without destroying existing data and may have lost track. 

I can mount ubuntu root from suse and have tried editing /etc/shadow to remove passwd crypt. But nothing works.

Any ideas how I can fix?

TIA

---

### Post by az on 2005-10-25
So, the problem is that you forgot your password?  Your Ubuntu system only has one user.  You access the root account by running sudo, not by becomming root.

If you need to reset your user's password, boot into recovery mode and that will drop you to a prompt.

passwd (username) (new password)

and then 

init 2

---

