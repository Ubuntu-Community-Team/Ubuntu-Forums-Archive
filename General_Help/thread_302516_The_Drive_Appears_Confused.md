---
title: "The Drive Appears Confused"
date: 2006-11-18
forum: General Help
---

### Post by daynah on 2006-11-18
My dad would like to start using Ubuntu, so I got my fancy shipped version of Ubuntu 6.06LTS and popped in the cd...

And his drive got confused and nobody cared :(

It was something like The drive appears confused (and it said it over and over again) and then on one like "nobody cares."

Any help? We're planning on installing it over Thanksgiving break!

(p.s. I was quite embarrased. Please help. I really want dad to switch. :( )

---

### Post by koenn on 2006-11-18
the drive said it was confused ?

---

### Post by bettlebrox on 2006-11-18
I'm confused? Not sure what you mean?

What happens when you boot from the Ubuntu CD?

---

### Post by daynah on 2006-11-20
Sorry I wasn't clear. I booted to the Dapper liveCD (it works on other computers just fine) and it made it to choose whether to actually start the live cd or do memtest or the other choices. I chose to start ot install ubuntu and then it showed the image of ubuntu, and stalled on the second option (I forget what it was). Then that went away as it when to terminal, and it said, "The drive appears confused." over and over again and then it said "nobody cares."

It was kinda funny in a sad way...

---

### Post by Termi11 on 2006-11-25
I have the same problem with Version 6.10 and an Asus Mainboard (P4 Dual core)
Lite-on DVD-R

---

### Post by johnny.greeley on 2006-11-25
I had the same problem, not only with Ubuntu 6.06 and 6.10 but with OpenSUSE 10.1, Knoppix 5.01, PCLinuxOS 0.93a. In all cases I was trying to boot a liveCD/DVD.

It appears all distributions begin booting the kernel fine, but there is a problem when the filesystem tries to be mounted off of the CD/DVD. It mounts all my hard drives successfully and claims to mount my DVD drive successfully but then balks when it trys to mount the filesystem and claims the cdrom appears confused. When the various distros try to dump me to a limited kernel I get some IRQ failure message and "no one cares."

I have the TDKRW1280B and a Asus P5P800 SE motherboard. I updated the firmware on the TDK and it didn't change anything.

---

### Post by daynah on 2006-11-30
Well I think we have our problem because I know my dad has an Asus, he's quite proud of it (I don't know what model though).

Is this a complete incompatibility with Asus motherboards or is there some kind of firmware that comes with these motherboards that can be changed if someone really wanted linux?

BTW, great troubleshooting, Johnny!

---

### Post by jmr on 2006-12-28
I've seen this myself yesterday on an Asus P5L-MX.  I found another [thread]("http://forum.freespire.org/showpost.php?p=29340&postcount=9") that suggests a simple BIOS reconfiguration:
> Try turning OFF the smart monitoring command for disks (magnetic, optical) in the bios of the machine...

I'll try it myself tomorrow.

Greetings,

João

---

### Post by jmr on 2006-12-29
Well, I tried disabling SMART monitoring in the BIOS and it didn't make any difference: I still get the "Drive Appears Confused" message.

However, I downloaded and applied the latest flash BIOS update (version 0301) for the P5L-MX and, after checking the BIOS configuration (SMART was on AUTO), the system (Ubuntu Linux 6.06.1 64bit) booted fine without any special options.

Hope this helps,

João

---

### Post by gendou on 2007-03-18
had the same problem with my asus mobo (p5ld2-vm) i changed the configuration of the ide devices to enhanced only in the sata devices.
now my ubuntu runs much much better...:lolflag:

---

### Post by masterodie on 2008-02-21
> **gendou said:**
> had the same problem with my asus mobo (p5ld2-vm) i changed the configuration of the ide devices to enhanced only in the sata devices.
now my ubuntu runs much much better...:lolflag:

I know this thread is damn old but man you saved my life ^^

---

