---
title: "Few problems with my Dell E1505"
date: 2007-02-20
forum: General Help
---

### Post by NOSintake on 2007-02-20
ok, so i got linux to run, and after some updates im still having a few problems.

ubuntu doesnt want to boot when my power supply is in. i have a dual core processor, so when the power is plugged in, it doesnt want to boot. not only that, it doesnt want to boot when anything is plugged in. i have several usb ports that are plugged in, and it doesnt want to boot when i have those plugged in.


i think thats it for now, but as i have problems, ill post them. by the way, this is my first time using linux, so if these are stupid questions, im sorry, im just not use to linux (dual booting with windows)

thanks for the time to read this


system specs incase you need to know:
100GB hard drive (20 to linux, 70 to windows)
ati x1400 video card
1gb of ram (2x512mb)
dvd drive

---

### Post by gradedcheese on 2007-02-21
> 
ubuntu doesnt want to boot when my power supply is in. 


can you ellaborate on that?  how far in the process does it get?  are there any error messages?

---

### Post by bettlebrox on 2007-02-21
What kernel version are U using?

---

### Post by NOSintake on 2007-02-21
> **bettlebrox said:**
> What kernel version are U using?

you mean like which version? 6.10.

what i mean is, when i have my laptop plugged in, it wont boot fully. i get the loading screen before i log in, and it hangs. i read that if you have a dual core cpu, that it wont boot about 60% of the time, and that i should just use 1 cpu. when i dont have the power in, only 1 cpu is working, thus allowing me to boot up. 

but ive tried booting up with only the power supply out, and other things plugged in, such as usb, sound, and etc, and it still wont boot up. the only thing i can have in for a fact is my ethernet cord

---

### Post by gradedcheese on 2007-02-21
I've used Ubuntu on a dual-core laptop and worked just fine.  "what kernel?" means, in a terminal, run the command:

```

uname -r

```

---

### Post by NOSintake on 2007-02-21
2.6.17.11 generic

---

### Post by gradedcheese on 2007-02-21
just curious: can you reboot with the older kernel?  To do that, reboot and then press ESC for the grub menu (it's right after the BIOS), and select the second newest kernel (2.6.17-10-something) ...will it boot correctly this way, even with the power supply plugged in?  I haven't had a chance to try to -11 kernel on a dual-core laptop yet.

---

### Post by NOSintake on 2007-02-21
> **gradedcheese said:**
> just curious: can you reboot with the older kernel?  To do that, reboot and then press ESC for the grub menu (it's right after the BIOS), and select the second newest kernel (2.6.17-10-something) ...will it boot correctly this way, even with the power supply plugged in?  I haven't had a chance to try to -11 kernel on a dual-core laptop yet.

same problem. it just doesnt want to boot all the way up. it gets about half way, then stops loading

---

### Post by NOSintake on 2007-02-22
hmm, well, i just tried again on my friends charger (dell also), and it booted up. wierd. guess ill try once more back on my computer. but even if i could get i to boot up fully with the power in, shouldnt i be able to boot up with all my other usb's plugged in?

---

