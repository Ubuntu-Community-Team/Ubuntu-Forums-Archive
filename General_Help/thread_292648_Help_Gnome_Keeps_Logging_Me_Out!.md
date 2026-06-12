---
title: "Help Gnome Keeps Logging Me Out!"
date: 2006-11-04
forum: General Help
---

### Post by Sheepish on 2006-11-04
Hi all, im desparate now, iv tried everything to fix it but to no prevail. When i log into my gnome session (or indeed any session) it logins in and plays the sound, but then it logs out again, sometimes i have to type in my user and password 10 times for it to actually log in!
i didnt do anything for it to do this, it just happened when i turned on the computer.

thanks in advance

---

### Post by philippe_carlo on 2006-11-04
Does it say anything? I once had a similar thing going on because some file in my home directory (.xsession or something) had wrong permissions. Try issuing the following command from a text console (replacing user with your login):
```

sudo chown -R user:user ~

```

---

### Post by Sheepish on 2006-11-04
No, it just flashes a black screen with a cursor (like an underscore) like it used to do in ms dos (btw i dont have and microsoft anything) then it loggs me out nd presents my with the login page. the command you asked me to used just asked me for the root password and then went onto a black line :-?

---

