---
title: "Lubuntu 19.04 - New User added fails at login"
date: 2019-08-09
forum: General Help
---

### Post by GhX6GZMB on 2019-08-09
Dear All:

I have a Lubuntu 19.04 install that works perfectly, and added a new user.

I did this using the "Preferences - LXQt Settings - Users and Groups"

User is created, Group as well. Both have the same name with UID 1001 and GID 1002, and connections between both are established.

After a reboot, I can now choose between my old account and the new user.

Problem is that the new user account doesn't accept my login. When logging in, I get "Login Failed". My existing account works perfectly on login.

Where did I go wrong? Is there some update command that I've missed?

---

### Post by guiverc on 2019-08-09
From your description I can see nothing wrong.

I booted a Lubuntu 19.04 (x86) system logged in, `sudo apt update; sudo apt full-upgrade`; then created a new user 'testing' which had the UID 1001 and GID 1002 as you had. I logged out and could login as 'testing'  (my only disappointment was the new user had `sh` ans shell instead of my preferred bash).   I rebooted and could login to 'testing', and other than needing two attempts to login (due to wrong password being typed) I had no issues.

If you switch to terminal (eg. ctrl+alt+F4), can you login to your second account that way?  ie. currently I'm wondering if you are trying with the wrong password, though your architecture is almost certainly x86_64 so I could try it there too...  

I doubt it's related to an update command you've missed; but if you `sudo apt update` do you see a number of hit's, for example on this [different] x86_64 box I see the following  (excerpt only)
```
Hit:3 http://ftp.iinet.net.au/pub/ubuntu eoan-updates InRelease                                                               
Hit:4 http://ftp.iinet.net.au/pub/ubuntu eoan-security InRelease 

```
followed by the message
```
All packages are you to date.
```
please note: that was copy/pasted from the box I'm replying to so shows 19.10 not 19.04 entries, and your mirror will no doubt be different to mine

---

### Post by GhX6GZMB on 2019-08-10
@guiverc, Thank You.
I worked it out, it was a user:group permissions problem, a chown command solved it.
I now have a perfect clone of my main account.

Concerning your sh vs. bash issue:

Go to "Preferences - LXQt Settings - Users and Groups", select the User and go to "Advanced". Here you can select bash.

Cheers.

---

