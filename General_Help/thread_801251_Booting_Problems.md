---
title: "Booting Problems"
date: 2008-05-20
forum: General Help
---

### Post by Lexus Dominus on 2008-05-20
slightly off-linux talk, but basically my computer wont boot up at all. no signal to the monitor, no input from the keyboard or mouse. there are not even any beeps. i get the impression that the bios is failing to start. there's defineltly power to everything & ive tried taking out the cpu, ram, HD, etc with no avail. ive also tried resetting cmos, but still nothing. i checked the motherboard for damage and it all seems fine. 

interestingly the same thing happened a couple of months ago, and after a few tries, it booted up. i chceked the memory & stuff & everything seemed normal & working properly. im out of ideas & i dont really want to go spending money on new hardware if i can help it.
thanks

---

### Post by ibuclaw on 2008-05-20
First I'd check for battery fluid on the motherboard batteries, then I'd test for CPU overheating.

Make sure all fans are functional, etc.

Make sure all motherboard power supply is nice and firmly in (That is both A, the 24-Pin and B, the 4-pin that goes in right next to the fan).

If you get past that with nothing, take out all RAM sticks apart from one, and test it in all RAM slots.

Also, depending on how old your hardware is, sometimes in Motherboards you get an LED light that tells you that everything is setup right and OK to go.
When you connect everything up, turn the power on at the wall (plug/socket, not the actual PC) and check for a light that may be turned on (or off as the case may be) in the motherboard.

If you haven't got one, don't worry about it...

Also, strip out everything except the bare bone neccessities (Motherboard, CPU, CPU Fan, 1 RAM Stick, Monitor connected to Onboard Graphics Port, Power Supply).

If you still get the same error, it's either one of the remaining hardware is failing or the Motherboard has failed altogether.

If you Motherboard has failed, one can only ask "What sort of area do you live in? Is your PC protected with a Surge Protector?"

Although, try booting with an alternate power supply before jumping to that conclusion...

Regards
Iain

---

### Post by jimv on 2008-05-20
Unplug your drives and graphics card and any other addon cards from the machine and try to boot.  You should get 1 post beep if it's working.  If you get the beep, then something is wrong with one of those things you unplugged.  Plug them in one at a time until the problem occurs.

If not, turn the machine back off and pull out the RAM.  You should get a long series of beeps (that means that there's no RAM) if the motherboard and processor are working.  If that's the case, then your RAM is bad, and you should replace it.

If it's still not working, I'd think that it's either the power supply or the motherboard, and I'd replace the power supply first, since they tend to go out a lot.  Or if you have a second power supply, you could try swapping them.

---

### Post by signseeker on 2008-05-20
Could well be a power supply issue.

---

### Post by Lexus Dominus on 2008-05-20
Ive checked all the power etc its all plugged in properly & i am using a surge protector. My PSU is less than 6 months old so i cant imagine any problems there. i think its a problem with my motherboard or processor. is there any way of finding out which? 

Its really strange though.. if its physical damage i dont get how it could have fixed itself last time.

---

### Post by signseeker on 2008-05-20
If you have another computer handy then try using that power supply - if it works then it's your power supply.

If it doesn't work, try using the suspect power supply to start up the other computer - if it works - your power supply is definitely in the clear.

With regards to ur power supply being only 6 months old - hardware can still fail :) Better that it fails while it's under warranty.

Good luck

---

### Post by lisati on 2008-05-20
> **Lexus Dominus said:**
> Ive checked all the power etc its all plugged in properly & i am using a surge protector. My PSU is less than 6 months old so i cant imagine any problems there. i think its a problem with my motherboard or processor. is there any way of finding out which? 

Its really strange though.. if its physical damage i dont get how it could have fixed itself last time.

Sometimes it's "wonky" connections. I'm not sure from what I've read in this thread if you've tried unplugging completely then replugging firmly.

---

### Post by Lexus Dominus on 2008-05-21
Wow, after fiddling with my processor, it actually booted up. then, shut itself off presumably because of the cpu temperature. so, after fiddling a bit more, it booted up again, and here i am on ubuntu(it took a few more attempts at booting before it finally worked). i can tell its going to happen again if i switch it off. is there any way i can  maybe diagnose the problem? thanks for all your help by the way :) im happy now. i may just leave it switched on and looking like a mess all over my floor forever.

just looking at my system now.. all my memory is fine, both cpu's are active and at 1-2%, temperature is 45 c, rams all fine ect and the rest of the boot happened normally.

My specs:
Gigabyte GA 8i915 g Pro (dual BIOS)
P4 dual core 3.4 ghz
1 gb ddr ram
ati sapphire radeon x300se

---

