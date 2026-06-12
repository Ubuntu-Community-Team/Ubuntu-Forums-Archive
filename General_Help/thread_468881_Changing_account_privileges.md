---
title: "Changing account privileges"
date: 2007-06-09
forum: General Help
---

### Post by Heinrisch on 2007-06-09
I just got my ubuntu server up and running yesterday and everythign works as planned. The only problem that I have is that the first account I created was named "administrator" and I would like to change that name. Is it even possible? If not, I would like to create another account, was able to do that, and change its privileges to the same as my "administrator" account. I'm having trouble chaning the privileges of this new account, could anyone help me? I don't use a graphical interface.

Thanks in advance!

---

### Post by 444 on 2007-06-09
Look in /etc/group. For every group that administrator is a member of, add your user to the list as well.

---

### Post by taurus on 2007-06-09
Just add the second user to groups adm and admin in /etc/group.  That's all you need to be able to use sudo/gksudo.

---

### Post by Heinrisch on 2007-06-09
Thank you guys, now it works perfectly.

---

