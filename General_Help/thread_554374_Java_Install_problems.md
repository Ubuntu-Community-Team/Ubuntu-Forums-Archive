---
title: "Java Install problems"
date: 2007-09-18
forum: General Help
---

### Post by RetroDemon on 2007-09-18
I was installing Java and it got to the first blue screen where you press <ok> and something happend and i couldnt go further. Now when i start the process over i get this message in the terminal: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


i dont know what the dpkg thing is.

---

### Post by sumguy231 on 2007-09-18
Paste this into a terminal and run it:
```
sudo dpkg --configure -a
```

---

### Post by RetroDemon on 2007-09-18
lol, im sorry for these nubish questions, i havent used linux since the mid 90's so im starting new again.

---

### Post by RetroDemon on 2007-09-18
ok, now im at the configuring screen (the blue scree) and i read the liscence agreement, and theres <ok> and when i hit enter nothing happens

---

### Post by RetroDemon on 2007-09-18
anything, cuz any button i hit isnt working, and its not frozen, cuz the liscence agreement is still scrolling when i go to scroll it.

---

### Post by RetroDemon on 2007-09-18
ok, so i got the blip there was a new thing to install and now i get this message when i go to install it. 
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by sumguy231 on 2007-09-19
You needed to press 'tab' before hitting OK. I missed that too before. Anways, as predicted you now need to run
```
sudo apt-get install -f
```
In a terminal to straighten things out.

---

