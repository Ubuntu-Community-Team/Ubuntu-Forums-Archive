---
title: "After reboot, no internet in Vista"
date: 2008-05-16
forum: General Help
---

### Post by dalert0140 on 2008-05-16
So I installed Wubi and Ubuntu and Ive been using it for a few days... still solving xorg issues, although i guess it could be worse. I like ubunt so far. Anyway, if i use ubuntu and reboot back into Vista I cannot get my comoputer to obtain an internet connection, if i go to the internet comand line i get something like DHCp server timed out. Anyone have any ideas?

---

### Post by ago on 2008-05-16
It's unlikely to be related to wubi/ubuntu

---

### Post by dalert0140 on 2008-05-16
No it's ubuntu related perhaps its not ubuntu's fault but it's related.It only happens after I reboot out of ubuntu and into vista.

---

### Post by ago on 2008-05-16
Do usual networking checks:

can you ping your router?
can you connect to your router http (gateway ip)?
can you renew your ip?

---

### Post by geoff123 on 2008-05-16
What happens if you unplug the network cable and power cable for a minute?

---

### Post by fmartinez on 2008-05-16
> **dalert0140 said:**
> No it's ubuntu related perhaps its not ubuntu's fault but it's related.It only happens after I reboot out of ubuntu and into vista.

How do you determine that it's ubuntu's fault? Is there a point when you are able to get internet access in Vista. 
Is the connection wireless or lan?
what type of network card are you using? 
In device manager (Vista) check the advanced config tab and disable the selections that allow the OS to control your network card. 
Then do a reboot and see what happens. 
I had similar problems on my Gigabit card.

---

