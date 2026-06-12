---
title: "sudo su"
date: 2006-08-20
forum: General Help
---

### Post by compwiz18 on 2006-08-20
Not sure if this is the right place, but...

I was wondering: what is the point of setting the root password different then your account password if anyone can just do **sudo su** and be the superuser just like that?

---

### Post by RudolfMDLT on 2006-08-20
I'm sort of new to linux, but, even though you are logged in, don't you get asked for the superuser password when you sudo anything?

---

### Post by taurus on 2006-08-20
Just so you know.  The only people can run the sudo command are those that belong to groups adm & admin in /etc/group.  Therefore, if you don't belong to those two group, you CAN'T use sudo...  End of story.

---

### Post by meng on 2006-08-20
> **RudolfMDLT said:**
> I'm sort of new to linux, but, even though you are logged in, don't you get asked for the superuser password when you sudo anything?
Assuming you are authorized to sudo, the password required is your user password. Several users make the mistake of trying to enter a different password at this prompt - perhaps because of migrating from other distros.

---

### Post by RudolfMDLT on 2006-08-20
> **meng said:**
> Assuming you are authorized to sudo, the password required is your user password. Several users make the mistake of trying to enter a different password at this prompt - perhaps because of migrating from other distros.

O! wel my Sudo password and user password are the same so I wouldn't have spotted that!	:redface:

Thnx meng

---

### Post by compwiz18 on 2006-08-20
> **taurus said:**
> Just so you know.  The only people can run the sudo command are those that belong to groups adm & admin in /etc/group.  Therefore, if you don't belong to those two group, you CAN'T use sudo...  End of story.
That answers my question.  Thank you.

---

### Post by yatt on 2006-08-20
> **compwiz18 said:**
> Not sure if this is the right place, but...

I was wondering: what is the point of setting the root password different then your account password if anyone can just do **sudo su** and be the superuser just like that?

You can also "sudo -s -H" and get the same effect.

---

