---
title: "can't install Ubuntu can't boot from usb anymore"
date: 2018-01-15
forum: General Help
---

### Post by fattyz on 2018-01-15
I don't know how I did this.  It's confusing now with the new options in the bios.  I have Ubuntu installed on an old HDD I stuck in my new gaming rig, Dell Inspiron 7567 i5 gtx 1050 ti and now I can't load anything not even the live USB.  I had it working a couple times, last night I rekt by installing the Nvidia driver from additional software.  I knew I shouldn't have done that but figured I had lost everything anyway by that time so what's another re install?  I got an error during the last install that said "grub can't be installed on this device would I like to install it elsewhere?"  This device being the old HDD.  Now the live USB won't start anymore, Ubuntu starts loading then I get to a flashing cursor.  I tried all the options I could think of in Legacy and UEFI mode to get the live USB to start but no luck.  When the system reboots now I get a grub prompt unless I go in pressing F12 and select the SSD where windows is installed.  Only thing I can think of is make a new USB with the most recent Ubuntu release?  Maybe it's updated for these newer machines?  I always install compiz and gnome I never use Unity.  Any suggestions would be great as I am not really sure what to do next.  Thanks!

---

### Post by sidzen2 on 2018-01-16
I don't believe just replacing the SSD with a spinner hd without making changes to the BIOS/EFI/UEFI is advisable or workable, necessarily.

Recommend trashing the old hdd and get back to a SSD.  Another SSD for  linux would be ideal, but dual-booting present SSD is an option (after  shrinking C;\ with windoze and putting the sys backup on USB or DVD). Why would a spinny hd be desired for that machine, anyway?

"I just copy and paste commands into the terminal from the internet.  It either gets fixed or it stops working."  --kinda like a crap shoot!  See [Rute.]("http://people.virginia.edu/~rtg2t/samba/rute.linux.intro.pdf")

---

### Post by sudodus on 2018-01-16
> **fattyz said:**
> ... When the system reboots now I get a grub prompt unless I go in pressing F12 and select the SSD where windows is installed.  Only thing I can think of is make a new USB with the most recent Ubuntu release?  Maybe it's updated for these newer machines?  I always install compiz and gnome I never use Unity.  Any suggestions would be great as I am not really sure what to do next.  Thanks!

I think you wrote grub to your USB [pen?]drive (and overwrote the previous bootloader there). It is a good idea to create a new live system in your USB drive. You can try to re-install the system you tried before, or a newer version.

- **16.04 LTS** is so far the newest version with long time support.

- **17.10.1** 'artful dot one' is the newest version

- **'bionic'** is the developing version, that will bring the 'latest and greatest' (with the newest available hardware drivers). Try it but be prepared for a bumpy ride, because it is still being developed and things may break temporarily. See this link,

[Ubuntu Desktop amd64 testcases in Bionic Daily](http://iso.qa.ubuntu.com/qatracker/milestones/384/builds/164448/testcases)

[hr][/hr]
But in any case, you need the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) **nomodeset** and then after installation I *think* you should install an nvidia proprietary driver in order to take full advantage of your graphics card.

---

### Post by fattyz on 2018-01-16
Totally did not replace the SSD stuck the old HDD in.  Thanks for the lite reading and the jokes.

---

### Post by fattyz on 2018-01-16
Thanks, not really sure if that happened or not.  Sadly it worked more than once and then I crashed it doing updates then crashed it again installing the Nvidia driver.  The wireless was going to be the first project next was the graphics but now just getting it installed again would be ok.

---

### Post by fattyz on 2018-01-16
I guess my explaining of what I did was not very good based on the replys.  I had a laptop that failed eventually with a good working (except for the black screen bug which I got around somehow) Ubuntu 14.04.  I really liked it.  After a couple years I forget how I set everything up.  Anyway I spent a long time trying to figure out how to get that install onto a new computer but because of damage to the old computer and some suggestions I finally pulled the HDD out.  I got a new dell inspiron laptop with UEFI and SSD and Win 10 installed.  It has an available bay and cable so I just stuck the old HDD from the old Laptop into the new one, not really knowing how to do this or if its a great idea but based on what I could cobble to gether in my spare time from the web I wanted to try it.  I reboot and it just worked out of the box, after I switched to legacy boot.  After a while this failed and I would only be able to get to a grub prompt.  I researched that awhile and eventually found a switch in windows to shut off fast boot.  Grub worked again.  Then during the update process I decided to try the nvidia driver.  Big mistake.  Trying to come back from that everything just went south and I ended up not being able to boot even off the live USB.  But, I can go into the BIOS through F12 and select the SSD where win 10 is and boot fine into windows.  I've had a couple threads up already I know it's tricky on these machines.  It's 2 bad the newer hardware makes it so difficult.  

Thanks again.

---

### Post by sudodus on 2018-01-17
Thanks for explaining with more details :-)

After reading post #6, I would suggest that you stay away from proprietary nvidia drivers on this computer. I think you can get Ubuntu working again, at least if you make a fresh installation.

[hr][/hr]
There may be boot problems with Ubuntu after major updates of Windows (because it tampers with the UEFI boot system). So it is a good idea to backup everything important (to have some regular schedule or routine for backup).

---

### Post by fattyz on 2018-01-17
Made a new live USB 16.04.  Up and running again.  Seem to have the grub problem solved.  Wifi worked right away that's a real plus.

Thanks

---

