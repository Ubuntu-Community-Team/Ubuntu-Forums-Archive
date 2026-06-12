---
title: "rt2570 and aircrack-ng not working in 7.04"
date: 2007-05-15
forum: General Help
---

### Post by Sqweeks on 2007-05-15
Well i cant seem to get aircrack-ng to work with the rt2570 drivers. In Back Track 2 my hardware works fine and fake auth with my AP but in Ubuntu it wont work at all. Any idea what could be setup wrong? I would hate to have to dual boot BT2 and Ubuntu.

---

### Post by wieman01 on 2007-05-15
What error messages are you referring to? 

I can confirm that the card has issues... I can successfully send ARP requests and do see them them in Airodump, however, I would never receive responses so the number of data packages collected is not impacted at all. Are you referring to the same thing?

---

### Post by Sqweeks on 2007-05-15
So far i just can't get a successful Authentication or Association request. Ill try leaving it and see if i get any arp requests. When I run airoscript.sh in Back track 2 everything works right off the bat so i don't know if its just a driver version difference or what.

---

### Post by wieman01 on 2007-05-15
> **Sqweeks said:**
> So far i just can't get a successful Authentication or Association request. Ill try leaving it and see if i get any arp requests. When I run airoscript.sh in Back track 2 everything works right off the bat so i don't know if its just a driver version difference or what.
I don't know either. It should work as aircrack-ng contains a patch for the RT2570 driver. I never got Authentication/Association requests to work either. 

Let me know how it goes.

---

### Post by Sqweeks on 2007-05-15
Ok i installed the 1.3 drivers for rt2570 and i am able to get a fake authentication now. Got to restart now because my airoscript.sh is going wack. Ill post back soon if everything works.

---

### Post by wieman01 on 2007-05-15
> **Sqweeks said:**
> Ok i installed the 1.3 drivers for rt2570 and i am able to get a fake authentication now. Got to restart now because my airoscript.sh is going wack. Ill post back soon if everything works.
Cool. Would appreciate it. Did you install the CVS drivers then?

---

### Post by Sqweeks on 2007-05-15
Ok everything is working fine now. I dont know if its the fact that i did 
```

sudo airmon-ng stop rausb0
sudo airmon-ng start rasub0 6

```

and just set the channel there but it seemed to work.

edit: i used the rt2570-k2wrlz-1.3.0.tar.bz2 drivers. There was a guide on the aircrack-ng site and it listed those so i gave it a go.

---

### Post by wieman01 on 2007-05-15
> **Sqweeks said:**
> Ok everything is working fine now. I dont know if its the fact that i did 
```

sudo airmon-ng stop rausb0
sudo airmon-ng start rasub0 6

```

and just set the channel there but it seemed to work.

edit: i used the rt2570-k2wrlz-1.3.0.tar.bz2 drivers. There was a guide on the aircrack-ng site and it listed those so i gave it a go.
Excellent!

May I ask if you get ARP responses as well?

---

### Post by Sqweeks on 2007-05-15
Yes I do, and the injecting is working great. The #data in airodump-ng is shooting up like crazy. If you use airoscript.sh you dont need to airomon start and stop, just use the option in the script. I like to use the airoscript.sh from back track 2. If you want it download it from here [airoscript.sh]("http://kevan.killion.googlepages.com/airoscript.sh") just make sure you edit the DUMP_PATH in the file and everything should work good.

---

### Post by wieman01 on 2007-05-15
> **Sqweeks said:**
> Yes I do, and the injecting is working great. The #data in airodump-ng is shooting up like crazy. If you use airoscript.sh you dont need to airomon start and stop, just use the option in the script. I like to use the airoscript.sh from back track 2. If you want it download it from here [airoscript.sh]("http://kevan.killion.googlepages.com/airoscript.sh") just make sure you edit the DUMP_PATH in the file and everything should work good.
Man, a million thanks! I will give it a go over the weekend.

---

