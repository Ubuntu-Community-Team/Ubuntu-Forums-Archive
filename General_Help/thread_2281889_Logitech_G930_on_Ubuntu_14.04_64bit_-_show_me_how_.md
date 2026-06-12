---
title: "Logitech G930 on Ubuntu 14.04 64bit - show me how to get it working"
date: 2015-06-10
forum: General Help
---

### Post by AgentZ86 on 2015-06-10
Hi all

I have Logitech G930 on Ubuntu 14.04 64bit

Alsomixer shows it there, and I can select it as a soundcard but no sound
Also the ubuntu 14.04 sound settings does not show it there so I can't select it

Does anyone know how to get it working or what to try next ? 

Please advise
Thanks

---

### Post by AgentZ86 on 2015-06-10
UPDATED (SOLVED)

G930 is plug and play, HOWEVER, it does not seem to be detected if you plug into a 3.0 USB slot or perhaps even 2.0

All I did was to change the USB wireless interface and plugged into another slot that was not the 3.0 slot and it worked and detected perfectly

---

### Post by ksatta1 on 2015-09-05
After lots of testing and research etc I've come to the conclusion that the surround feature (Dolby Headphone) doesn't work in Linux (a semi-working workaround below) (Dolby Headphone is a software-only solution, currently available only in the Logitech Gaming software in Windows). So, I'm posting this here if anyone is doing research before buying it. I personally didn't do enough research and ended up with quite an expensive stereo headset that I thought would be surround.


Logitech's response is that they don't support Linux and there are no plans to support Linux, so I personally won't be buying anymore Logitech products.


I've contacted Dolby about this, maybe they could make some software solution that people could buy for Linux, to get Dolby Headphone. Very unlikely, but doesn't hurt to ask :)


**Workaround:** The best way I've found to make it (kind of) work is with jackd streaming the audio to Windows (virtual or real) and then, in Windows, Jack is outputting the 7.1 channels to the Logitech's driver. I'll post a tutorial on this later, I'm still testing and tweaking it. The biggest problem with this is the latency. I've been testing with a virtual Windows installation only so far, next I'll try a real Windows installation on another machine.


On the other hand it looks like Dolby Headphone is the best way to get surround sound with headphones, and there currently doesn't seem to be any manufacturers who support Linux.

---

### Post by valrossen-oliver on 2016-08-14
Hello, how did it go? Did you make any progress or did everything go to hell? :)

---

### Post by oldos2er on 2016-08-14
ksatta1 hasn't returned to the forums since the date of their last post. If you're having a similar problem please create a new thread; you can link back to this one if you think it helpful.

---

