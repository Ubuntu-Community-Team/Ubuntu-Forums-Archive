---
title: "Monitor only working with one CPU.  (Both Edgy Eft.)"
date: 2007-02-02
forum: General Help
---

### Post by Sef on 2007-02-02
I have two CPUs and oneSamsung LCD monitor.   I want to switch from my older CPU to my newer CPU.  All is well with my older computer.  However, with my newer computer, I just get a black screen.   I took it to a shop, and on an cathod ray monitor, it works.  Yet back home, I just have the black screen.  Any ideas of what could be the problem?

Update:  Wondering if I changed something in the BIOS....does anyone know what I should check?

---

### Post by Sef on 2007-02-03
Bump.  Anyone?

---

### Post by Sef on 2007-02-05
Bump 2, anyone?

---

### Post by eXisor on 2007-02-05
Sef, perhaps a bit more info would help.

1) From your post, I'm reading that you have two boxes, A & B.

Box A is old CPU/Motherboard/Memory/VGA card

Box B is new CPU/Motherboard/Memory/VGA card

2) or, since you zone in on CPU as the changed factor, are you just replacing the CPU in box A? And what OS? If windows, does safe mode work?

Also, you ask about bios, so I'm reading that you are at least seeing the bios during startup?

The few times I've had the symptom you descibe, it had to do with the refresh rate set for the graphics card in windows (I was replacing VGA card A with B) and forgot to first set refresh rate to 60 before pulling the old card. In my case the system woke with the new card and loaded default (crummy) drivers, and then tried to set refresh rate to 85 since that's the value it had in the registry. The crummy drivers couldn't support that so I got the symption you describe.

---

### Post by Sef on 2007-02-05
> Also, you ask about bios, so I'm reading that you are at least seeing the bios during startup?

I'm seeing nothing at all.   

> The few times I've had the symptom you descibe, it had to do with the refresh rate set for the graphics card in windows (I was replacing VGA card A with B) and forgot to first set refresh rate to 60 before pulling the old card. In my case the system woke with the new card and loaded default (crummy) drivers, and then tried to set refresh rate to 85 since that's the value it had in the registry. The crummy drivers couldn't support that so I got the symption you describe.


It is just an on board video card.   Maybe I should just get one and see if that takes care of the problem.

---

### Post by eXisor on 2007-02-05
Still struggling to understand the setup.

New CPU in old box, or two completely different boxes?

If the m/b in question has been used before, it could be the bios settings are set to not use the internal vga card.  In this case you can remove the cmos battery for a few minutes and then put it back. That should reset m/b to factory defaults.

Or try another vga card. In any event it seems unlikely the CPU as anything to do with it.

---

### Post by Sef on 2007-02-05
> New CPU in old box, or two completely different boxes?

Two completely different boxes.   One box, the older one, works just fine.   The problem is with this newer box, which is about 3-4 years old, I was told.

> If the m/b in question has been used before, it could be the bios settings are set to not use the internal vga card. In this case you can remove the cmos battery for a few minutes and then put it back. That should reset m/b to factory defaults.

So I should just get another vga card?   If I take it to the shop, it will work on the tech's monitor, which is a cathod ray type.  However, on my LCD monitor, nothing shows up.

---

### Post by eXisor on 2007-02-05
Ok, I got the picture now. Hmmm, a tricky one.

So, to summarise, internal vga works fine with CRT, but not LCD. 

A few things to try (I hope your local techie is a buddy or really helpful):

1) see if a bios upgrade is available for the m/b
2) borrow a pci/agp (best m/b takes) VGA card and see if that works with the LCD
3) could be a LCD has a higher power requirement than an CRT? Borrow a newer PSU and see if that helps

In any event, I wouldn't spend a dime until i tried all the above to identify exactly where the gremlin lies.

---

### Post by Sef on 2007-02-05
Thanks for your input.   You have been helpful about this.

Let me back up a bit:

The person who gave this to me had bought a new computer because this one was virus infested.  I used Knoppix and a flash drive to remove his files from here with his monitor, and I had no problems.  

When I got it home, I found that Knoppix would boot up fine, but just before the desktop came up, it had a problem.  It would blink off and on a few times before coming up.  Eventually nothing would show up, and then after a reboot or two, it would show up.   Other distros also gave me problems.   I installed Edgy (with an LCD monitor) after I took it to the shop and had the tech check it out.   It worked fine with his CRT monitor, but then when I went to reboot it the next morning, the monitor showed nothing.  And it hasn't showed anything on my monitor since.

The monitor is a Samsung Sync Master 17".

---

### Post by eXisor on 2007-02-06
OK, scratch everyone I said so far. The symptom you now describe sounds like a vga card dying.

If it can't wake the Samsung at all now, will it still do a CRT? Best to test this.

I had a geforce TI card a few years back that started needing a few reboots before it could parlez voux monitor, and then it died.

From the sound of it, your onboard vga card is now caput.

---

### Post by Sef on 2007-02-06
Thank you.  I will check it out.  It did work a few days ago on the tech's CRT, but not on mine.

---

