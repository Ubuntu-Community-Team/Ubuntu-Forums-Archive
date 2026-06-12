---
title: "Help! Linux running really slow!"
date: 2007-09-19
forum: General Help
---

### Post by kdarkentity on 2007-09-19
My Ubuntu 7.04 system is crawling right now... earlier today it was running smoothly for the most part.

All i did today was install some applications, installed and played with screenlets and not much else.

Beryl is the window manager i use and it crashed and restarted itself at least 15 times in the last hour...

So what i'm asking is how can i diagnose why all of a sudden my machine went from running well to running poorly all in a day?

---

### Post by rsambuca on 2007-09-20
> All i did today was install some applications, installed and played with screenlets and not much else.
Obviously something happened here.  Perhaps if you actually list what programs you installed, and what settings you changed, then perhaps we might be able to help.  We are not mind readers!

---

### Post by kdarkentity on 2007-09-20
well heres the thing.. i installed about 50 programs yesterday just because, and now i removed all of them and its still crawling... soo i think the problem might have something to do with screenlets. if its not this than i have no idea whats wrong either

---

### Post by rsambuca on 2007-09-20
Did you remove all of the dependencies as well?

---

### Post by kdarkentity on 2007-09-20
im not sure, how can i check? ...all i did was install the apps and remove them using add or remove programs

---

### Post by rsambuca on 2007-09-20
You can open a terminal and enter```
sudo apt-get autoclean
```.  Also, I am sure you tested this, but have you disabled the screenlets to see if the problem goes away?

---

### Post by kdarkentity on 2007-09-20
ok thanks ill try that... and i dont think screenlets are running... especially cause im forced to use metacity as my window theme... but still i think the problem started after i started using screenlets... ill get back to you after ive done this.

---

### Post by kdarkentity on 2007-09-20
ehh w/e man thanks for the help.. but i decided to just o a reinstall

---

