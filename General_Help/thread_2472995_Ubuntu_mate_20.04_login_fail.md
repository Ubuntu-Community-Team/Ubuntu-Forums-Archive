---
title: "Ubuntu mate 20.04 login fail"
date: 2022-03-20
forum: General Help
---

### Post by bobsone on 2022-03-20
Hi
I have a desktop running Mate 20.04. It is an AMD system with 2 nvme M.2s, 2 SSDs, a 3700x, x570 board, 2 screens and a new rtx3050.
I have just installed the 3050, at first boot I had black screens, 2 resets later I had the login screen with user defined background on both screens.
The problem is that I cant login, I can type either users password and then enter, the computer acts as if it is logging in (it removes the login background) but then reverts to the login screen.  
I have tried an incorrect login password and it rejects the attempt with "Invalid password, please try again" so it appears that part is working.

Any help appreciated

---

### Post by bobsone on 2022-03-20
Update.

The grub version is 2.04, 
I tried the recovery mode screen and found that the current version (linux 5.13.0-35-generic) just went to the login page as expected.
The earlier version (linux 5.13.0-30-generic) login worked (with those huge icons) so I created a new user and restarted. Unfortunately although the new user is now on the login screen, all login attempts result in the same login loop.
The old GPU (a 750ti) has the same login loop issue now.

---

### Post by bobsone on 2022-03-20
This desktop is needed in the morning so I have refitted the old gpu and rolled back the os with timeshift...

---

