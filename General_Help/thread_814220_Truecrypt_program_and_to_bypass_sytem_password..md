---
title: "Truecrypt program and to bypass sytem password."
date: 2008-05-31
forum: General Help
---

### Post by esteckis on 2008-05-31
Hello everyone. I am using Truecrypt. Now when I click on the Truecrypt icon, the system asks for my system password before I can enter the Truecrypt password to open the encrypted file. Since this appears to be a bothersome duplication, is there a way that I can have the system let me run Truecrypt without the system asking me for the system password everytime.  When I run Truecrypt, I just want to enter the Truecrypt password.

OK, I right clicked on the icon to look at properties, it states that the owner is root, group is root, others is read only.  How do I change the permissions so that when I am logged in, I can run the program without being asked for the root password?

---

### Post by itaintover on 2008-05-31
Maybe this helps? 
Ubuntu Tricks - 4 ways to run Root privileged processes without a password.

---

### Post by esteckis on 2008-05-31
I guess this will help with any future programs (I guess)

1) I logged out and signed in as root, then I right clicked the icon and picked properties. I changed permissions to allow read and write for all.  I hope I am not compromising my system.

I tried the sudo su in terminal and it still would not let me change permissions. But doing the 1 above worked. I also did not want to the 2nd option of running root while I am signed in.

---

### Post by niteshifter on 2008-05-31
Hi,

See this [link]("http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10") for how to set up truecrypt without needing sudo every time.

It describes setting up a an GUI application (tcgui) for the non-GUI version(s) of truecrypt on the first page. Since you're using the GUI version of truecrypt you can skip that part. [Page 2]("http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10-p2") is where you need to begin. You need to do the parts labeled:

3.2.1 Users & Groups (about adding a truecrypt group and you to that group)
3.2.2 Sudo (editing the sudoers file)

Logout and back in and try truecrypt, it should not ask you for your user password. If it does do the section "3.2.3  Truecrypt Group", then you should be good to go. Note that version 5.3a of truecrypt (the GUI version) is different with respect to the command line, so skip the "truecrypt -l" test given in section 3.2.3 - I'm not sure that will work with TC 5.3a.

---

### Post by chrisccoulson on 2008-05-31
itaintover: Please have a look at [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=765414")

---

### Post by itaintover on 2008-05-31
> **chrisccoulson said:**
> itaintover: Please have a look at [Forum policy on log-in-as-root tutorials]("http://ubuntuforums.org/showthread.php?t=765414")
Thanks for bringing that into my attention. I didn't know about that policy.

---

### Post by esteckis on 2008-05-31
Thanks for the links. In reference to running in root. I am not doing it permanently. I was just changing the permission to Truecrypt so I could run it when I am logged in normally without not being in root.

One question I have is, all I did was when I was in root was to assign read and write permissions for using that program, when I am normally logged in. Would that have been the same as creating a user group?

---

