---
title: "Problems with avi"
date: 2005-07-27
forum: General Help
---

### Post by delirium on 2005-07-27
I followed the directions in ubuntuguild.org for installing Divx support and it works for my main account.  Now the problem is that when another account tries to play the same avi, totem splits out the error "Cannot open resource for writing" or something like that.

Can someone help?

---

### Post by diffuser78 on 2005-07-27
[QUOTE=delirium]I followed the directions in ubuntuguild.org for installing Divx support and it works for my main account.  Now the problem is that when another account tries to play the same avi, totem splits out the error "Cannot open resource for writing" or something like that.

Can someone help?[/QUOTE]

Try gxine

sudo apt-get install gxine

Hope this helps

Dan

---

### Post by hod139 on 2005-07-27
Make sure you have the groups configured correctly.  If you used the System->Administration->Users and Groups account editor, when creating a user make sure you use the Desktop profile in the advanced tab, not default.

Since the user already exists, you can use the tool to edit the user and click the User privileges tab, and check everything except 'Executing system administration tasks' (unless you want them to have sudo privileges)

Hope that helps

---

### Post by delirium on 2005-07-28
[QUOTE=hod139]Make sure you have the groups configured correctly.  If you used the System->Administration->Users and Groups account editor, when creating a user make sure you use the Desktop profile in the advanced tab, not default.

Since the user already exists, you can use the tool to edit the user and click the User privileges tab, and check everything except 'Executing system administration tasks' (unless you want them to have sudo privileges)

Hope that helps[/QUOTE]
 Thanks, that fix the problem.

---

