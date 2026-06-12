---
title: "Ubuntu 7.10 Boot Error 17"
date: 2008-06-13
forum: General Help
---

### Post by nemesis93 on 2008-06-13
Alright so i just installed Ubuntu 7.10 using the alternate CD as i cannot install ubuntu using the LiveCD nor 8.04 hardy heron.

So i changed the bios to boot up directly from my EXTERNAL HDD and i get a black screen with this message:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17
_ (blinking underscore)

The keyboard nor mouse respond when i try to use them at this screen.

What should i do :confused:

Note: I just installed Ubuntu 7.10 to my External Seagate 250 GB HDD.

---

### Post by nemesis93 on 2008-06-13
No responses?!? Please help me!
1.5 weeks of pulling my hair and im starting to give up...

---

### Post by logos34 on 2008-06-13
This explains it better than I can:

[error 17]("http://users.bigpond.net.au/hermanzone/p15.htm#17")
(-->'In a computer with more than one hard disk'
-->'GRUB Command Line Interface method'
--> Device.map method)

---

### Post by meierfra. on 2008-06-13
Did you install grub to the external drive?

Get SuperGrub (see my signature) and use the "advanced solution" on this page:
[URL="http://www.supergrubdisk.org/wiki/Howto_Fix_Grub"]
http://www.supergrubdisk.org/wiki/Howto_Fix_Grub[/URL]

to install Grub to the MBR of the external drive.

---

### Post by nemesis93 on 2008-06-13
I think i installed grub to external hdd.

Now which is the external hdd??!

is it 
Natural
1        or
2       ???

---

### Post by meierfra. on 2008-06-13
Is is probably 2.   Just try 2, the next screen (I think) will let you pick the partition, if the Ubuntu partition is not listed, just go  back to the previous screen.

---

### Post by meierfra. on 2008-06-13
I just doubled check my answer.  It should be 2. But the rest of my last post is nonsense.

---

### Post by nemesis93 on 2008-06-14
So i tryed the SuperGRUB and i had no luck once again!
When i tryed it, it said Unable to recognize File system (something like that) 
:(

I cannot seem to install ubuntu to my computer! :cry:
Good night!!

---

### Post by nemesis93 on 2008-06-14
Alright so i finished installing Ubuntu 7.10 onto my HDD and still no luck.
After i change the bios to boot first from the External HDD it gives me Error 17.

GRUB Loading stage1.5

GRUB loading, please wait...
Error 17


The keyboard does not respond.

What can i do to get ubuntu to finally WORK?!? :(

---

### Post by rraj.be on 2008-06-14
Dont be panic.

Just do what i have mentioned below.

```
Boot into live cd.
```

Open terminal and type

```

sudo grub

find /boot/grub/stage1
```

If it returned like hd(x,y)

type 

```
root (x,y)

setup (x)

quit 

sudo reboot

```


this will solve.


may i know if further help required.

---

### Post by nemesis93 on 2008-06-14
Alright im going to try to use the LiveCD of 7.10.
Even though when i tryed to boot a demo from the LiveCD i could not even boot into that!
I will try 7.10 Live CD though.

I do not know why my system is pretty much 'linux proof'!
Anyways I will keep trying till i get tired of it..:)

---

### Post by meierfra. on 2008-06-14
rraj.be:  Please learn the proper grub syntax:

 	
> 
sudo grub

find /boot/grub/stage1

If it returned like [COLOR="Red"](hdx,y)[/COLOR]

type

root [COLOR="Red"](hdx,y)[/COLOR]

setup[COLOR="Red"] (hdx)[/COLOR]

quit 

sudo reboot



> 
this will solve.
Unlikely, since the OP already did the equivalent thing with SuperGrub. 
But it is worth a try.

---

### Post by rraj.be on 2008-06-14
:)

its very simple yar.:popcorn:

you just want time and patience to learn any thing in this  world.

---

### Post by meierfra. on 2008-06-14
If the Ubuntu Live CD does not boot, you might try ["PartedMagic"]("http://partedmagic.com/") or ["SystemRescue"]("http://www.sysresccd.org/Main_Page").

---

### Post by rraj.be on 2008-06-14
> **meierfra. said:**
> rraj.be:  Please learn the proper grub syntax

what you are telling is exactly correct with 8.04.

But the OP is going to use 7.10 live cd:):lolflag:

---

### Post by meierfra. on 2008-06-14
> But the OP is going to use 7.10 live

It is just as wrong with 7.10 live.

---

### Post by rraj.be on 2008-06-14
I am extremely sorry if i am wrong.

But its working for me like that with 7.10 and as you said for 8.04.

i dont know whats the problem.

i will correct if mine is mistake.

---

### Post by meierfra. on 2008-06-14
> But its working for me like that with 7.10 

This can't be  true. Please try it right now.

---

### Post by rraj.be on 2008-06-14
Its 100% TRUE.

I am a Guy who tweak windows and some security stuffs with that and i will reinstall that  at least once in two or three week's.

I have 2 SATA hard disks and i am frequently doing the same.

Its 100% and there is no  need for me to bit a lie.

---

### Post by meierfra. on 2008-06-14
Did you  try it right now?

---

### Post by meierfra. on 2008-06-14
I'm not accusing you have lying. I just think that you don't remember exactly how you did it.

---

### Post by rraj.be on 2008-06-14
No buddy, but i did yesterday.

Now i am in a bit busy that i cant log out.

But i am sure.

---

### Post by nemesis93 on 2008-06-15
How do i boot into Ubuntu 7.10 using the RescueCD?!?
I have it on an external hdd

---

### Post by meierfra. on 2008-06-15
> How do i boot into Ubuntu 7.10 using the RescueCD?!?


????? I'm not sure what you are asking.  What RescueCD? 
You can run reinstall grub (see post 12) from  just about any LiveCD.
SuperGrub is   best tool for trying to boot into Ubuntu.

But looking at your other threads it seems to me that you have a hardware problem and not a grub problem (although I really don't know anything about hardware.)

---

### Post by nemesis93 on 2008-06-15
I think i have a great idea!
Since i cannot run the LiveCD nor fix GRUB through the SuperGRUB CD cant i just run these commands using a Virtual Machine as Virtual Box??
My installation went smoothly and perfectly using virtual Box!!
If you have any suggestions please post!

Thank You.

---

### Post by meierfra. on 2008-06-15
You can run the commands with supergrub. Just press "c" at the first menu. (and skip the "sudo grub"). No idea whether it works in a virtual environment, just give it a try. But as I said, I don't think the commands will accomplish anything. 

You can also run the commands from other live CDs, like "SystemRescue" or "PartedMagic"

---

### Post by Mukilan on 2008-06-15
Hi Guys,

   I  had a external HDD USB  type , I was facing he same problem  grub error , clash in the boot system b/w ubuntu and windows . I found a  easiest solution by removing my internal HDD completely and installing ubuntu on extranl HDD so i got my grub in extrnal , when  i need windows , just disable extranl USB boot .It works great for me..

Mukilan S

---

