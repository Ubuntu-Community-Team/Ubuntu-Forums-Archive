---
title: "External Monitor prompt flashing all the time"
date: 2020-11-26
forum: General Help
---

### Post by meetdilip on 2020-11-26
I have 20.04 and 18.04 as dual boot. In both of them, the *external monitor selection prompt* flashes annoyingly. It doesn't matter which one I select, the option to choose which monitor does not go away. In short, I cannot work at all if I attach a monitor through HDMI to my laptop. This issue is only when I use an external monitor, which I cannot avoid at this moment. Is there any method to kill it ? I have the same issue when using KDE Plasma, which goes away when I stoop Kscreen2  through settings > background services . Is there any similar kill switch that I can use to make this flashing prompt go away ? Thanks

---

### Post by CelticWarrior on 2020-11-26
Is your intention to use both monitors or just the external when the external is connected?

---

### Post by meetdilip on 2020-11-26
Thanks for the reply

External will be fine. But I do not want to lose the laptop's built-in monitor gone forever.

---

### Post by CelticWarrior on 2020-11-26
It can be either way and there's no reason for the thing you allude to (I don't really know what you're talking about).
In standard Ubuntu (Gnome) multi-monitor desktop is set in System Settings > Screens. There you can select mirrored or extended desktop, the relative position of different screens and, if you want only the external monitor you can also disable the internal one. This settings will persist unless changed to something else but, obviously, will only take effect if and when an external monitor is connected. Meaning: The internal always work if nothing else is connected but will turn off when the external monitor is connected.

All of this is pretty simple and basic. I feel you're kind of clueless and, again, I have no idea about what you're actually complaining about, [COLOR=#000000]the [/COLOR]*external monitor selection prompt &#8203;[that] flashes annoyingly.*

---

### Post by meetdilip on 2020-11-26
Let me explain. 

1. I start Ubuntu 20.04 laptop with an external monitor plugged in through HDMI
2. At some point, mostly after logging in, the screen starts flashing between black and normal monitor output
3. A short while after the prompt to select options appear.
4. This prompt in my case is useless. No matter what I select, 

a. The prompt comes back flashing and won't let me work on Ubuntu
b. Screen blinks between black and normal monitor output

5. I tried selecting my choice through Settings and press Apply
6. I won't be recorded, the whole saga of blinking and prompt flashing continues


What I am looking for 

a. Please help me get a stable laptop and monitor display
b. Through settings whatever choice I Apply stays
c. Please make the flashing prompt go away after display is stable

Thanks.

---

### Post by CelticWarrior on 2020-11-26
Please post your hardware specifications, particularly the graphics.

---

### Post by meetdilip on 2020-11-26
I used Neofetch

OS: Ubuntu 20.04.1 LTS x86_64 

Kernel: 5.4.0-54-generic 
 Uptime: 36 mins 
Packages: 2723 (dpkg), 12 (snap) 
Shell: bash 5.0.17 
Resolution: 1366x768, 1366x768 
DE: GNOME 
WM: Mutter 
WM Theme: Adwaita 
Theme: Yaru-Orange [GTK2/3] 
Icons: Froze [GTK2/3] 
Terminal: gnome-terminal 
CPU: Intel i5-2430M (4) @ 3.000GHz 
GPU: AMD ATI Radeon HD 6630M/6650M/6 
GPU: Intel 2nd Generation Core Proce 
Memory: 1784MiB / 3841MiB 

Thanks for your time

---

### Post by meetdilip on 2020-11-26
If I may, is there any way to kill this prompt ? Because without it flashing and choosing by its own, everything is fine.

---

### Post by CelticWarrior on 2020-11-26
Again, I have no idea what that prompt is, never seen it in spite of having used hundreds of multi-monitor configurations.

---

### Post by meetdilip on 2020-11-26
I see. This prompt is my main villain. It is a small strip in the middle of the screen with 4 options ( icons )

------------------------------------
Mirror | Join | External | Built-in
------------------------------------

If only I can kill it after login, I will be able to use Ubuntu without trouble. It flashes too much that I barely had time to fetch the Neofetch details.  Thanks.

---

### Post by tea for one on 2020-11-26
> **meetdilip said:**
> Let me explain. 

1. I start Ubuntu 20.04 laptop with an external monitor plugged in through HDMI


Have you tried to start your Ubuntu 20.04 laptop **without** the external monitor attached?

Then plug it in after logging in to Ubuntu.

---

### Post by ajgreeny on 2020-11-26
You still have not shown us the hardware you're using; neofetch output is not good enough for the detail we need so as a start please show us the output of ```
inxi -Fzx
```

---

### Post by meetdilip on 2020-11-26
I tried starting Ubuntu first and then plugging in the monitor through HDMI. But the issue persists. I somehow manage to capture a screenshot this time

[ATTACH=CONFIG]287461[/ATTACH]

---

### Post by CelticWarrior on 2020-11-26
OK, that I've seen before and it only appears when we use the "screens configuration" key (typically one of the functions keys or a key combo - FN+Fsomething).

---

### Post by meetdilip on 2020-11-26
> **ajgreeny said:**
> You still have not shown us the hardware you're using; neofetch output is not good enough for the detail we need so as a start please show us the output of ```
inxi -Fzx
```

I tried the above command. It says>  inxi - command not found


---

### Post by meetdilip on 2020-11-26
> **CelticWarrior said:**
> OK, that I've seen before and it only appears when we use the "screens configuration" key (typically one of the functions keys or a key combo - FN+Fsomething).

I see. I haven't touched anything after login. Not even the mouse. But it still prompts. Thanks.

---

### Post by CelticWarrior on 2020-11-26
Perhaps you should check your keyboard then...
Nevertheless, what happens after you select your desired option? If it appears again then most likely you have a stuck key.

---

### Post by meetdilip on 2020-11-26
Ok. I will check the keys. But whatever I select through the prompt and settings does not save. The whole saga of blinking continues, no matter which one I choose. Interestingly, the prompt chooses a random answer every time it flashes. ie, first it will choose joint, the external, the mirror and so on. No pattern, mostly random and its own choice.

It is almost 2:00. Too tired. Please don't mind, I have to leave. Kindly do leave you inputs. Thanks.

---

### Post by meetdilip on 2020-11-26
I checked twice. Keys looks fine. Because I have Kubuntu desktop installed and I get this prompt there as well. But it goes away when I  " Stop " a process called " Kscreen2 ". If possible, can you tell me which process can do the same with Gnome / default DE ? Thanks

---

### Post by meetdilip on 2020-11-28
Regret bumping, which process to kill to stop the prompt from flashing ? Thanks.

---

