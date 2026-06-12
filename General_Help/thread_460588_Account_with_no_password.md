---
title: "Account with no password?"
date: 2007-05-31
forum: General Help
---

### Post by oiler920 on 2007-05-31
I realize this has been asked before, but the latest dated back to 2003 and the topic faded with no clear answer to the question. :( I am a noob on these forums, but I am an experienced Ubuntu user. If there is anyway to make an account with no pass, I'd like it. I have a 5-yr old who will never remember a 6-letter password, let alone type it in. Plus, I'd like to have a "guest" account on Ubuntu. I'm fine with using the Terminal. Any help would be appreciated. :)

---

### Post by hellmet on 2007-06-01
Not sure if this works on ubuntu
```

passwd -d <username>

```

This, on redhat, removes the requirement of a password for the <username>

---

### Post by jonallport on 2007-06-01
Nope, I can't get Ubuntu to accept a null password.  Best I can to is {space}

---

### Post by hellmet on 2007-06-01
You could do one thing.. You could add an auto login feature to the username you desire, if its going to be a single user system!

---

### Post by zvacet on 2007-06-01
For another account

```
sudo adduser <username>
```

**and go to the login window>security>automat login**

Let your new account be on automatic login but without admin privileges.That way your kid don´t have to write anything.

---

### Post by fanatik on 2007-06-01
take a look in /etc/pam.d/common-password - you should be able to modify some options there, to enable 0 length passwords... it's commented well.

you could try removing the nullok option and/or changing min= to 0.

Remeber this will apply systemwide, however!

HTH

---

### Post by oiler920 on 2007-06-01
> **hellmet said:**
> You could do one thing.. You could add an auto login feature to the username you desire, if its going to be a single user system!

Actually, this is a shared system, unfortunately. Only because I don't have enough money to get my own yet. And of course EVERYBODY wants their own account. So, kind of a prob.

---

### Post by oiler920 on 2007-06-01
Oh, and I tried the common-password thing...do you have to create accounts via terminal?

---

### Post by rillip on 2007-06-01
> **oiler920 said:**
> Oh, and I tried the common-password thing...do you have to create accounts via terminal?

Nope, there's a gui.  In KDE, go to System Settings -> Users and groups.  There's likely one in Gnome as well, but unsure of where.

---

### Post by oiler920 on 2007-06-02
I know there's a GUI! I was asking if I had to create them through the Terminal because the GUI is stubborn and wants to impose the 6-character pass no matter what. Anyway, I just decided to do an automatic login, since nobody who uses this comp. can remember a pass (unless it's their name :P). Thanks! :)

---

### Post by oiler920 on 2007-06-02
> **rillip said:**
> Nope, there's a gui.  In KDE, go to System Settings -> Users and groups.  There's likely one in Gnome as well, but unsure of where.

And that GUI happens to be a GNOME app.....(Ubuntu and Kubuntu use the GNOME app)..:lolflag:

---

### Post by kellemes on 2007-06-02
Possible to create a user without password?
Don't think so..

But this is really about making it easy for someone to login right?
Just create a normal useraccount and configure the loginmanager to enable Pasword-Less Login for this user.

For GDM you probably have to edit /etc/pam.d/gdm.

---

### Post by oiler920 on 2007-06-11
> Possible to create a user without password?
Don't think so..

But this is really about making it easy for someone to login right?
Just create a normal useraccount and configure the loginmanager to enable Pasword-Less Login for this user.
For GDM you probably have to edit /etc/pam.d/gdm.


That makes no sense. At first you say you can't do a passwordless user, and then you say you can? :-k

---

