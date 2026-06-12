---
title: "removing dual boot"
date: 2008-06-09
forum: General Help
---

### Post by namsiuH on 2008-06-09
At the moment I have a Vista/Ubuntu (7.something)/Kubuntu(8.04) triple boot.

But since the wireless network card doesn't work in either Ubuntu or Kubuntu I want to delete both of them. I'll probably install one of them again if I can find the courage/time to tackle the broadcom-problem.

Ubuntu and Kubuntu are on the same 10Gb partition and I use the normal Grubloader.

Does anyone know how to delete Ubuntu and Kubuntu without Vista acting up?

Thanks in advance,
Tobias

---

### Post by trevelyan on 2008-06-09
here is how i would do it:

boot from the vista DVD

where it shows you the window that says "install now" there is a lil text link at the bottom left. it reads "repair your computer" click on it.

then it shows you the vista instalations you have (there should only be one of course)
select it and click next.

then it shows you the "system recovery options" window
click "startup repair"
what this does is that it looks for problems and fixes them.. it will replace GRUB with the vista bootloader.

after its done repairing you can click the "click here for diagnostics and repair details" if you wanna see what was done. the bootloader rapair should be at the bottom of the list of tests.

you can simply click finish now and your comp will boot into Vista.. now to get rid of Ubuntu and everything else... do this:

right click the computer icon on your desktop or your start menu

select manage

go to disk management (or something like that)

you'll see all the partitions and hard disks you have. including the ubuntu ones...

just select the ubuntu partition and format it.... and youre done. no more ubuntu.


sorry that youre going... i just started using ubuntu a couple of weeks ago.. and i love it. :D

---

### Post by Titan8990 on 2008-06-09
You can pick whatever method you like of deleting the partitions that contain the Linux OS. Personally I would boot to the Ubuntu live CD and reformat via fdisk.

Alright, so now you have deleted your Linux OS but still have a broken crap I mean Vista OS to fix. To reinstall the Vista bootloader follow these instructions (stop after step 2). [http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by Gannon8 on 2008-06-09
> **trevelyan said:**
> just select the ubuntu partition and format it.... and youre done. no more ubuntu.
That will make your computer unable to boot from the internal hard drive, because the MBR points to GRUB files that were on the partition.

---

### Post by trevelyan on 2008-06-09
> **Gannon8 said:**
> That will make your computer unable to boot from the internal hard drive, because the MBR points to GRUB files that were on the partition.

thats why we replace GRUB with the vista bootloader first.. dont be lazy.. read the whole thing ;)

---

### Post by Gannon8 on 2008-06-09
Oops...
I'm such a noob XD

---

### Post by jace001 on 2008-06-20
i need to remove ubuntu from my windows dual boot system but for a different reason...

my ubuntu system (hardy heron) seems to have upchucked into itself. i was updating the other night when it hung, i reset the machine, afterwards things got weird, and now it says that the OS has errors or something and it doesn't allow me to use it at its full functionality. I tried reinstalling by putting the installation Cd and booting from that (as i still want to keep XP and use ubuntu) but it just hangs again. i assume i'll have to take out linux completely first for reinstallation to work.

if info on my set-up helps, i'm currently running a 64 bit pc, with just one 300gig drive, partitioned into 5 drives (only one of which is dedicated for the ubuntu os). the os has updated thrice and it shows 3 different kernels (and recovery modes) plus the windows xp in the boot loader. i've previously edited grub so as it automatically highlights XP and boots it up after 30 seconds of leeway time, so that if my family every uses the pc it doesn't leave them scratching their heads wondering as to why they're faced with ubuntu instead of xp.

so now my questions are the following: 
1) if i don't edit my grub boot loader as it is now and instead reformat the linux partition (via disk management in xp) and try reinstalling, will it allow me to?
2) any other suggestions or thoughts? 

thanks a lot!

---

### Post by insuusvenerati on 2008-06-22
I'm a complete numb nuts at linux and the broadcom wireless fix wasn't that hard. :) Just do a search.

---

