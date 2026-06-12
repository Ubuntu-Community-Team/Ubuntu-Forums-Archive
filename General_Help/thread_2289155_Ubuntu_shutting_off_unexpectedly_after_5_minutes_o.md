---
title: "Ubuntu shutting off unexpectedly after 5 minutes of boot"
date: 2015-08-01
forum: General Help
---

### Post by satyamM on 2015-08-01
Hi,

There is a very strange problem that has happening from yesterday in my system. The system immediately shuts off without any warning sign after 5 minutes of boot. And 5 minutes is the time in first boot. If second boot is made after that, it only allows me to login and then shuts off immediately after 2 minutes. This goes on and on no matter how many logins I do. There is some serious problem I suppose.

Help!
Thanks and Regards
Satyam

---

### Post by QIII on 2015-08-01
Hello!

What happens if you wait 30 minutes before trying to boot in again?

---

### Post by tgalati4 on 2015-08-01
What kind of computer is it?  If it is a laptop, remove the battery.  Plug in the AC cord and try booting.

---

### Post by satyamM on 2015-08-02
> **QIII said:**
> Hello!

What happens if you wait 30 minutes before trying to boot in again?

I booted just now after 12 hours of gap. Same thing! Lasted for 5 mins and gone. I could open my browser and checked few social media. That's it. Second time I booted, it lasted for 3 mins and gone.


@[COLOR=#000000]tgalati4 - I removed battery yesterday only. And currently running system on A/C. I am running 14.04 on a Dell Inspiron N5010 , 2.8GB RAM, 2010 bought.


[/COLOR]

---

### Post by tgalati4 on 2015-08-02
Does the system suddenly shut off when running on AC only?

---

### Post by pqwoerituytrueiwoq on 2015-08-02
maybe it if full of dust bunnies causing it to overheat
install sensors and check the temps
```
sudo apt-get install lm-sensors
sudo sensors-detect # answer yes to all
sensors
```
maybe there is a bad connection for the cpu cooler
maybe the power cord is damaged and only works in certain positions
maybe you need to pass a special kernel parameter so the fan works right

---

### Post by satyamM on 2015-08-02
> **tgalati4 said:**
> Does the system suddenly shut off when running on AC only?

Yes it does shut off exactly like that!

---

### Post by satyamM on 2015-08-02
And now the system is stuck on the grub options. I hit enter and nothing happens. Just stays there.

Attached is the screenshot of my grub screen.

---

### Post by tgalati4 on 2015-08-02
You might need a new power brick.  If the power supply can't supply enough current to boot the computer and you have a dead battery, then you get similar shut down symptoms.

---

### Post by satyamM on 2015-08-02
Shouldn't the A/C be enough to boot it? I understand the battery might have gone down, since I have not changed it since I bought this computer. But why is it not working with A/C? Thanks for your comments.

---

### Post by tgalati4 on 2015-08-02
A bad battery draws too much current which weakens the power brick.  Now the power brick can't supply enough current to boot the computer without the battery.  This is a common problem.  Find a new power supply.

---

### Post by leunam12 on 2015-08-03
It sounds like overheating. Remove the keyboard and use an air compressor or one of those compressed air cans to blow air from the exhaust vents into the computer. What kind of computer is this? (brand, model)

---

