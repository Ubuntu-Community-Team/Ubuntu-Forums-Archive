---
title: "Permissions Hell"
date: 2007-08-11
forum: General Help
---

### Post by Ozdemon on 2007-08-11
I have installed 7.04 on 2 PC for my kids.  I created user accounts for each child with restricted privileges.  Now if during one of their sessions I need to install something, I can't.  A graphical window will pop up asking for the password.  If I use their password - no go, which is as it should be.  If I use my password, still no go.

So I used terminal to create a root password that was the same as my password.  Still no go - by that I mean password rejected.

Can anyone tell me how to install something while running a restricted account?  Or any way of installing that will **apply **to the restricted account?  :confused:

---

### Post by hanzomon4 on 2007-08-11
Open a terminal and type "su {your username}" like "su hanzomon4". It will ask for your password after that you can use sudo from the terminal, I don't believe gksudo will work for gui apps though so use apt-get instead of synaptic

---

### Post by Ozdemon on 2007-08-11
Tks for the reply.  I will try.

But I am a little surprised if there is no way for an admin to install using a GUI while logged in to a restricted account.  Maybe there is a good reason?

---

### Post by hanzomon4 on 2007-08-13
Yeah that's why you have restricted accounts, Wait...

by Restricted I mean not able to use sudo, A regular users can use sudo, and the super user doesn't need sudo because the superuser rules all. The default user has access to sudo. You need root access(sudo) to install things because the install process puts files in restricted areas like /bin /usr/ and such.

---

