---
title: "Skype not logged in"
date: 2014-04-11
forum: General Help
---

### Post by raisen on 2014-04-11
I am not being able to login on Skype under Ubuntu 13.10. The spinning wheel just spins but it never goes to the next screen.

I tried to run Skype from the terminal and when I click on the Sign In button, I saw a couple of those errors:

Failed to create secure directory (/run/user/1000/pulse): Permission denied

I'm not sure if it's related to Skype though.

---

### Post by raisen on 2014-04-11
The problem was with pulseaudio. The folder mentioned above was owned by root instead of a regular account. I'm not sure how that happened, but I changed the permission and Skype is working now.

---

