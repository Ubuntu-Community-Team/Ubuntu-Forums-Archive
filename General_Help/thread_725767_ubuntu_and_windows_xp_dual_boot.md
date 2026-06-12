---
title: "ubuntu and windows xp dual boot"
date: 2008-03-16
forum: General Help
---

### Post by -=Viper=- on 2008-03-16
ok so i cant use windows since i put ubuntu on my computer, i have 2 hard drives one with ubuntu and one with windows, pretty much all the guides ive seen are from windows to ubuntu dual boot not ubuntu to windows, can anyone give me a simple easy guide to fix this and make a dual boot?

---

### Post by pijits on 2008-03-16
What are your jumpers on the hard drives set to?

---

### Post by -=Viper=- on 2008-03-16
no idea, how do i tell?

---

### Post by pijits on 2008-03-16
should be a little plastic black or white thing that is in a certain spot on the back of the hard drive where the cables come out. Theres indicators of what is Primary and what is secondary and what is cable select. Usually the manufacturer has them set to Cable select. What operating system boots first?

---

### Post by -=Viper=- on 2008-03-16
ubuntu boots first. might as well give you the whole storey if it helps, ok  so my friend gave me a fedora 3 cd and said it came with a dual booter on it so windows would still work. anyways that night i install it to my 2nd hard disk and after i do all of it i restart my computer and i can boot windows, then i go back to fedora do some stuff try to go back to windows and then nether work. then another friend gave me a ubuntu 7.10 cd and i put that on there. yeah thats the storey, i have windows on my 1st hard disk but it wont boot, when i installed ubuntu i took out the first hard disk so i would accidently erase it, now when both are in nothing boots.

---

### Post by sandysandy on 2008-03-16
when u boot what are u getting.

r u getting GRUB.

if so, do u get choices for Ubuntu, fedora , windows

if not, what do u get at boot

regards

---

### Post by pijits on 2008-03-16
By the sounds of it there may be a jumper conflict but we'll try something. If your in Ubuntu right now enter in ```
sudo fdisk -l
``` you should see all of your hard drives there. 
Next open up your grub menu through ```
sudo gedit /boot/grub/menu.lst
``` near the bottom it will say the root or where the hd is. Usually Linux will assign itself as hd0. 

```
title           Microsoft Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```
is how it appears in mine. you could try copying it and seeing if it works.
I got most of what i know from [HTML]http://ubuntuguide.org/wiki/Ubuntu:Feisty#Boot_Menu[/HTML]
It could help

---

### Post by zxscooby on 2008-03-16
ok , sounds like when you installed fedora you set up a dual boot , with grub i presume.
im not sure if grub is installed with ferora.
That removed your windows boot loader and replaced it with grub
Then when you installed ubuntu your first hdd was removed so grub was written to your 
second hdd. now that your first hdd is replaced your computer is trying to boot from the windows drive again and the boot loader on that drive is looking for boot information that 
has changed or is no longer there. 
its possible that you can reinstall grub completely, with the windows hdd installed and things will be corrected. 
it is also possible that you have a cable that is not plugged in properly, or a drive that has failed.  
first ,check the bios to see if both drives are detected properly.
then if everything is ok you can use your ubuntu cd to reinstall grub. 
you can also set your bios to boot from the ubuntu drive first , but you will still not have windows unless you correct the grub menu.

---

### Post by Lantesh on 2008-03-16
As others have already said you have to fix your Grub menu.  Of course since you did some hard drive disconnecting and reconnecting I'm not sure what master boot record your Bios is even trying to read at this point.  In any case if all of this seems pretty daunting, and you are not sure what direction to go there is another alternative.  Do a Google search for "Super Grub Disk".  Follow the instruction you see on the guys website on how to make a super grub disk which is a bootable CD that give you boot options.  You can boot any valid Linux or Windows install on any hard drive from the CD, and it gives you Grub repair options.

---

### Post by Mustard on 2008-03-16
So which OS is on the master drive and which is on the slave?

---

