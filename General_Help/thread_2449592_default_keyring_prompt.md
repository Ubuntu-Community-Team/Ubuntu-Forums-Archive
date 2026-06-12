---
title: "default keyring prompt"
date: 2020-08-30
forum: General Help
---

### Post by gertrude58 on 2020-08-30
Lately I keep getting the popup An application wants access to the default keyring when i login. I enter my login password which is not accepted,but nothing else happens,I just cancel the popup and carry on.So I decided to change my login password ,went to users-passwords and updated my login password.I read in the help section that the updated password would also be the same as the default keyring,so all  should be ok again. But I am still getting the popup.So I took a look at Passwords and Keys in settings.Default Keyring is locked and my login password wont open it.Login is open but it is saying This collection appears to be empty!  I dont know how to get rid of the popup or find out what password it wants.Please help!

---

### Post by dino99 on 2020-08-30
The first step i should propose: clean the system, via autoclean/autoremove or better via bleachbit (as root, carefully opt in  options).
The second will check error(s) (red line) and warning(s) (yellow line) from 'journalctl -b' output

---

### Post by gertrude58 on 2020-09-07
Sorry,i don't really understand how to do any of the things you advise! Thanks anyway..

---

### Post by CelticWarrior on 2020-09-07
All the above is easy to google but I don't think it helps.

NOT using auto-login surely will.

---

### Post by gertrude58 on 2020-11-08
So by changing settings to login by password instead of auto-login,this will solve the problem?

Sorry if I sound a bit dim!

---

### Post by CelticWarrior on 2020-11-08
Hopefully yes, it will.

Logging in with a password unlocks the keyring. Auto-login doesn't. So, when you needs to connect to WiFi and/or any app requests access to the stored passwords it'll ask for the password anyway.

And regardless of the above using passwords is a good practice. Not using them is a bad habit acquired by having been dumb down by old Windows versions. Microsoft adopted the same security model (+/-) years ago.

---

### Post by gertrude58 on 2020-11-09
Doesn't seem to work,I changed to logging in with a password but still get asked to unlock the keyring several times . Latest thing,I get "Access Prompt"is not responding popup and I have to force quit it. Not sure what to do next!

---

### Post by CelticWarrior on 2020-11-09
Dumb question: Have you rebooted or at least logged out and in again?
If so, please provide a screenshot of those pop-ups.

---

### Post by gertrude58 on 2020-11-11
Not such a dumb question!I had logged in and out but not rebooted. So I rebooted and so far no pop-ups. Hopefully that was the solution. Thanks a lot!

---

