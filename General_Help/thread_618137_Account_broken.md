---
title: "Account broken"
date: 2007-11-20
forum: General Help
---

### Post by jixor on 2007-11-20
I originally had one account called "user". I just created a new account called "local" and changed the "root" account's password. Now I can't log into the "user" account with its password or the password of the new local account (in case somehow something strange happened there when I tried to change the root password) and I can't seem to sudo root with "local". In "local" I also can't access the users and groups management app.

So I'm stuck with this half functional "local" account and can't seem to find any way of logging into "user", not that I ever actually made any changes at all to the "user" account, it just stopped working. I could possibly narrow it down that I clicked where it says "local" in the panel bar and in the drop down hit "user", I was expecting a password box maybe? However after I did that it crashed (just a plain brown screen) and haven't been able to login as "user" since, but I can't be sure if thats where it went messed up or not.

---

### Post by banewman on 2007-11-20
In a terminal type - 
sudo usermod -p user
where user is the login name 
that will let you check the password for the user - assuming you have the rights to do that...

---

### Post by jixor on 2007-11-20
I just get prompted "[sudo] password for local:" and when I enter it I just get the prompt, nothing returned. Also when I try to sudo for root access (ie try to load "gksu users-admin") after intering the root password I get "The underlying authorization mechanism (sudo) does not allow you to run this program..."

---

### Post by jixor on 2007-11-20
If it helps I keep getting this problem too, maybe its related (see screenshot)

---

