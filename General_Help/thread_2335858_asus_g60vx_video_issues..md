---
title: "asus g60vx video issues."
date: 2016-09-02
forum: General Help
---

### Post by javan-cardillo on 2016-09-02
Ok so heres the thing, on vista i get zero video card problems, not one, but as of late when ever i have run ubuntu i have been getting some major video issues and crashing problems where i have to restart the laptop by holding down the power button. I will include photos, one is of a massage that come up when i start the laptop and after i chose the ubuntu hard drive. And the other is pics of the video just doing what ever. I am running 2 hard drives one with windows vista and the other with ubuntu. I just got this machine hoping it wasnt gonna be a lemon and could last me some time. I own my own business and right now its not so good so dont tell me its a old machine and buy something new as i dont have that kinda money, if its the video card then i can replace that, if its the hard drive then i can replace that, but just dont tell me its the f-ing laptop cause far to many people have been saying just buy a new machines, well if i had the 1k to drop on a new computer do you think i wouldnt of done that.... yes im a bit salty.

---

### Post by mörgæs on 2016-09-02
If something is strong enough to run Vista it's not old on my scale.

Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by javan-cardillo on 2016-09-03
the person i got it from had windows 10 on it but cleaned the drive and put vista back on it,i only run vista for some games i have. i ran the code you put up and it did nothing.

---

### Post by javan-cardillo on 2016-09-03
the cpu is a Intel® Core&#8482;2 Duo CPU P7350 @ 2.00GHz × 2 and the gpu is a NVIDIA®  GeForce® GTX 260M with 1GB GDDR3 VRAM and im running 4 gigs of ram, i plan to get 8 gigs and put in a 3ghz cpu.

---

### Post by mörgæs on 2016-09-03
I don't think that you need more hardware. It should be enough to configure the stuff you have already. It's more powerful than anything in my household. 

Did you write the command I posted or did you use copy-paste?

---

### Post by javan-cardillo on 2016-09-03
both and didnt work, the main reason i plan to put in more ram and a bigger cpu is cause i want to game with my gf on warframe and as of right now the ram runs at 100% and the cpu at 70%, it also has a cooling issue so i have cut open a vent hole over the fan on the base, next will be a cooling pad and open up over the heatsink and maybe make a water cooling system for it, but right now the pressing issue is usability on linux, ubuntu 14 and 15 on both 32 and 64 bit could not run on this laptop. i have zero clue why but they both would just freeze and just not work, so im running 16 64bit and i keep having video issues.

---

### Post by javan-cardillo on 2016-09-04
Now let me add this i have the drivers for the gpu how ever i am NOT running them and am running the x.org driver thats using  Gallium 0.4 on NV92 and the reason i have chose not to use the nvida driver is when i ran the driver on both 14 and 15 i had to reformat the hard drive as it just wouldnt get past the login screen, were as when i was using the x.org on 14 and 15 it atleast logged on and then i could do stuff for like 5min then it would freeze. so i dont really feel like reformating the hard drive again if the driver blows up the hard drive again.

---

### Post by mörgæs on 2016-09-06
You don't have to reformat but if you have some extra space then a dual boot is a good place for experiments.

---

