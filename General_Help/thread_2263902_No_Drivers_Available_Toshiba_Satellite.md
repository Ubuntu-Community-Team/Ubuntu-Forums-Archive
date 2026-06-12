---
title: "No Drivers Available Toshiba Satellite"
date: 2015-02-04
forum: General Help
---

### Post by devdlp on 2015-02-04
Ive been trying to install ATI and AMD drivers on ubuntu 14.04 and havent been able to because of an driver problem but i dont know what it is and when i go to software 7 updates then to available drivers there are no available drivers listed what cfan i do to get drivers listed and use them? Or is it just a internal problem with my card, please help. On my other computer the drivers are listed automaically and there's a few of them that makes me think something is wrong with this laptop i dont know.

---

### Post by Peptid on 2015-02-05
Hi,

Which graphic cards are there in your laptop? You should check if propriety drivers are available, and you can do this from settings -> additional drivers (or similar). 

I had a similar problem with my HP pavilion dv6 laptop, and we figured out that no later version of Ubuntu than 12.04.1 supported the drivers. So, you may also want to check this, if the problem resists.

---

### Post by mörgæs on 2015-02-05
Yes, please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by Mark Phelps on 2015-02-05
> Ive been trying to install ATI and AMD driversIf you are seeing a desktop, not a command line, then you already have AMD drivers installed -- just the default open-source drivers, not the proprietary ones.

> there are no available drivers listedThis means there are no restricted drivers available for your PC and the version of Ubuntu you are running.

> On my other computer the drivers are listed automaically Drivers are hardware-specific; different computers have different hardware.

---

### Post by devdlp on 2015-02-05
thanks

---

