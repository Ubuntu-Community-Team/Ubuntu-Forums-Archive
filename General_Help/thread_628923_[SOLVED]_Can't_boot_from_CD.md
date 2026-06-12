---
title: "[SOLVED] Can't boot from CD"
date: 2007-12-01
forum: General Help
---

### Post by PeterH42 on 2007-12-01
Hi!

I recently installed ubuntu 7.10 on a tablet (acer c110 i think). for reasons beyond the scope of this thread, i need to re-install windows to make the tablet marketable (ebay anyone? :p).

I have tried with no sucess to boot from the windows recovery cd (starting into the bios and changing the boot order.. or just skipping the bios and selecting boot from cd)... whenever i try it just continues to load up grub and go into ubuntu :confused:

is there anyway to go about re-installing windows? (maybe some way to wipe the harddrive to eliminate grubs hi-jacking bootness?).

i'm not really familiar with linux/ubuntu so i haven't been able to figure this out.

thanks for any help!

( i know you guys just love windows on this forum :P)

---

### Post by Craigus on 2007-12-01
Grub cannot hijack the boot process. If the tablet isn't booting from the CD, it is either because there is something wrong with the CD, something wrong with the optical drive, or something wrong in the BIOS. Will any other machine boot the CD, and will the tablet boot any other CD ?

---

### Post by WarMonkey on 2007-12-01
Did you check your BIOS to make sure your CD drive is the first item in the boot order?

---

### Post by zipperback on 2007-12-01
> **PeterH42 said:**
> Hi!

I recently installed ubuntu 7.10 on a tablet (acer c110 i think). for reasons beyond the scope of this thread, i need to re-install windows to make the tablet marketable (ebay anyone? :p).



Ebay does not have a policy that says you have to install windows on your tablet in order to sell it.

Just install Ubuntu linux on it, and include a copy of the Linux installation media with the computer when you sell it.


> **PeterH42 said:**
> 
I have tried with no sucess to boot from the windows recovery cd (starting into the bios and changing the boot order.. or just skipping the bios and selecting boot from cd)... whenever i try it just continues to load up grub and go into ubuntu :confused:

is there anyway to go about re-installing windows? (maybe some way to wipe the harddrive to eliminate grubs hi-jacking bootness?).

i'm not really familiar with linux/ubuntu so i haven't been able to figure this out.

thanks for any help!

( i know you guys just love windows on this forum :P)


Move the CD drive in the boot order in your bios to be the primary boot hardware.

Insert your OS CD and boot it.

If the system isn't seeing your hardware, then it's probably NOT a grub loader issue.

If you want to install windows however, that is your choice.

Insert an Ubuntu Linux install cd and see if it will boot it. If it boots THAT but it doesn't boot the Window$ install cd, then you probably have a pirated copy of windows and you shouldn't be trying to install it anyway. OR... Your laptop is smart, and knows that it doesn't want window$ installed on it, and it is trying to tell you that, but you are not listening to it's VERY good suggestion.


In all seriousness though, just install Linux on the tablet and sell it as such.

---

### Post by PeterH42 on 2007-12-01
Okay... i'll try booting from a linux CD, but i can assure you my copy of windows is genuine (unless acer distributes pirated licenses of windows with it's computers? seriously, everyone thinks this when i tell them my problem, but it is the recovery disks, not a windows disk).

and yes, i thought i made it clear in my first post that i changed the boot order in the bios. (and i also tried another option my bios has of just selecting what to boot from).

"Your laptop is smart, and knows that it doesn't want window$ installed on it"
this really isn't a discussion about superiority of one OS over the other. so far i haven't been that impressed with ubuntu, it took ages to boot up on the tablet, and now it is hijacking my boot choice... i really wanted to like it (i hate Mac and M$)... but it's not helping me...

"In all seriousness though, just install Linux on the tablet and sell it as such."
I'm considering it but i have a feeling that it would lower the value... i'll give you the benifit of the doubt and assume you're not suggesting failing to mention the OS in the listing.

(giving them the windows/recovery disks wouldn't do any good either, since A) the average ebayer wouldn't be able to use it if it doesn't boot from BIOS and B) again i wouldn't "not mention it").

sorry if i come across as a jerk, i know that any help ya'll give me is straight out of your free time, i'm just getting a little frustrated with this and i feel like i just went to the doctor and he told me i'm not sick :(

---

### Post by Craigus on 2007-12-01
I don't think anyone thought ill of you. As I said though, this cannot be a grub issue, so you need to be looking elsewhere for the problem.

---

### Post by PeterH42 on 2007-12-01
okay, thought i don't really know where to look.

i tryed boot from the ubuntu cd (the one i used to install ubuntu on that machine), and it will not boot either.

i also tryed booting from the recovery disk on two seperate desktops... neither seemed to work (it went into stuff about a cd driver not being found)

the instructions for the recovery disk say to boot from it, but it's starting to seem like that's not the way they work :-/...

---

### Post by Craigus on 2007-12-01
Does it appear to be trying to boot from the CD - does the activity light come on at the right time ?

---

### Post by PeterH42 on 2007-12-01
no it doesn't... not even a flicker or a whir >_<

[edt] is there a way i  can reformat the hard drive from within ubuntu? (like the M$ DOS method)

---

### Post by Craigus on 2007-12-01
OK then - in the BIOS, is the optical drive showing as present ? (not in the boot order item, but in the actual list of drives present)

Is the optical drive working if you boot into linux ?

I know you've said as much, but are you really, really sure that the optical drive is the first boot device in BIOS ?

Edit: IF you really want to erase the drive, get Dban : [http://dban.sourceforge.net/]("http://dban.sourceforge.net/")

---

### Post by PeterH42 on 2007-12-01
well, the drive works if i boot into linux. (it's shown in the file system...etc)
and cd-rom it is at the top of the boot order in the BIOS (with the HDD at the bottom)
but i just realized that since it is a external cd-rom drive, it might not be recognized untill the OS boots up?

i am going to try using something like "wipedrive" (found in quick google) to just wipe the harddrive completely...

---

### Post by Craigus on 2007-12-01
Is it a USB external CD ? Is there a USB boot option in BIOS ?

---

### Post by PeterH42 on 2007-12-01
it is firewire, there isn't a usb option in the bios.

good news!

i didn't change a single thing and it worked this time! :confused:
(it booted as cd-rom)

i've been at this for days so i'm happy it worked and i'm not going to complain even if it made me look like a fool here :p...

uhh...thanks for the help...
:popcorn:

---

### Post by -grubby on 2007-12-01
you could mark it as solved, by going to your original post and then thread tools>mark as solved

---

### Post by PeterH42 on 2007-12-01
done. i'm so proud of myself for all the hard solving work i did =D>
^sarcastic alert^

---

