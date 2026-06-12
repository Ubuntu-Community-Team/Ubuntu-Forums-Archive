---
title: "New install, login, then can't authenticate"
date: 2014-09-13
forum: General Help
---

### Post by js0n2 on 2014-09-13
Today I did a fresh install of Lubuntu 14.04.1 on a 2008 MacBookPro on which I had formatted the entire drive. The install went smoothly and once it was compete I had no problem logging in with the username and password I created during the install process. I noticed immediately that there seemed to be a problem with my trackpad, and a quick search provided me with a solution to fix that, however it involved editing a file for which I needed to use sudo for to edit. Problem is that when I try to sudo, and enter my password, it isn't accepted. I then went into System Tools->Users and Groups to chnage my password, but you need to enter your password to do so, and my password isn't accepted there either. I tried logging out and had no problem logging back in with the password that isn't accepted for anything else. 

So I can use my password to login to Lubuntu, but after that the password doesn't work anywhere else. 

Not sure if it is important but my password does contain a * and an @.

I've done a bunch of googling and the closest I can find to my problem was this: [http://askubuntu.com/questions/176337/installed-perfectly-but-password-not-working-for-login-or-authentication](http://askubuntu.com/questions/176337/installed-perfectly-but-password-not-working-for-login-or-authentication)

however, that post doesn't have any solution for my particular situation. 

Really hope someone can help because a Linux system that I can't sudo on is a pretty sad (and useless) one. 

Thanks!

---

### Post by deadflowr on 2014-09-13
Did you 
A) find out if you belong to the sudo group using the command: groups.

and 

B) Did you try changing the password to a different one following the guide in that post
[http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password](http://askubuntu.com/questions/24006/how-do-i-reset-a-lost-administrative-password)

Maybe one without those two characters...
(Though I don't think those characters are any problem)

---

### Post by js0n2 on 2014-09-14
Hi, yes, I checked groups and I am in the sudo group. 

I also just followed the instructions to boot into recovery mode and changed my password to one with no special characters and I can now authenticate fine! Thank you for your advice!

Out of curiosity, any thoughts on what was going on? I guess I could test to see if it was the special characters, but am also wondering if it could have been something else. I've installed Linux quite a few times over the past decade and have never had this problem.

---

### Post by riph72 on 2014-10-03
I have this problem too, I think it's something to do with a "US" keyboard being selected when you log in (but on login screen it's "UK").  I've found I can get root access by searching for the US-version of my special char, but I can't seem able to select a UK keyboard, so haven't solved that part of the problem yet...

---

