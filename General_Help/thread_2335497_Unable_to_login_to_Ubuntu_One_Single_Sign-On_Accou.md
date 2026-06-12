---
title: "Unable to login to Ubuntu One Single Sign-On Account to install Snaps"
date: 2016-08-29
forum: General Help
---

### Post by fidelis1 on 2016-08-29
Hello,

I seem to be unable to login to my Ubuntu One Single Sign-On Account to install Snaps. I keep getting "Incorrect email or password" even though I know for a fact they are correct. I have no problem signing in from a web browser. I have tried changing the password. Any help would be greatly appreciated.

Thanks,
fidelis1

Edit: I was able to login and install the keepassx snap via the terminal. So  this only happens when I try to login and install snaps via the software  app.

---

### Post by coldgrid on 2016-09-24
I have same problem .

---

### Post by kirk_grem on 2016-09-29
I have this same problem.  Discovered it trying to install VLC.  What's the deal?

---

### Post by Jan_Johansson on 2016-10-11
I'm having the same issue on Ubuntu 16.04 Gnome - No problem signing in via webbrowser or I would not be able to write this! Most likely an issue with the software app, but developers rarely look here so try to find the git and if you do then post a link here.

---

### Post by howefield on 2016-10-11
This looks like a relevant bug report.

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943)

---

### Post by Jan_Johansson on 2016-10-11
> **howefield said:**
> This looks like a relevant bug report.

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943)

Howefield, you beat me to the punch:) That is the correct page.

I just wrote on that page to the developers that they ought to inform people of this bug, and this thread would be an idea to use:)

JBJ

---

### Post by diegogermangonzalez on 2016-10-11
install from the terminal
**sudo snap install vlc**
Update 
**sudo snap refresh vlc**
remove
**sudo snap remove vlc**

---

### Post by landennick on 2016-11-29
Same problem  **twice** .

before and after clean install on the same laptop

---

### Post by howefield on 2016-11-29
Thread closed to the army of me-tooers.

---

