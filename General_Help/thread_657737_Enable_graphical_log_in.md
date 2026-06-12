---
title: "Enable graphical log in"
date: 2008-01-03
forum: General Help
---

### Post by xbob on 2008-01-03
I am new to Ubuntu, and i was disabling some thing that i thought i didnt need. 

Well, i disabled the graphical login mode and now I am in the command prompt. Where i see "username@computername". Can someone please tell me how to enable it?

---

### Post by reckless2k2 on 2008-01-03
i think you need to do this:

```
sudo chmod +x /etc/init.d/gdm
```

reboot and then you should be alright. 

ALSO...you should be able to just run this at that command prompt to get back to graphically:

```
startx
```

let me know how it goes unless you tweaked up your X server then we will have to do something different.

---

### Post by xbob on 2008-01-04
I typed in startx at the commend prompt and it works, thanks.

---

### Post by reckless2k2 on 2008-01-04
you just need to re-enable your gdm or kdm depending on if you're using ubuntu or kubuntu then. i gave you the code to re-enable you gdm.

gdm and kdm are just the login screens.

---

