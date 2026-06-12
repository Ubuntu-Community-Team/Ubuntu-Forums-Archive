---
title: "Disable terminal + Locking down guest session for public use"
date: 2014-08-20
forum: General Help
---

### Post by jtjj222 on 2014-08-20
I am creating a public workstation, and I would like some information about locking down the guest session. 

I have found the Ubuntu wiki page about customizing the guest session, and  I have already modified the /etc/guest-session/skel to include standard sidebar and desktop shortcuts for the apps that will be needed in the guest session (firefox, nautilus and libreoffice).

In order to prevent the computers from being abused, I would like to disable the terminal. I tried setting the default shell for the user to /bin/false, however a new user is created each time, so I don't know how I would set it. Adding chsh /bin/false $USER to prefs.sh crashed the account before it would log in.

Are there any suggestions? Thank you!

---

### Post by nerdtron on 2014-08-20
Why would you like to disable the terminal? What particular changes are you restricting them? As long as the users don't have sudo access they can't change anything on the system, except for their personal settings of course.

---

### Post by jtjj222 on 2014-08-20
I don't want to give them the option.

For anyone stumbling across this, I figured it out. I am using usermod -s /bin/false in prefs.sh, and it works perfectly. Thank you.

---

