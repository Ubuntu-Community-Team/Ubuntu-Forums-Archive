---
title: "Installed Pidgin 2 and sounds don't work"
date: 2007-05-31
forum: General Help
---

### Post by madelman on 2007-05-31
Hi:

I installed Pidgin 2.0.1 and no problems to communicate, but sound are not working and the only thing I can hear is the console beep. I checked in  /usr/share/sounds/pidgin and I can see all of them there and when I try to open them with movie player I can hear them without any problem then I go to Pidgin and setup preferences and  choose those sounds it keeps beeping with the console beep. 

Do you know how to setup these sounds?

---

### Post by madelman on 2007-05-31
never mind. I found the solution. 

You need to setup the Audio Method to Command then add : aplay %s

---

### Post by mijj on 2007-05-31
I was gonna say that!

<pouts at lost opportunity>

---

### Post by steveneddy on 2007-06-13
Thank you - it worked for me also.

---

### Post by KongKNoob on 2007-06-14
Another thanks from me!

---

### Post by starfleetcaptainrob on 2007-07-18
Yup.  Worked here as well.  Thanks.  I hate that beeping noise.

---

### Post by magikx21 on 2007-10-17
Glad I found this thread had the same problem solution worked. :)

---

### Post by Eviltelm on 2007-10-18
I just installed gutsy, did that but doesn't wort :(
any more tip? :P
thanks


EDIT: I was in 'do not disturb' mode :), it even works with the alsa now :)

---

