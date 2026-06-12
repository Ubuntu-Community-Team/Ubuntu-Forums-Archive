---
title: "Ubuntu freezes a lot..."
date: 2008-06-28
forum: General Help
---

### Post by Hellraizer51 on 2008-06-28
I have Ubuntu on my machine, but when I do heavier tasks (which aren't that heavy at all), like moving some files from my EXT3 partition to the NTFS partition and then trying to browse the web with Firefox, Firefox freezes all over the place. This also happens in other situations, but I can't remember them. Also, this does not happen in Windows XP or Vista. My specs are Q6600, 2GB of 800MHz DDR2 RAM and 8800GT 512MB. I have Compiz Fusion installed as well, but I doubt it has anything to do with this freezing problems. And yes it's a fresh install so this kinda stuff shouldn't happen.

---

### Post by danwood76 on 2008-06-28
When you say firefox freezes all over the place is it just friefox or your whole system?

What version of the nvidia drivers are you running?
There have been stability issues with one version of the driver with particular cards, you can try updating them you can get them from the nvidia site.

---

### Post by Hellraizer51 on 2008-06-28
Just Firefox. And my drivers are 173.14.09.

---

### Post by citizenchris099 on 2008-06-28
how can you tell what drivers you are using? (noob question i know lol)

---

### Post by Hellraizer51 on 2008-06-28
Type nvidia-settings in the terminal, and then it's around there, don't remember where though because I'm not in Ubuntu right now.

---

### Post by danwood76 on 2008-06-28
Do you have any addons installed in firefox?
Are the pages you are viewing when it slows down heavily flash orientated?

---

### Post by Hellraizer51 on 2008-06-28
No addons in Firefox, and if you count the Ubuntu Google start page as heavy, then you're crazy :P

---

### Post by danwood76 on 2008-06-28
Hehe, ok.

What version of firefox do you have?
The final release of firefox 3 is already out if you havent already updated from the beta.

---

### Post by Hellraizer51 on 2008-06-28
It's the final release of 3 of course.

---

### Post by Hellraizer51 on 2008-06-28
But as I have said, it doesn't happen only in Firefox, it happens in other cases too. But for example I believe that if I start file transfering and doing stuff on my system (viewing images, opening programs, etc) it also freezes.

---

### Post by lanzailan on 2008-06-28
i'm having problem when i watch youtube.. my firefox freeze

---

### Post by Hellraizer51 on 2008-06-28
No one's got a solution?

---

### Post by danwood76 on 2008-06-29
@lanzailan
This is a flash issue, you could try the latest beta build of flash 10 to see if its any more stable for you.

@Hellraizer51

You make it sound as if it only happens when transfering files, are these to ntfs partitions?
The ntfs-3g driver does use a little more CPU time than any of the other fs drivers, though with your CPU I dont see why this would slow you down.

It could be something to do with CPU frequency scaling, add the CPU frequency scaling meter to your gnome panel and see if it always stays on the lowest setting, it should spike up everytime you go under load but if it stays low then you may have a scaling issue.

---

