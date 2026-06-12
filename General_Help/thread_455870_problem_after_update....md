---
title: "problem after update..."
date: 2007-05-27
forum: General Help
---

### Post by inub on 2007-05-27
hey there,
    i am using drapper and yesterday i updated for the first time as it showed that it had more then 200 updates listed up. Now after the update, now my pc wont do anything after i log in. The mouse is there and the background it there but there is no loading and it remains that way...
    I was about to format my pc coz i dont any windoze anymore to go for emergencies. But something caught my attention about a failsafe login. Now i have managed to log in but nautilus doesnt work and everything is so big. But i am happy that firefox worked and i was able to reach here and post this coz now someone will help me.

---

### Post by mbradlcu on 2007-05-27
I would start with trying to correct you're screen resolution, try:
```
sudo dpkg-reconfigure xserver
```

---

### Post by inub on 2007-05-27
thanks alot mbradlcu...
your answer did allow me to correct my problem.I am complete noob. So here is what happened. When i pasted the code given by you in the terminal it gave a error saying that xserver is not installed...i thought i should install it and opened synaptic and it gave another error sign that dpkg is not correctly installed and i should use the code sudo dpkg --confifure -a to correct it
i did that and it took some time and voila my problem is solved. 
phew that was a close one as i came close to formatting and losing everything
thanks again

---

