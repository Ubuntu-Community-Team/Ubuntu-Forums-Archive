---
title: "System freezing, strange CPU behavior"
date: 2013-06-27
forum: General Help
---

### Post by colsonutter on 2013-06-27
I installed Ubuntu a few days ago and am getting some strange freezing behavior. Programs will freeze momentarily (~5s), and instead of seeing all CPU usage spiking to 100%, all CPU usage drops to 0 which is lower than even system idle CPU usage which hovers around 5%.

This happens with the file manager, firefox, system settings, minecraft, gimp, everything. 

I have a 4x 2.3GHz Intel Core i5-2410M CPU, and 16GB RAM, with Intel 3000 Mobile HD graphics with 512MB dedicated memory.

I can see no reason why this hardware setup would freeze the system for 5 seconds when I do simple things like click on links in my web browser.

Any ideas?

[ATTACH=CONFIG]244219[/ATTACH]

---

### Post by PaulW2U on 2013-06-28
> **colsonutter said:**
> I installed Ubuntu a few days ago and am getting some strange freezing behavior. Programs will freeze momentarily (~5s), and instead of seeing all CPU usage spiking to 100%, all CPU usage drops to 0 which is lower than even system idle CPU usage which hovers around 5%.

This happens with the file manager, firefox, system settings, minecraft, gimp, everything. 

I have a 4x 2.3GHz Intel Core i5-2410M CPU, and 16GB RAM, with Intel 3000 Mobile HD graphics with 512MB dedicated memory.

I can see no reason why this hardware setup would freeze the system for 5 seconds when I do simple things like click on links in my web browser.

Any ideas?

[ATTACH=CONFIG]244219[/ATTACH]

Over the last month I've experienced regular freezes of around 5 to 10 seconds after which I regain control of my PC although the screen updates much slower than before the freeze. Sometimes a further freeze totally disables the system and I have to force a reboot. :(

I've seen such freezes while using Opera, Firefox and Krusader. I haven't noted the CPU activity around the time of the freeze but it will be something that I will try to look out for in future.

The specification of my PC is similar although inferior to yours. You didn't say what version or flavour of Ubuntu you're using but I'm running Kubuntu 13.04 and don't have this problem on my laptop which runs the same version of Kubuntu.

I can't help with the solution but at least the thread will be bumped. :)

Do you notice any deterioration in the speed of the screen updating after the freeze?

---

### Post by colsonutter on 2013-06-28
This is on normal Ubuntu. 
The whole system doesn't freeze, it's just one application, like for example, right clicking on a link (in any web broswer) will often take 5-10 secs for the menu to open even when there are no other applications running. CPU use will be at like 15-20% and then drop to 0% for the 5-10 seconds. Very strange and annoying.

---

### Post by Ranko Kohime on 2013-06-29
IOwait, perhaps?

Run "top" in a terminal, and see if the number in the 3rd row marked "wa" spikes.  immediately to the left is "id", for idle.

Just a hunch.

---

