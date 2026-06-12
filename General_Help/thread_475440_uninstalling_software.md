---
title: "uninstalling software"
date: 2007-06-16
forum: General Help
---

### Post by edat34 on 2007-06-16
I would like to know how i go about removing ubuntu and reinstalling my windows software.

is there anyone who can help me?

---

### Post by edat34 on 2007-06-16
Is there anyone that can help me? please :(

---

### Post by bigken on 2007-06-16
boot from the windows xp cd

---

### Post by edat34 on 2007-06-16
I did that and it still boots back up to this.

---

### Post by bigken on 2007-06-16
go into your bios and select cdrom as 1st boot device

---

### Post by edat34 on 2007-06-16
bigken, I changed it to boot from the cdrom. it still boots back up to the ubuntu login. i even tried running the restore cd and it tells me that i need to run fdisk.

---

### Post by bigken on 2007-06-16
download gparted live cd and format the hdd

---

### Post by edat34 on 2007-06-16
when i boot up the cd, do i select auto config?

---

### Post by bigken on 2007-06-16
ye just say yes to everything

---

### Post by edat34 on 2007-06-16
thank you for ur help.

---

### Post by edat34 on 2007-06-16
it gave me a couple of warning: never mount anything on /mnt! it would freeze the sys. use mkdir /mnt/mydirand mount on /mnt/mydir instead.

x.org: you need graphical enviro to start gparted. the enviroment config should have been done automaticaly. unfortunately it did not, since you are back to the bash!

so please run forcevideo script, and you will be asked for video driver, and res.
vesa driver should always work, and 1024x768 res too. if needed, you can kill x by using ctrl+alt+bkspace combo. what does all that mean?

---

### Post by bigken on 2007-06-16
ok its telling you to select your video driver just select vesa

---

### Post by edat34 on 2007-06-16
at the bottom of the screen it has gparted~# and a blinking box. i typed vesa and it gave me, bash:vesa:command not found.

---

### Post by bigken on 2007-06-16
na you should get gui interface

---

### Post by bigken on 2007-06-16
try this at the prompt **forcevideo script**

---

### Post by bigken on 2007-06-16
I cant understand why you cant boot from your system discs ?

---

### Post by bigken on 2007-06-16
what is the make and model of your pc you may have press something like F10 to boot from the restore disc

---

### Post by edat34 on 2007-06-16
its a hp xt914. i rebooted and im at a screen where it is asking me for the keymap.

---

### Post by edat34 on 2007-06-16
as far as my restore disk, in the past all i had to do was boot the pc from the disk.

---

### Post by bigken on 2007-06-16
40 for uk i think

---

### Post by bigken on 2007-06-16
you could also try booting from the ubuntu live disc and run gparted from there unmount the partitions and delete them

---

### Post by edat34 on 2007-06-16
this may sound stupid but im in the us, does that matter?

---

### Post by bigken on 2007-06-16
no lol

---

### Post by bigken on 2007-06-16
ok look at your bios screen and if it has option to select boot device ie by pressing F8 or something

---

### Post by edat34 on 2007-06-16
if i run fdisk it gives me the option to unmount and delete. if i run the ubuntu live cd how do i get to gparted? also at the beginning of the err msg it tells me available console tools: vim, partimage, testdisk, mc,  ntfs-3g- mount the disk ntfs-3g /dev/hda1 /mnt.windows.

---

### Post by edat34 on 2007-06-16
no,  there is no f anything to select boot device

---

### Post by bigken on 2007-06-16
well just run fdisk what this does it returns your hdd back to a raw state ie unformated 
no partitions

---

### Post by bigken on 2007-06-16
on the live ubuntu disc you go to sytem/administration gnome partition editor

---

### Post by edat34 on 2007-06-16
at my fdisk options it give me these options 1 create dos part or log dos dr.2 set active part 3 delete part or logi dos drive 4 display part info

---

### Post by bigken on 2007-06-16
3 delete 

then its 1 & 1

---

### Post by edat34 on 2007-06-16
i went ahead and went back into the ubuntu disk and then to gparted. in the partition box i deleted two of them the first 1 is locked.

---

### Post by bigken on 2007-06-16
unmount it

---

### Post by edat34 on 2007-06-16
it says i cannot unmount it. that most likely other partitions are also mounted on these mountpoints. you are advised to unmount them manually

---

### Post by bigken on 2007-06-16
just use fdisk its very easy

---

### Post by edat34 on 2007-06-16
will do.

---

### Post by edat34 on 2007-06-16
they are all deleted, what do i do next? create dos part or logical dos drive?

---

### Post by bigken on 2007-06-16
logical

---

