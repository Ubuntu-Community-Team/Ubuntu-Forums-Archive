---
title: "Is there a cpu limit in Ubuntu?"
date: 2007-11-19
forum: General Help
---

### Post by ~LoKe on 2007-11-19
This isn't looking all that great.  /cat/proc/cpuinfo seems to indicate that my Q6600 (Quad core @ 2.4GHz stock) is running at 2GHz.  Panel frequency scaler applet says the same (gets the info from cpuinfo, I'd imagine).  However, conky tells me 3GHz.  I overclocked my processor in my BIOS to run at 9x335 (3xxxMHz).  Am I being limited to an actual speed of 2GHz, or is it truly using the full potential?

---

### Post by ahaslam on 2007-11-29
There's certainly not a cpu limit & it's not just Ubuntu either. It's either a problem with acpi or cpufreq, if you disable both of these you'll sacrifice scaling for the correct reading. I have an e6300 clocked to 3.15GHz & only 2.33GHz is displayed. I can assure you that performance is not affected (assuming performance or on-demand throttle) as I've tested it with numerous super_pi runs.

Any chance you can pm your conkyrc? ;)

---

### Post by s3a on 2007-11-29
I don't really have any help to offer, sorry, but I just wanted to say that to my knowledge Ubuntu has a 16 core limit. Mac has a 2 core limit...I think and Windows XP has a 32 core limit. Just so you know...

---

### Post by aldenhg on 2007-11-29
s3a, you're wrong about OSX having a 2 core limit. Look at the MacPro line.
[http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?nnmm=browse&mco=7B72365D&node=home/shop_mac/family/mac_pro](http://store.apple.com/1-800-MY-APPLE/WebObjects/AppleStore.woa/wa/RSLID?nnmm=browse&mco=7B72365D&node=home/shop_mac/family/mac_pro)
I'm also pretty sure that if there is a limit for Ubuntu it's MUCH higher than 16 and XP can only have 2 CPUs - but those CPUs can be multi-cored which right now would place the limit at 8 cores.

---

### Post by ahaslam on 2007-11-29
I'm sure that cpu *speed* limit was intended. That's certainly the context in which I replied. 

Let's not stray, eh ;)

---

