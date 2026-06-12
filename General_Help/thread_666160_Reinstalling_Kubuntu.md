---
title: "Reinstalling Kubuntu"
date: 2008-01-13
forum: General Help
---

### Post by Khane on 2008-01-13
A friend of mine convinced me to give Kubuntu a try and he himself installed it on my computer a few weeks ago. I would like now to make a fresh install of Kubuntu by myself.

Right now I gave kubuntu 12GB of my 140GB hard disk: Root on a 2.8GB partition , /home on a 9.2GB partition and SWAP on 5126 MB. Are these good setting or should I give on my new install a bigger partition to Root  and SWAP ? I have no problem to shrink my NTFS D: drive and dedicate 10GB more to Kubuntu if needed. Are there optimal and minimal partitioning setting for Kubuntu ? By the way, I have 2GB Ram.

There is on thing I remember from when my friend installed Kubuntu; when he was partitioning, he was asked if he wants to install the different parts on the BEGINNING or END. What should I choose and is it important ?


Thanks.

---

### Post by misfitpierce on 2008-01-13
Atleast 8GB is good for root... and 2GB of SWAP is more than enough.

---

### Post by .nedberg on 2008-01-13
I would go for a bigger /, about 2GB for swap (I think you meant you had 512MB swap atm). How much you want for /home is up to you...

---

### Post by Khane on 2008-01-13
> **.nedberg said:**
> How much you want for /home is up to you...

I have no idea how much I **need** because I don't know how thing work in Kubuntu. In Windows I know that unless I decide to install a program on drive D:,then programs are installed by default on drive  C: Program Files . How is it on Ubuntu? Where are programs installed, on root or home ?

Thanks for helping
Khane

---

### Post by .nedberg on 2008-01-13
/home will be like "My Documents" in Windows. Programs go to /

---

### Post by Khane on 2008-01-13
Thank you very much for the very useful information.  Is placing root , home or SWAP on the BEGINNING or END during the install important ? If so then what's right for each of them?

---

### Post by .nedberg on 2008-01-13
Acctually I don't know...

But I think the installer places / first, then swap (it doesn't set up a separate /home). Try /, swap, /home.

---

