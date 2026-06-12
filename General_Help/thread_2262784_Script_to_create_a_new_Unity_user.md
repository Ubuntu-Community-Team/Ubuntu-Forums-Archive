---
title: "Script to create a new Unity user"
date: 2015-01-27
forum: General Help
---

### Post by Romu on 2015-01-27
Hi,
I'm looking for a way to create a new user account, able to connect to Unity, with a bash script. Ideally, this new user should not have any password, but I don't know if this is doable.

I've tried this, but doesn't work:

```
sudo useradd -d /home/toto toto
sudo passwd toto -d
```

Then, I see "toto" in the list of users in the login screen. When I click on it (or through the "users" settings applet), I see there is no password. But if I click "Log In", I get a black screen and get back to the login screen. 

Any idea?

---

### Post by Romu on 2015-01-27
Found the fix. It didn't work because the home folder was not created. The good, working, code is:

> 
sudo useradd -m -d /home/toto toto
sudo passwd toto -d

Enjoy!

---

