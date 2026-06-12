---
title: "Cant Install Programs"
date: 2007-05-12
forum: General Help
---

### Post by PapaDragon on 2007-05-12
I just installed Ubuntu 7.04 and everything sames cool but I don't have some of the basic options that I should. Under Applications I don't have the Add/Remove Programs option and I can't add it using the System->Preferences->Main Menu. There are several things in the Main Menu GUI that are in italics and will not let me add them. I manually added an option to my application drop down that points to /usr/bin/gnome-app-install but when I try to install something using this I get the error below. I put in the Admin pass word and everything appears ok until i get this. Please help.

Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '50331651' '--set-selections-file' '/tmp/tmp7tosYR' as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

---

### Post by phidia on 2007-05-12
Did you have a different user when you installed ubuntu? I ask because I think ubuntu only allows the 1st user admin privledges.

---

### Post by PapaDragon on 2007-05-13
I don't think so, but when I installed ubuntu it pulled up my windows users and made them users then I got to another screen that create another account and set the name of my computer. Maybe I need that user signed in. How can I see a list of all users including admin from a non-admin account?

---

### Post by PapaDragon on 2007-05-13
I got it! I didn't realize that I sought up two accounts. when I switch to the other user I guess that was the admin account because it unlocked all the options.

---

### Post by zvacet on 2007-05-13
For future maybe go to the **system>administration>users&groups**

---

