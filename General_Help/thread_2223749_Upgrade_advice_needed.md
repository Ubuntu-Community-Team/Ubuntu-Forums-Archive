---
title: "Upgrade advice needed"
date: 2014-05-12
forum: General Help
---

### Post by ofnuts on 2014-05-12
I'm currently running Kubuntu Quantal on a Lenovo ThinkPad T430. The disk is encrypted with LUKS. Since Quantal is getting out of service I'll have to move to a later version.

Any chance given the above to successfully upgrade to 13.10 or 14.04? Or should I burn my bridges, make a good backup (which I'll do anyway for the upgrade) and reinstall from scratch? Since it it my work system I don't want to to be unusable for tool long.

Any good or bad experiences?

---

### Post by sammiev on 2014-05-12
I tried a few upgrades and they all took with no issues. But yes, backup first.

---

### Post by Yellow Pasque on 2014-05-12
I think you'd have to upgrade to 13.04 first, and that's already EOL because non-LTS releases are supported for only 9 months now.
If you don't like to upgrade every 6 months, do a fresh install of 14.04 LTS (or switch to a rolling release distro).

---

### Post by ofnuts on 2014-05-13
Anyone upgrading with LUKS? Because there are several war stories when you google for it...

---

### Post by Elfy on 2014-05-13
> **Temüjin said:**
> I think you'd have to upgrade to 13.04 first, and that's already EOL because non-LTS releases are supported for only 9 months now.
If you don't like to upgrade every 6 months, do a fresh install of 14.04 LTS (or switch to a rolling release distro).

I think that the upgrade route from 12.10 was dealt with - they knew that 13.04 would go EOL before 12.10.

---

### Post by mastablasta on 2014-05-13
i upgraded 13.04 to 13.10 in april. waiting a bit (plus i do not have time at the moment) until we upgrade to 14.04 on one PC.

eventhough 13.04 was EOL it just upgraded as usual to 13.10.

i don't know what happens with LUKS but it should be tested (since feature is available) and should work. i would backup and upgrade.
any PPA's get disabled and new PPA's get prepared so youc an just re-enable the new one sif oyu have any. very nice and smooth process. the only issue i had with upgrade to 14.04 is baloo. well it's not an issue it is just really agressive when it indexes the files. upgrade was about 2 hours, and then baloo took 3 hours on oldish mashicne to complete the indexing. after that 14.04 in my case boots slower than earlier versions, takes a bit more ram on boot, however desktop is way more responsive.

also on my laptop Fn keys and "Prt Sc" key stopped working and camera doesn't work anymore in skype in 14.04. so you might want to try some live session and check for posible solutions or workarrounds before doing the upgrade to 14.04.

---

### Post by sammiev on 2014-05-13
> **mastablasta said:**
> i upgraded 13.04 to 13.10 in april. waiting a bit (plus i do not have time at the moment) until we upgrade to 14.04 on one PC.

eventhough 13.04 was EOL it just upgraded as usual to 13.10.

i don't know what happens with LUKS but it should be tested (since feature is available) and should work. i would backup and upgrade.
any PPA's get disabled and new PPA's get prepared so youc an just re-enable the new one sif oyu have any. very nice and smooth process. the only issue i had with upgrade to 14.04 is baloo. well it's not an issue it is just really agressive when it indexes the files. upgrade was about 2 hours, and then baloo took 3 hours on oldish mashicne to complete the indexing. after that 14.04 in my case boots slower than earlier versions, takes a bit more ram on boot, however desktop is way more responsive.

also on my laptop Fn keys and "Prt Sc" key stopped working and camera doesn't work anymore in skype in 14.04. so you might want to try some live session and check for posible solutions or workarrounds before doing the upgrade to 14.04.

Skype works great here with 14.04 but I had to turn it on at the bottom of the screen the first time.

---

