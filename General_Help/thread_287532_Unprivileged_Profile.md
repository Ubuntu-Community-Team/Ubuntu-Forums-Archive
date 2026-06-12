---
title: "Unprivileged Profile"
date: 2006-10-28
forum: General Help
---

### Post by rhy7s on 2006-10-28
Is there more to the unprivileged user profile than just unchecking all the boxes in User Privileges? If not, would this level of access be appropriate for a kiosk or guest user?

An option to create a mandatory or locked profile via the GUI would be grand,  a check box to toggle that state maybe even better.

Any thoughts on the topic?

---

### Post by benpage26 on 2008-02-27
I would also like to know the answer to this question

---

### Post by aysiu on 2008-02-27
I don't even know what the question is.

Unprivileges users can change anything in their /home/*username* directory and anything in /tmp, but they cannot make other system-wide changes. They cannot access most of the items under System > Administration, including use of the package manager to install or update programs.

If that's not enough for you, look into Pessulus or Kiosktool.

---

### Post by benpage26 on 2008-02-27
Thanks aysiu

Can they use the sudo command to become 'privileged' because when i tested, using sudo asked for the password and ran the command, this may have been because the command didn't require sudo (i'm not sure if it did, i didn't want to try anything 'silly')

I would have expected sudo to say "You are not admin" if the user wasn't allowed to use sudo.

---

### Post by aysiu on 2008-02-27
> **benpage26 said:**
> Thanks aysiu

Can they use the sudo command to become 'privileged' because when i tested, using sudo asked for the password and ran the command, this may have been because the command didn't require sudo (i'm not sure if it did, i didn't want to try anything 'silly')

I would have expected sudo to say "You are not admin" if the user wasn't allowed to use sudo.
If the *Administer the System* box is unticked, then the user should not be able to successfully execute *sudo* or *gksudo* commands. It should just skip to the next line. See the attached screenshots for more details.

---

### Post by benpage26 on 2008-03-02
Thanks alot for explaining that!!
Ben

---

