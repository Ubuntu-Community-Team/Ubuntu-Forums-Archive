---
title: "two drives"
date: 2021-07-21
forum: General Help
---

### Post by oneleded on 2021-07-21
i got my Linux drive, and my other linux drive. so far they are not compatible. one is ssd, the other is hdd. remember before, i was trying to get two linux OS, on one drive. the ssd drive is working the other drive has puppy on it. i got lubuntu, an mint on the ssd drive, puppy aint as friendly. best i can remember tonight, it dont like UUID?. i also got REfind, but cant understand how it works yet. (too much going on)., an still havent read the books i got to understand linux. (just a bit, not enough), got the spirit though. always will. the ssd drive sees the hdd drive, just havent figured out how to connect. i read Rods Books sum, none has soaked in enough yet. thats where i got the ideal. guess i should keep reading. y'all know though i play golf, two minor strokes, two major ones. just hope i play on, an you too. //ed
i didnt say i appreciate all the help before, an i better quit writing, while i can..

---

### Post by TheFu on 2021-07-23
Is there a question?  If so, we need details about what you hope to achieve and the hardware.

Puppy has been replaced around here by a flash drive with Ubuntu-Mate on it that boots into a "Try Ubuntu" mode.  Anything can be fixed from that boot.  I've run for 5 days using *Try Ubuntu* mode when a HDD died and shipping of the replacement was slow.

I haven't dual booted in a long time.  Much prefer to use virtual machines to try out other releases.  Zero risk to my HDDs and data in doing that. No chance that a bad setup will accidentally wipe the main OS either. Virtual machines use virtual storage, which gets setup by us, usually as a big file.  The virtual machine cannot write outside that file and harm the main OS on the system, unless we do a number of manual steps to allow it.  I don't think it would be possible to cause harm to the main OS from inside a VM by accident, no matter what you do.

---

### Post by dragonfly41 on 2021-07-23
I will add a note in reply to your reference to ReFIND and Rod's Books.

I use ReFIND to choose booting between 1 internal HDD (Windows 10) and two external SSD's (Ubuntu and backup).

Install efibootmgr (instructions here .. [https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027](https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027))

    sudo apt install efibootmgr   

Now if your run efibootmgr you can change boot order.

You can also choose ReFIND from menu to boot up and you see the ReFIND GUI.

[COLOR=#FFFFFF]



[/COLOR]

---

### Post by oneleded on 2021-07-23
thanks, slow i am. i'll practice on phrasing a question. on the side, i havent had windows, since 2016..

---

### Post by oneleded on 2021-08-04
this post of mine was nonsense, so i changed it. no need to waste anybody else's time reading it.. trying out your suggestions, thanks.

---

### Post by oneleded on 2021-08-04
installing efi boot manager

---

### Post by oneleded on 2021-08-18
i have given this a lot of thought, and putting this, on only one drive, is different than two drives.. so the thread i posted, dont count for much. thanks to being patient while i figured this out.
the info i based this on was for only for one drive. my question was based on two drives. so it dont count quite yet. if not for this place, i would have never figured this out.

---

### Post by oneleded on 2021-08-22
just for kicks, i may have said this before, i dont have windows, an havent since 2016. so, i might be working from a different perspective. the last windows i had was xp, an i run it into the ground, even after it expired, an before i went total linux.  just a few years later, half a decade, im still here, an glad of it..

---

### Post by oneleded on 2021-09-06
time fly's by, an i got to mark this as solved, as i got to do more research, is my main problem. no need to leave this hanging. i thank ya all for the help ya have given me. an hope to report back soon.. for the thread gets locked..

---

