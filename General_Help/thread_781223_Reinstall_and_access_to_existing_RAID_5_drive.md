---
title: "Reinstall and access to existing RAID 5 drive"
date: 2008-05-04
forum: General Help
---

### Post by Scorpuk on 2008-05-04
I plan to do a clean install of 8.04 and would like to know if the existing RAID 5 volume I have will be accessible on the new system without loosing the data?

---

### Post by fjgaude on 2008-05-04
Yes, the raid5 and all of its data will be as it is. All you have to do is install mdadm and then:

sudo mdadm --assemble --scan

That's it... I've done it many, many times going from motherboards and new installs of Ubuntu, 64 and 32-bit, etc.

It always worked.

Let us know how you make out.

---

### Post by Scorpuk on 2008-05-05
Thanks for the reply. 


Forgot to mention that this is a hardware raid. I setup with webmin, mainly as I wasnt to familiar with seeting up Volume Groups and logical groups.


Will the command still work?


Cheers.

---

### Post by fjgaude on 2008-05-05
No, no... that command is only for software raid setup with mdadm.

What kind of hardware raid do you have, a card or the kind that is on the motherboard?

If the latter you will have to learn to use dmraid... which I don't use anymore... not too flexible and likely doesn't work readily with raid5.

---

### Post by Scorpuk on 2008-05-06
I have an AMCC/3Ware 9650SE-12ML KIT.

---

### Post by fjgaude on 2008-05-06
> **Scorpuk said:**
> I have an AMCC/3Ware 9650SE-12ML KIT.

Well, just follow instructions that comes with the board, the kit, when you change out your present system. You shouldn't have any issues.

---

