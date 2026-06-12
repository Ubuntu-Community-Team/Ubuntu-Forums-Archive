---
title: "How to scale down performance (old laptop with overheating and freezing issues)"
date: 2015-07-02
forum: General Help
---

### Post by Juho_Maenpaa on 2015-07-02
I have a 10-year old laptop with an Intel Core Duo CPU (1,83 GHz) and ATI Mobility Radeon X1800 (256MB) GPU. I used WinXP with it and had constant problems with overheating which resulted in freezes. I could barely use XP by underclocking and -volting the CPU/GPU, regularly blowing off the dust inside the laptop and using low resolution. Anyway, I decided to try LXLE (a Ubuntu-variant) as it is supposed do wonders to older PCs. I barely got it installed via USB because of the overheating issue with my laptop. Unfortunately, while LXLE works great with my hardware, there is still the issue of overheating. It now seems that I yet again have to try to lower the performance of my system to prevent overheating.


I've tried to use Google and search for tips and tricks. I read about using 'cpufreq' which I managed to use but its powersave mode didn't help much. I tried to manipulate ATI GPU's powerstate settings but couldn't find up-to-date commands.


I'd now like to ask you for help in terms making LXLE/Ubuntu lighter for my laptop (resolution, CPU, GPU, underclock, undervolt, powersave etc.). I'm really a beginner concerning Ubuntu so while I can find information if you lead the way, I'd appreciate making it easier for me.

---

### Post by kerry_s on 2015-07-02
try installing thermald. 
sudo apt-get install thermald

you might want to keep trying other ubuntu versions, they all run differently. lxle is based on lubuntu, so try xubuntu & ubuntu-mate.
also might want to give elementary os a try, for me it gives the longest battery life, as well as staying cooler.

you think they would be similar since there all based on ubuntu, but i find they all react differently on the same hardware.
mines a hp-mini 210-1010nr 2x-1.6ghz atom 2gb ram

---

### Post by Yellow Pasque on 2015-07-02
Have you tried removing the heatsink(s), thoroughly cleaning, and reapplying the heatsink(s) with fresh thermal compound?

You can try setting "profile" and "low" to tame the GPU. Details here: [http://wiki.x.org/wiki/RadeonFeature/#index3h2](http://wiki.x.org/wiki/RadeonFeature/#index3h2)

---

### Post by Juho_Maenpaa on 2015-07-02
> **Temüjin said:**
> Have you tried removing the heatsink(s), thoroughly cleaning, and reapplying the heatsink(s) with fresh thermal compound?

I have opened the laptop, blowed off the dust and tightened the heatsink screws. I have thought about applying thermal paste but that stuff is pretty expensive and as I use this laptop maybe 1-2 a month, I don't want to invest anymore than I have to it. However, I might try eBay to find a cheap paste...

---

### Post by tgalati4 on 2015-07-02
Yes, definitely replace the paste.  Look around for a PC or electronics surplus store.  The paste with silver is expensive, but works well.  You can find ceramic paste that will work well as well and is cheaper.  At 10 years old, the original paste has dried out and is not doing its job.  If new paste does not fix the issue, then you may have a motherboard problem, or your CPU is worn out.

---

### Post by mattharris4 on 2015-07-03
You don't say what model the computer is but Toshibas are known for the air vent to the CPU filling in with dust and not allowing the fan and heat sink to do its job.  Videos how to rectify this are on YouTube but it is quite complicated as the computer has to be disassembled completely (and I mean COMPLETELY -- this is not like a desktop where servicing is relatively easy), the ventilation assembly removed from the computer, the dust cleaned out of it, thermal paste applied to the CPU, the ventilation assembly re-installed and then the computer completely reassembled.  This is more than I would attempt on my own but you sound like you are quite handy so the video may be worth a look if you have a Toshiba.  Unfortunately your CPU only scores a 795 Passmark score which is very slow (a new mid-line i3 equipped laptop scores in the 3000's, a refurbed Core 2 Duo scores around 1500-2500 depending on the speed rating) but if the computer works well for your use until it heats up $60-$80 to a computer repair shop to do this is better than the price on even a minimal refurb laptop (about $135 with Win 7 Pro installed).

I have seen a video with similar problems regarding a Dell laptop as well but I am unsure as to whether it affects all Dells of a certain vintage or if it is only one or two models.

---

