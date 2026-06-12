---
title: "Fire Fox Crashing"
date: 2007-05-01
forum: General Help
---

### Post by jayneella on 2007-05-01
Hello,

Im currently running Ubuntu Edgy on Linux, i have a thinkpad T42 lap top and every time i go to my online banking to [www.lloydstsb.com](www.lloydstsb.com) I lose FF and it crashes,, any ideas anyone???

Thanks

---

### Post by phidia on 2007-05-01
If you open ff from the terminal and leave terminal open when ff crashes there should be some output that may help sort out why that's happening. There might also be something in /var/log.

---

### Post by jayneella on 2007-05-01
Hello, can you tell me how to do that in terminal? like what do i type, (command)?

Thanks

---

### Post by Turellius on 2007-05-01
You should be able to just type "firefox".  If that doesn't work then try 
```
cd /usr/bin
```
```
./firefox
```

---

### Post by jayneella on 2007-05-01
Hello i tried that and all it did was bring up a new ff window

---

### Post by jayneella on 2007-05-01
Checked terminal and it isn't saying anything new when FF crashes, i have had this before and had to set up a new default setting in ubuntu but now i cant remember how i did it?

---

### Post by phidia on 2007-05-01
You mean the terminal you opened ff from doesn't have any output when firefox crashes? You need to leave the terminal window open after opening ff from it and then try going to the site that ff crashes when trying to load.
There should be something.

---

