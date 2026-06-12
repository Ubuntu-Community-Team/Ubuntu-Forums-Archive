---
title: "k3b causing dvd-burner to stop working"
date: 2007-09-08
forum: General Help
---

### Post by mwolfe on 2007-09-08
Alright i've been using k3b for a long time and its always worked great. Yesterday i tried to burn a data dvd and all the sudden my dvd wasnt recognized when i opened k3b and I got a message about not removing a device while it is in use (the message you'd get if you unplug a usb drive without ejecting/unmounting first)
I no longer could eject the disk so i restarted and then i could eject it (i'm referring to manually ejecting it by pressing the button)
When i booted back into ubuntu the disk worked fine and I could open and close the drive, that is, until i opened K3b again and it did the same thing.

So i tried gnomebaker and i was able to burn a dvd fine. I really don't like gnomebaker though as it seems to overrwrite dvdrw media and i like to append data to them (in k3b it only overwrites if there isnt enough free space left). Plus k3b as more features as well.

I'm not sure if there were any recent updates that may have broke k3b with my dvd burner, how can i check an update log or something like that?
Also, does anyone know of commands that may be able to get my drive back up and running without rebooting?? diagnosis is a b*tch when i have to reboot everytime.

Thanks

---

### Post by mwolfe on 2007-09-12
anyone at least know some commands i can type to get my cd rom back working? I know of lspci to get info on ide drives but nothing about how to load them.. Restarting works.. But thats it.

---

### Post by mwolfe on 2007-09-12
sorry, double post.

---

### Post by AllFather on 2007-09-16
Bump :p
got same problem.
dvd works perfectly, i burn something with k3b, it goes well, ejects cd.
but after that, dvdrom stop working, and computer needs to reboot to get it to work.

---

### Post by mwolfe on 2007-09-16
Hmm.. in my circumstance, just opening up k3b makes my dvd burner completely useless until after a reboot.. I've tried burning with gnomebaker and it works fine. I also tried brasero and it works for burning, but it burns really slow... That may be because i had burnproof on though, but it was going like 2x with 16x burner. Burning a dvd-rw with brasero went around 0.8x-1.1x so it took forever to burn. Gnomebaker burned at good speeds though.

Since my drive stopped working i looked into getting an upgraded firmware but there arent any for my drive. After searching i found that the model i have is the same as some BENQ drive that has updated firmware. So i cross flashed it to the BenQ drive and it still has the same problem with k3b even though it shows up as a benQ drive now, and works the same way with the other programs.

---

### Post by AllFather on 2007-09-18
Doesnt seem like many others have this problem, cause the thread aint getting much respons :p

---

### Post by mwolfe on 2007-09-18
yeah thats too bad. i'm  patiently waiting for others to start using their k3b program and have it stop working.. :p
I thought it was definitely a hardware issue at first but it doesnt seem to be since it works with gnomebaker and brasero.. i'm curious to try others and see if it works.. It also seems find for playing cd-roms/dvd-roms just fine.. I havent tried burning in windows yet but i'd guess that it works fine there also. 
I'm considering buying a new one just because this is annoying, but i'm not sure what the problem is. In october gutsy comes out (i believe) and possibly it will work again then.. so i'll wait before buying anything.

---

### Post by splintercellguy on 2007-09-18
Perhaps you should file a bug at Launchpad.

---

### Post by tszanon on 2007-09-18
> **mwolfe said:**
> anyone at least know some commands i can type to get my cd rom back working? I know of lspci to get info on ide drives but nothing about how to load them.. Restarting works.. But thats it.
Have you tried unmounting and remounting the disc? Supposing your DVD drive is /dev/hda:
```
sudo eject /dev/hda
```
or
```
sudo umount /dev/hda
```
Maybe then you'll be able to use the drive without rebooting.

---

### Post by henrik79 on 2007-09-22
I have exactly the same problem. Running Kubuntu and K3b 1.0.3.

---

### Post by ashurson on 2007-10-04
I have the same problem here on my feisty.
K3b takes a long time to start.. and dmesg shows these lines:

```
[ 3950.172000] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 3950.172000] ata2.00: cmd a0/01:00:00:00:00/00:00:00:00:00/a0 tag 0 cdb 0xac data 8 in
[ 3950.172000]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3950.172000] ata2: soft resetting port
[ 3950.492000] ATA: abnormal status 0x7F on port 0x00010177
[ 3950.492000] ATA: abnormal status 0x7F on port 0x00010177
[ 3950.496000] ata2.00: revalidation failed (errno=-2)
[ 3950.496000] ata2: failed to recover some devices, retrying in 5 secs
[ 3955.500000] ata2: soft resetting port
[ 3955.820000] ATA: abnormal status 0x7F on port 0x00010177
[ 3955.820000] ATA: abnormal status 0x7F on port 0x00010177
[ 3955.824000] ata2.00: revalidation failed (errno=-2)
[ 3955.824000] ata2: failed to recover some devices, retrying in 5 secs
[ 3960.828000] ata2: soft resetting port
[ 3961.148000] ATA: abnormal status 0x7F on port 0x00010177
[ 3961.152000] ATA: abnormal status 0x7F on port 0x00010177
[ 3961.160000] ata2.00: revalidation failed (errno=-2)
[ 3961.160000] ata2.00: disabled
[ 3961.664000] ata2: EH complete

```

After that dvd is disabled until reboot.

I'm pretty sure i have this problem since i did "apt-get dist-upgrade" about a month ago, and apt reinstalled kernel 2.6.20-16-generic, altough kernel 2.6.20-16-generic was already installed.. maybe initramfs was updated ?

At least I hope gutsy will solve this bug.

---

### Post by AllFather on 2007-10-06
"bump" 
anyone found a solution to this? :p

---

### Post by TransitMan on 2007-10-06
While researching for a solution to this problem, as I have been experiencing the same, I cannot find anything to solve this, except waiting for Gutsy to come out. Apparently there is a resolution in Gutsy that fixes the k3B killing DVD-R problem.
For now I am using Nero for Linux.

---

### Post by ashurson on 2007-10-07
I just tried Gutsy Beta and it seems that this bug has been solved.
I'm using kernel 2.6.22-13-generic.

Gutsy rocks! :guitar:

---

