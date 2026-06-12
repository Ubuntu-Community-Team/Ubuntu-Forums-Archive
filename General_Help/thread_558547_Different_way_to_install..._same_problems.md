---
title: "Different way to install... same problems"
date: 2007-09-24
forum: General Help
---

### Post by DrSlump on 2007-09-24
Hi to all, it's about 1 year i try to install ubuntu on my pc, without success.

My PC:
Asus P5W DH Deluxe main board
G.Skill 2Gb ddr2 ram
Ati X1900XT 
Maxtor 320Gbyte Sata2 hd on ich7r controller
Seagate 40Gb Ata disk on Jmicron JMB36X controller
Optiarc AD7173A ATA dvd burner on ich7r ata controller

Windows XP pro and Vista Ultimate 64 Works flawless on this config.

The Problem:
During normal install (using the live cd or alternate cd), i get the infamous "TTY" error ad the busybox prompt, or error 21 with grub after reboot.

Using wubi, these are the results.
if i edit the kernel line with the irqpoll option, i get this result:
[http://farm2.static.flickr.com/1198/1432260520_2ecf4fe4a6.jpg?v=0](http://farm2.static.flickr.com/1198/1432260520_2ecf4fe4a6.jpg?v=0)

if i don't edit the kernel line andi let the system to start normally i get this result:
[http://farm2.static.flickr.com/1389/1432257330_e39da63405.jpg?v=0](http://farm2.static.flickr.com/1389/1432257330_e39da63405.jpg?v=0)

Nice, isn't it?
What's wrong with my pc? It's the most standard pc configuration on the world...i never had so much problems installing an os.

---

### Post by Mud.Knee.Havoc on 2007-09-24
I don't want to advertise for other forums, but there's [a post at another forum]("http://www.linuxquestions.org/questions/showthread.php?threadid=338856") that you can check - just don't forget to come back here after! :)

---

### Post by ago on 2007-09-24
Grub error 21 should be unrelated.
Most important is that it looks that there are some hardware incompatibilities particularly with com/irc. You first have to sort that out using standard LivCD and some appropriate boot parameters. It's difficult to say what may work for you. Usually new kernel versions tend to work better with this sort of things (that's by no means guaranteed, it only means that progress is quite fast). 

So you may want to try ubuntu gutsy or the new wubi version. If you still have issues, you should open a bug report.

---

### Post by DrSlump on 2007-09-24
Thankyou very much guys.
I've tryed the beta 5 of gutsy and there are no way to install ubuntu on my pc.
I'm still trying to install wubi, and i had success installing it on the ATA hd, but only if i use the irqpoll option pressing esc during grub execution.
Ubuntu starts very, very, very slowly, getting "ataX failed etc etc" error.
Even if ubuntu starts, it's still not supported the integrated usb2 wifi card, based on realtek RTL8187L chip.

How is it possible that the hardware i use, more than one year old, is still not supported??

---

### Post by 1234five on 2007-09-24
> **ago said:**
> 
So you may want to try ubuntu gutsy or the new wubi version. If you still have issues, you should open a bug report.

New Wubi version? If I go to wubi-installer.org there is still the older one... I want to try using the new one to see if that will work for me, so... I dunno...

---

### Post by ago on 2007-09-24
> **1234five said:**
> New Wubi version? If I go to wubi-installer.org there is still the older one... I want to try using the new one to see if that will work for me, so... I dunno...

[http://wubi-installer.org/devel/minefields](http://wubi-installer.org/devel/minefields)

Use only option 0 (use cd) or 1 (read only) since the others are not ready yet.

---

### Post by 1234five on 2007-09-24
Yeah, it said "could not retrieve some essential files"

---

### Post by ago on 2007-09-25
> **1234five said:**
> Yeah, it said "could not retrieve some essential files"

Can you redownload both? wubi and the ISO have been updated
In fact, try to burn the ISO and use Wubi with the CD inserted. Then you might be able to select any of the option.
Check the md5 of the disk first against the one published on the website [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by DrSlump on 2007-09-25
Hello to all, i've downloaded the 7.10 alfa version of wubi and, yes, the same problems.
I get errors with ata devices or "control turned off" with busybox.

---

### Post by 1234five on 2007-09-25
I re downloaded it but... still the same problem, "could not receive some essential files"

So I should burn the ISO to a disk and try again?

---

### Post by ago on 2007-09-26
Can you run wubi with "--debug" and see what is the relevant error? 
I guess 7zip

---

### Post by ago on 2007-09-26
can you also see if rev 309 makes any difference?

---

### Post by 1234five on 2007-09-26
> **ago said:**
> Can you run wubi with "--debug" and see what is the relevant error? 
I guess 7zip

Uh... so run "wubi--debug"?

---

### Post by piotrwoj on 2007-09-26
my english is very bad
1) Download and install systemrescuecd 0.3.8, latest stbale version, boot it
2) cd / and mkdir target
3) mount -t proc none /target/proc
4) mount --bind /dev /target/dev
5) chroot /target /bin/bash

If chrooting proces is OK  You can  configure Grub:

1) grub
2) device (hd0) /dev/disk  #kernel sysrescuecd has hda notation, kernel on ubuntu gutsy sda, this is no problem, UUID is important

3) root (hd0)
4) setup (hd0) or on an other partition (hd0,x) x- tab keys listing 0x83 partition
5) quit
6) update-grub
---------------------------------------------
[Drzwi Zewn&#281;trzne]("http://www.drzwi-warszawa.pl/") 
[Drzwi Antyw&#322;amaniowe]("http://www.domar.biz.pl/")

---

### Post by ago on 2007-09-26
> **1234five said:**
> Uh... so run "wubi--debug"?

wubi --debug
with a space in between

---

### Post by ago on 2007-09-26
Did you try rev 309?

---

### Post by DrSlump on 2007-09-26
Hello, i tried the latest beta version of gutsy and wubi: this time i get the error even if i use "irqpoll" option... :(


What's happening?

---

