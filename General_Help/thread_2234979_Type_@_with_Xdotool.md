---
title: "Type @ with Xdotool"
date: 2014-07-18
forum: General Help
---

### Post by CkDGTAT on 2014-07-18
Hi,

Anybody found a solution to type email adress with xdotool

```
xdotool type "myemail@adress.com
```

gives

```
myemailadress.com
```

---

### Post by billdozor on 2014-07-18
I could not reproduce your issue with xdotool and double quotes.

Have you tried literal single quotes? As in:
xdotool 'myemail@address.com'

An alternative is to send the shift+2 key press as in:
xdotool type "myemail"
xdotool key "shift+2"
xdotool type "address.com"

---

### Post by grumblebum2 on 2014-07-19
Works fine here.
Font???

---

### Post by CkDGTAT on 2014-07-22
I set a delay between keystroke to solve my problem

---

