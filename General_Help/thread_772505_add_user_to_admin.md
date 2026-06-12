---
title: "add user to admin?"
date: 2008-04-28
forum: General Help
---

### Post by tparker on 2008-04-28
I need to add my user to admin so I can sudo as needed but can't get my system to do so. This is a fresh install of Hardy and my /home is on a network server. I can login to Hardy with my user name and my /home is there - but I do not have any admin rights so I cannot change anything, I can't even unlock stuff to change how my desktop looks, everything in both System>Preferences and System>Admin is grayed out once it's window opens. It says I don't even have permission to move back files I backed up from my local drive into my /home before the reinstall.

I used root at a command line and did usermod -G admin *username*, grepped afterward to check and it does show me as being in admin and users. Accessing /home from the server shows me in both user and admin as well. What did I miss?

---

