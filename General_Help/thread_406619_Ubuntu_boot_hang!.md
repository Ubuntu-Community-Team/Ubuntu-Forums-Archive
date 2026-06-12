---
title: "Ubuntu boot hang!"
date: 2007-04-11
forum: General Help
---

### Post by davbren on 2007-04-11
Hi, I know there have been many threads about this but I don't seem to have found a solution. I've tried putting acpi=off acpi=force in the boot list thingy and neither help.

My pc is a AMD Athlon 64 3500+, 2 gigs ram, Audigy 2ZS, I also have wireless card. Its a texas instruments thing. I've heard the wireless cards cause alot of trouble for linux, there has to be a solution...

---

### Post by cantormath on 2007-04-11
have you tried the alternative cd?

---

### Post by davbren on 2007-04-11
How would that help a current installation? I have ubuntu installed, its just now that it hangs.

---

### Post by cantormath on 2007-04-11
where does it hang?

---

### Post by davbren on 2007-04-11
Right at the beginning of the boot, the progress bar doesn't even look like it wants to move.

---

### Post by sujith_m82 on 2007-04-12
Edit /boot/grub/menu.1st  - Add 'debug' option to the kernel and you can see exactly where it hangs.
Also, remove the 'splash' and 'quiet' option in the kernel entry.

Example :

kernel  /vmlinuz-2.6.20-12-generic root=UUID=21725820....<snipped>  ro debug

---

### Post by davbren on 2007-04-12
It gets stuck on "ohci_hcd 0000 :00 :1c.0: new bus registered, assigned bus number 1"

---

### Post by sujith_m82 on 2007-04-12
Try adding "noapic" and "noacpi" to the kernel boot parameters and see if it works.

---

### Post by davbren on 2007-04-12
Yh i tried that before, I found out it didn't like my external hard drive so I unplugged it and everything is good :) 

Well almost everything, Now in grub there is no windows option, it just sorta got rid of it. How do I get it back?

---

### Post by sujith_m82 on 2007-04-12
You should add something like this to your /boot/grub/grub.conf :

title Windows
    root (hd0,1)      # assuming that windows is installed on 2nd paritition 
    chainloader +1

(hd0,1) means the 1st hard disk, 2 partition.
To list the partitions on your machine, you can use 
"fdisk -l" if you are root,
"sudo fdisk -l" if an ordinary user.

---

### Post by davbren on 2007-04-12
i did the fdisk thingy and it says

"   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14592   117210208+   7  HPFS/NTFS
"

thats the windows one, so would it be hdb1? not hd0,0??

---

### Post by sujith_m82 on 2007-04-12
Hmm .. it would be root(hd1,0)
Can you post the entire output of fdisk -l ?

---

### Post by sujith_m82 on 2007-04-12
And the current contents of /boot/grub/menu.1st ...

---

### Post by ububaba on 2007-04-12
> **sujith_m82 said:**
> Edit /boot/grub/menu.1st  - Add 'debug' option to the kernel and you can see exactly where it hangs.
Also, remove the 'splash' and 'quiet' option in the kernel entry.

Example :

kernel  /vmlinuz-2.6.20-12-generic root=UUID=21725820....<snipped>  ro debug
Sujith,
I did remove 'splash' and 'quiet' by replacing it with 'debug'. At the next reboot A lot of text rolled 
down rapidly on the black screen. However, it stopped at [COLOR="Red"]Running local boot scripts (/etc/rc.local).
[/COLOR] It may mean something to you, but not to me. Can you please explain what has to be the next step. :( 

Thanks.

---

### Post by phossa on 2007-04-14
hi inicialy, i'm brasilian and english are terible.

so, i've a Asus m2n4-SLI with Ax2 3800, and i cant boot when use live cd.
i try add noapic in the code of boot in kernel line, only sometimes the bar under ubuntu name move. how i can do it one time.. ? thanks.

---

