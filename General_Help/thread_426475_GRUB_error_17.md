---
title: "GRUB error 17"
date: 2007-04-28
forum: General Help
---

### Post by otto888 on 2007-04-28
I Can't Boot! I Made A Ntfs Partion Out Of The Free Space On My Physical Hd that unbutu is on And I Rebooted And Got Grub Error 17. I Have To Use Wii For Stuff And I Don't Have A Live Cd (of Any But I Have 6.10 Installed I Think.)plz Help:( I have 1.5 of GRUB

---

### Post by otto888 on 2007-04-28
B.ump
U.p
M.y
C.ry
F.or
H.elp
PLZ HELP!
Typin on wii is a pain, my friend won't let me use his new vista pc cause LogMeIn is a beta 4 vista. I JUST WANTA GO BACK TO MY WORK!(amazingly)

---

### Post by confused57 on 2007-04-28
If you get the error 17 when trying to boot an entry in your grub menu, you might be able to get your Ubuntu to boot...if you don't even get the grub menu at boot, you'll definitely need a live cd to troubleshoot.

If you do get a grub boot menu, try highlighting your Ubuntu entry, press "e", then try changing the root from (hd0,0) to (hd0,1), then press "b" to boot.  Your Ubuntu partition number may have changed by adding another partition and you'll have to find the correct partition, by trying different combinations for your root entry.

---

### Post by elephant007 on 2007-04-28
I had the same issue once, I'm not dual booting and I ended up reinstalling Ubuntu.  Seems error 17 is indicating so sort of file structure failure... can anyone else verify this?

---

### Post by Josey on 2007-04-28
you need super grub disk or something like that.  It will be able to get you back up and running.

It's pretty simple really you just need to boot from the super grub disk floppy and then run a couple commands and you'll be back up and running.

Just a sec I'll get you links.

---

### Post by elephant007 on 2007-04-28
I did some research and found this [http://www.mepis.org/node/9283#comment-32716]("http://www.mepis.org/node/9283#comment-32716")

---

### Post by Josey on 2007-04-28
Make a floppy grub boot disk since you don't have a livecd.
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Then follow reinstall grub instructions here
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

I'll quote the page.
When you boot from the grub floppy you'll find yourself at the following prompt

```
grub>_
```

then run this command.

```
grub> find /boot/grub/stage1
```

you'll have something that looks like this
grub> find /boot/grub/stage1
   (hd0,1)
   (hd0,3)

Then use the output you see for the next command... in the example we use (hd0,1) but yours might be different depending upon the output of the first command.

```
grub> root (hd0,1)
```

and last

```
grub> setup (hd0)
```

Hopefully this is what you see from that command...
> grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd0,1)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.


This fixed my error 17... basically this finds your old grub list and reinstalls it.

---

### Post by otto888 on 2007-04-28
> **confused57 said:**
> If you get the error 17 when trying to boot an entry in your grub menu, you might be able to get your Ubuntu to boot...if you don't even get the grub menu at boot, you'll definitely need a live cd to troubleshoot.

If you do get a grub boot menu, try highlighting your Ubuntu entry, press "e", then try changing the root from (hd0,0) to (hd0,1), then press "b" to boot.  Your Ubuntu partition number may have changed by adding another partition and you'll have to find the correct partition, by trying different combinations for your root entry.

I get it when it loads. no os select. If I barrow Vista from my friend and use VistaBootPRO to load the windows xp and - loader,will it work and is it leagle to?

---

### Post by confused57 on 2007-04-28
I doubt if the Vista BootPro will repair your mbr(you could try, I suppose), you'd need a Window's XP install cd...here's a guide for restoring your Window's IPL code to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

It'll involve booting the XP install cd, press "r" for recovery, & entering FIXMBR, to repair your mbr.

The Super Grub Disk is a great tool, as was mentioned earlier...maybe you could download & make a copy on your friend's pc.  It's a very small download, only a few Mb's...just use their cd burning software to burn the iso as an "image", not as a data cd, burn at a low speed(8x or less)...you could use an old cd-rw that you have lying around.

---

### Post by m.musashi on 2007-04-29
> **otto888 said:**
> I Made A Ntfs Partion Out Of The Free Space On My Physical Hd that unbutu is on
That is most likely the cause of the problem. If the partitions changed then your boot files are on a different partition (well a differently named partition). The fix it pretty easy but it does require a live CD. If you installed 6.10 then the CD you installed from is the live CD you can boot from to fix it. Super grub disk is also useful for this but personally I find it a bit clunky and not overly intuitive. A live CD seems nicer to work with (although kind of slow to boot). If you can find a live CD boot it and then open a terminal.

```
sudo grub
find /boot/grub/stage1
```
This will return something like this
```
(hd0,5)
```
with the first number referring to the drive number (0 is the first) and the second the partition counting from 0. Next type
```
root  (hd0,5)
setup (hd0)
quit
```
Change the 5 to match your situation.

This should fix the mbr to look on the right partition for the grub files and menu.lst. However, I don't know if this also fixes your menu.lst and it might be pointing to the wrong partition for the rest of the boot process. So before you reboot you will need to check/edit menu.lst.
```
sudo gedit /boot/grub/menu.lst
```
Find the line that looks like this
```
/boot/vmlinuz-2.6.17-11-generic root=/dev/sda6 ro quiet splash 
```
If instead of /dev/sda6 or similar you have a bunch of characters you are probably using the UUID stuff. I don't know how to recalculate that but it doesn't matter. Change it to look like the above but using the correct device name and partition number. However, if the files were on (hd0,5) the device name would be /dev/sda6 (or hda6 if you don't have SATA). If it is already correct then leave it. I'm just not sure if setting up grub also fixes this or not.

Hope that helps.

---

### Post by otto888 on 2007-04-29
i fixed it but i took off linux so....

---

### Post by confused57 on 2007-04-29
> **otto888 said:**
> i fixed it but i took off linux so....

Glad you at least were able to get Windows booted...now you can download the live cd, burn a copy, and reinstall Linux.  Anyone who has Linux installed and repartitions their hard drive afterwards really should have a copy of the live cd, for obvious reasons.

---

### Post by Josey on 2007-04-29
Because you didn't use the grub commands correct?

---

### Post by elephant007 on 2007-04-29
> **otto888 said:**
> i fixed it but i took off linux so....

That's not fixing it, that's working around it!!! HA HA
Fixing it would have been keeping everything intact and getting GRUB to boot...
At least you're not getting the error anymore

---

### Post by Josey on 2007-04-29
yeah i knew the linux install was in trouble after I told him how to fix it and then he's talking about "vista boot pro"

---

