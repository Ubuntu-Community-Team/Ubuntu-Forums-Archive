---
title: "FreeFileSync FFS very slow. Other ways to copy 1.2TB of files to external HDD?"
date: 2023-12-30
forum: General Help
---

### Post by Advait on 2023-12-30
I'm using Ubuntu 22.04 on a laptop. Earlier today I started a FFS mirror job of my 1.2TB user files to an external USB-C connected spinning hard drive. FFS says the job will take 30 days...!!!! Also, while FFS was running, I was unable to start any other apps on my 40GB-RAM Ryzen 7 laptop. So naturally I stopped the FFS job. My main drive is a laptop internal 2TB nvme.

Is there a faster way to copy files to an external USB-C connected spinning hard drive? Should I use an USB-C connected external nvme drive instead? (I'll buy one if needed to get decent copy times.)

I'm thinking if I find a a faster way to copy files to the external drive, I'll use FFS to sync future jobs (which will be small and go very fast).

---

### Post by MAFoElffen on 2023-12-30
Yes. You are already using USB3.2 USBC... Those interface speeds are going to be from 5GiBs to 40 GiBs. (depening on the Gen) So the Speed of the drive is going to matter. HDD is not very fast,compared to Silicon SSD. 

I have both External SDD and NVMe. With NVMe, I don't have to wonder if it can write fast enough. I can tell you that is has been a change for moving TB's of data, from previously taking hours, to it olny taking minutes.

I bought a dual caddy NVMe M.2 m-key drive case, so I could clone drives, on-site, quickly and easily. It has paid for itself in time savings and use.

---

### Post by Advait on 2023-12-30
Does your dual caddy nvme drive case have a fan(s)?

---

### Post by Advait on 2023-12-30
> **MAFoElffen said:**
> Yes. You are already using USB3.2 USBC... Those interface speeds are going to be from 5GiBs to 40 GiBs. (depening on the Gen) So the Speed of the drive is going to matter. HDD is not very fast,compared to Silicon SSD. 

**[[Yes, this is very true! :p ]]**

I have both External SDD and NVMe. With NVMe, I don't have to wonder if it can write fast enough. I can tell you that is has been a change for moving TB's of data, from previously taking hours, to it olny taking minutes.

**[[Sounds good, I'll get a quality nvme and a case with a cooling fan. 30 days for a backup is a bit much...  :) ]]**

I bought a dual caddy NVMe M.2 m-key drive case, so I could clone drives, on-site, quickly and easily. It has paid for itself in time savings and use.

text

---

### Post by MAFoElffen on 2023-12-30
Both of mine have aluminum heatsinks:
[https://www.amazon.com/gp/product/B0B6NXFJK7/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B6NXFJK7/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)
[https://www.amazon.com/gp/product/B0B6N92K1H/ref=ppx_yo_dt_b_asin_title_o09_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B6N92K1H/ref=ppx_yo_dt_b_asin_title_o09_s00?ie=UTF8&psc=1)

Watch which "keys" they are before you order them. Current today is m-key. The first one up there had one bay as m-key, with the other as b+m-key. The second was m-key.

When I was doing onsite calls, I brought both, so I could support either. Now that I don't do that as much, I have the b-key in the single, and use that fro my Rasp Pi4. The dual tray caddy I have with both m-key trays, and still use it for backups and cloning drives.

---

### Post by Advait on 2023-12-31
> **MAFoElffen said:**
> Both of mine have aluminum heatsinks:
[https://www.amazon.com/gp/product/B0B6NXFJK7/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B6NXFJK7/ref=ppx_yo_dt_b_asin_title_o00_s00?ie=UTF8&psc=1)
[https://www.amazon.com/gp/product/B0B6N92K1H/ref=ppx_yo_dt_b_asin_title_o09_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B0B6N92K1H/ref=ppx_yo_dt_b_asin_title_o09_s00?ie=UTF8&psc=1)

Watch which "keys" they are before you order them. Current today is m-key. The first one up there had one bay as m-key, with the other as b+m-key. The second was m-key.

**[[ Yes, good reminder. I have a few nvme m.2 drives so I've learned to be careful and make sure I'm getting drives with the right key. ]]**

When I was doing onsite calls, I brought both, so I could support either. Now that I don't do that as much, I have the b-key in the single, and use that fro my Rasp Pi4. The dual tray caddy I have with both m-key trays, and still use it for backups and cloning drives.

text

---

### Post by Advait on 2023-12-31
Update: I did have my external HDD connected to a powered USB hub. But I moved it to directly connected to my laptop. Also I dropped FreeFileSync and I&#8217;m now trying Grsync. I&#8217;m now doing a big backup to the same HDD drive and it seems to be going a lot faster with a direct connection and using Grsync. 

Hopefully these changes will lead to a fast and successful backup. I&#8217;ll report back w results.

Update, Looks like the direct connection worked. Only took 15 hrs for FFS to complete the 1.2TB backup.

---

### Post by Advait on 2023-12-31
Is there a Linux Ubuntu app that displays real time up to date data transfer speeds to external USB connected HDDs? Looks like hdparm does not do this. (UPDATE: I found one called MissionCenter; works great.)

---

