---
title: "Expanding Swap partition"
date: 2007-11-21
forum: General Help
---

### Post by vgrisham on 2007-11-21
I've just doubled the RAM on my computer from 2GB to 4GB. My swap partition is currently sitting at 4gb. I read somewhere that it should be twice as big as the computer's installed RAM (please correct me if that's wrong). So, I want to increase my swap partition from 4gb to 8gb.

I was thinking that I should boot to the live cd and edit the partitions using gparted. Will I also have to change anything grub wise or make any other changes?

Thank you in advance.

---

### Post by mikewhatever on 2007-11-21
No, don't do it. Even 1 GB of swap is more then enough for most PCs. With either 2 or 4 GB of RAM you most probably do not need swap at all, unless you hibernate. Does swap ever get used? Use free or free -m command to check your memory usage.

---

### Post by vgrisham on 2007-11-21
> **mikewhatever said:**
> Does swap ever get used?

I'm not sure. How could I tell if it were being used?

---

### Post by mikewhatever on 2007-11-21
Here's mine with only 1 GB of RAM.

---

### Post by vgrisham on 2007-11-21
Well, sweet! I didn't want to have to mess with that anyway. Thanks for the advice. 

Happy Thanksgiving.
Vaughn

---

