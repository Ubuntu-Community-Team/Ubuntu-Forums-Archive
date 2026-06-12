---
title: "Wierd Kubuntu problem (KDM, X.org failure?)"
date: 2007-05-23
forum: General Help
---

### Post by apakatt on 2007-05-23
My Kubuntu-system has suddenly stopped working. When I boot my computer it works fine and I get to the graphical login-manager KDM (and it shows this on my monitors with correct resolution) without any errors. 

The problem is when I try to sign in it just falls back to KDM again. If i try to start X from console it just falls back to the console. What bothers me is that I have not changed any hardware, installed any software or automatic updates (that i can remember) or made any changes in my x.org (or such) which has worked for years and what I can tell there is no big error in the x.org log either.

X.org log: [http://paste.ubuntu-nl.org/21988/](http://paste.ubuntu-nl.org/21988/)
X.org config (should be ok): [http://paste.ubuntu-nl.org/21989/](http://paste.ubuntu-nl.org/21989/)

---

### Post by Bordy on 2007-05-23
So, I have no idea why this worked for me, or if it will work for you, but I was having roughly the same issue with my xubuntu install.

Somehow a fsck worked.

Worth a shot?

---

### Post by apakatt on 2007-05-23
Problem solved!
I used SSH to access my computer and used df -h to check if my external harddrive was pluged-in and I noticed that my /home-partition was 100% full. I deleted some files and now it works again.

Wierd problem with no error-messages but luckily for me i stumbled upon the solution! :)

---

