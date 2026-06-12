---
title: "Computer bricked after hibernate"
date: 2014-10-01
forum: General Help
---

### Post by mcdickson101 on 2014-10-01
I've got a Gigabyte Z68AP-D3 motherboard, GeForce GTX 460 and an i5 processor. 

I recently installed Ubuntu alongside my Windows 7. Everything seemed to working well until I pressed hibernate within Ubuntu. 

When I got home a couple of hours later, I attempted to resume my computer but it wasn't having any of it. The light on my CPU fan seemed to flicker (and possibly turn off) but then nothing happened.

Naturally I assumed that I would simply have to perform a hard shutdown and everything would work afterwards. Apparently not the case. Now when I turn on my computer, it seems to load up and makes all the relevant noises, but my monitor doesn't seem to react. It's like the graphics card has stopped outputting anything for the screen to process. 

The fun part of all of this is that sometimes when I turn the computer on, both fans flicker and then turn off. After about a second they both turn back on again. This makes me feel like there might be something wrong with the power supply. 

Please let me know if you have any ideas or diagnoses I can run to try to work out what's wrong here. Honestly I'm stumped.

---

### Post by ajgreeny on 2014-10-01
Hibernate is disabled in Ubuntu by default so unless you enabled it yourself it will not work for you.  However that should not affect rebooting of the computer in any way.

It sounds more like a coincidence to me but it may be worth booting to a live DVD/USB, assuming you can and it's not the power supply at fault, and then running a disk check on your Ubuntu root partition with command ```
sudo e2fsck /dev/sdx#
```where sdx# is that root partition.

I presume you are not even getting to the grub menu, which you have always done previously, which does point to the problem not being specifically Ubuntu, but rather some hardware failure.

---

### Post by sotiris2 on 2014-10-01
This must be some kind of a hardware problem. When you say it makes the relevant noises, did your pc *beep* (once) when booting successfuly? Does it now? If it is beating in anything more than one beep it's some kind of error code you can look up in your motherboard's manual.

That said to troubleshoot it I would:
Remove power totally for a few minutes.
Clear CMOS (check you motherboard manual if unsure)
Strip the pc to the minimum components ( 1 ram stick , no pci cards, no hard drives / dvd..) and try to boot after making sure everything is connected securely. 

If your i5 has integrated graphics I would also remove the geforce and try the integrated ones.

---

