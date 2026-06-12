---
title: "Dual Booting Ubuntu And RHEL"
date: 2007-10-28
forum: General Help
---

### Post by alok_mishra_4 on 2007-10-28
Ok everyone,this is a bit complex case i've got here! (Atleast considering the time to read this post) :)

I have two hard drives of 40 gbs each on my system.
I've got ubuntu feisty on my hard disk no.2. In order to use a part of my 1st hard disk,i mounted 20 gigs of hard disk 1 onto /opt during ubuntu installation.

So,last night,i installed RHEL 4 on the remaining 20 gigs left on my 1st hard disk.During installation,it failed to recognise the entire second hard disk which had ubuntu(dunno why!!).
Anyways i installed it on the remaining 20 gigs by splitting them as:
/boot   100 mb
/           Approx 19.9 gb(i.e. remaining)
As i feared using the grub which comes with red hat,i selected the option of not installing RHEL grub (As it had failed to see my hdb containing ubuntu during setup).
Now my hard disk partitions looks like:
Hard Drive 1:                                                         
HP Diagnostics 30 mb(Cant remove that!)
/                         19 gb
/boot                   100 mb
/opt                     20 gb(that is /opt in ubuntu) 

Hard Drive 2: (ubuntu)
/boot                 100 mb
/                         39.9 gb
                    
Then after installation,i edited grub menu.lst in ubuntu as follows:
(The kernel basically in my case is the uuid of the /boot partition of RHEL which i found)

title		Red Hat RHEL	
 root		(hd0,2)
 kernel	/vmlinuz-2.6.9-5.EL root=UUID=d83c184c-1652-419b-a4da-665cbe8b0784 ro quiet splash vga=791
 initrd /initrd-2.6.9-5.EL.img

Then came the terror when things stopped moving beyond! I can boot into ubuntu fine.
but whenever i select the rhel at boot,it gives me the following error,and then i've to reboot again:

audit(1193581007.952:0): initialized
Red Hat nash version 4.1.18 starting
mount: error 6 mounting ext3
mount: error 2 mounting none
Switching to root
switchroot: mount failed: 22
umount /intrd/dev failed: 2
Kernel panic -not syncing:Attempted to kill init!



Now i also placed links to intrd and vmlinuz in the /boot to the  / of RHEL by mounting them using ubuntu to make sure that it finds the path.In fact i've tried a lot of permutations with my grub,but each time i get this exact error.:confused:
So,basically i cant get into Red Hat Enterprise Linux.
So,can anyone give any ideas here? I think if someone can figure out what exactly this error message means,then probably i can see some light!

---

