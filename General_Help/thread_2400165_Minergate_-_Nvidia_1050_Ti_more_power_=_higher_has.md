---
title: "Minergate - Nvidia 1050 Ti more power = higher hash rate?"
date: 2018-09-03
forum: General Help
---

### Post by rharrower on 2018-09-03
Hi guys sorry if this is not a direct question about Ubuntu. However I use and run Ubuntu 18.04 on my mining computer am currently getting 600h/s mining monero with the GUI minergate software (note not V8.3 because that keeps crashing).

But am trying to work out how to increase the hash rate of the graphics cards. However there seems to be little to no easy documented way of overclocking the 1050 and the 1050 Ti versions (yes I have one of each) the Ti version runs a little faster then the non Ti version but I expected that. What however I did not expect was to get a rough 550-600h/s I was hoping to be getting Mh or just something in the 1000h/s.

Now that might not be possible saying that am not here asking how to get higher hash rates by coding. But more would increasing the power supply from 500w to 1000w help.

I know it seems a stupid question, but I don't want to spend $600+ on a new power supply only to find out that while yes it could increase hash rate, but the time I add 4-6 more cards I will once again either need another power supply or buy a higher power supply unit.

So could someone please either point me in the correct way to increase hash rate or tell me the correlation to power supply vs hash rates. I'll even watch YouTube video on it if you can point me in direction

Thanks

---

### Post by Yellow Pasque on 2018-09-03
Either the power supply unit (PSU) can meet the power demand of the system, or it cannot. If it cannot, the system will be unstable (crashing or sudden shutdown/reboot).

For OC'ing, see: [https://noobminer.xyz/overclocking-multiple-nvidia-graphics-card-linux/](https://noobminer.xyz/overclocking-multiple-nvidia-graphics-card-linux/)
Note that not all cards support OC'ing, even with Coolbits flipped on. And of course, you void your warranty and risk hardware damage. If it breaks, you keep the pieces.
Also note that the guide recommends using Nvidia drivers directly from Nvidia.com. That is a bad idea. If you must have the latest and greatest driver, use: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

