---
title: "Ubuntu won't boot"
date: 2007-08-04
forum: General Help
---

### Post by tomtomhall on 2007-08-04
I installed the latest version of Wubi onto my computer, I reboot like it says and select Ubuntu from the boot screen. But after I choose Ubuntu my screen displays this message:

(hd0,1)
Filesystem type is ntfs, partition type 0x7
[Linux- bzImage, setup=0x1c00, size=0x1a82cc]
[Linux- initrd @ 0x1f04e000, 0x7918a5 bytes]

I'm guessing this a normal message but nothing happens after this, I can't enter any text, pressing the enter key makes no difference. I've waited like 30 minutes, no other message appears, it won't boot into Ubuntu and this is the 3rd install of Wubi. 

Please help !!!

---

### Post by tuxcantfly on 2007-08-04
> I'm guessing this a normal message but nothing happens after this, I can't enter any text, pressing the enter key makes no difference. I've waited like 30 minutes, no other message appears, it won't boot into Ubuntu and this is the 3rd install of Wubi.

Sounds like a bug with the Wubi bootloader (grldr). Does pressing Ctrl-Alt-F2 help you (any additional stuff displayed there)? Also, you might want to try doing a clean reinstall of Wubi, and before you reboot, open the file C:\wubi\boot\grub\menu.lst , locate every line that begins with "kernel" and isn't commented out (doesn't start with "#"); they're towards the end, and at the end of those lines, write in "acpi=off"

---

### Post by tuxcantfly on 2007-08-04
Also, another suggestion: if that didn't help, right after you select Ubuntu and it begins showing the initlal boot messages, start hammering away at the "ESC" button; it should get you into a menu. Press "c" there and it will get you to a command line. In there, enter:

```
root (hd0,1)
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso
initrd /wubi/boot/initrd
boot
```

And tell us if it prints out any messages.

---

### Post by tinybit on 2007-08-05
try grub4dos build as late as 2007-08-04, which can be downloaded from

[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

This build has fixed a bug about compressed NTFS volume.

---

### Post by tomtomhall on 2007-08-05
> **tuxcantfly said:**
> Sounds like a bug with the Wubi bootloader (grldr). Does pressing Ctrl-Alt-F2 help you (any additional stuff displayed there)? Also, you might want to try doing a clean reinstall of Wubi, and before you reboot, open the file C:\wubi\boot\grub\menu.lst , locate every line that begins with "kernel" and isn't commented out (doesn't start with "#"); they're towards the end, and at the end of those lines, write in "acpi=off"

Pressing ctrl+alt+f2 didn't do anything, I entered in "acpi=off" on every kernel line but the same message still appeared and Ubuntu still doesn't boot.

---

### Post by tomtomhall on 2007-08-05
> **tuxcantfly said:**
> Also, another suggestion: if that didn't help, right after you select Ubuntu and it begins showing the initlal boot messages, start hammering away at the "ESC" button; it should get you into a menu. Press "c" there and it will get you to a command line. In there, enter:

```
root (hd0,1)
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso
initrd /wubi/boot/initrd
boot
```

And tell us if it prints out any messages.

I managed to enter the code and it said "Filesystem type is ntfs, Partition type 0x7"

---

### Post by tomtomhall on 2007-08-05
> **tinybit said:**
> try grub4dos build as late as 2007-08-04, which can be downloaded from

[http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

This build has fixed a bug about compressed NTFS volume.

How do you install the latest build ?

---

### Post by tuxcantfly on 2007-08-05
> How do you install the latest build ?

Download the zipfile, unzip it, rename grldr to wubildr, place that into C:\ to replace the original wubildr, also copy over grldr.mbr as wubildr.mbr, then rename the file I attached from menu.lst.txt to menu.lst and place it into C:\

---

### Post by tomtomhall on 2007-08-05
> **tuxcantfly said:**
> Download the zipfile, unzip it, rename grldr to wubildr, place that into C:\ to replace the original wubildr, also copy over grldr.mbr as wubildr.mbr, then rename the file I attached from menu.lst.txt to menu.lst and place it into C:\

Did all that but got this error message:

Try (hd0,0): FAT32: NO GRLDR
Try (hd0,1): NTFS5: No grldr
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null

Error: Cannot find GRLDR in all devices. Pres Ctrl+Alt+Del to restart.

---

### Post by tuxcantfly on 2007-08-05
> Try (hd0,0): FAT32: NO GRLDR
Try (hd0,1): NTFS5: No grldr
Try (hd0,2): invalid or null
Try (hd0,3): invalid or null
Try (fd0): invalid or null

Error: Cannot find GRLDR in all devices. Pres Ctrl+Alt+Del to restart.

Oh wait never mind, those are the stock grldr builds not the Wubi ones, so don't rename the files to wubildr, just keep them as grldr and grldr.mbr place them into all your drives (C:\, D:\)  it should work

---

### Post by tomtomhall on 2007-08-05
> **tuxcantfly said:**
> Oh wait never mind, those are the stock grldr builds not the Wubi ones, so don't rename the files to wubildr, just keep them as grldr and grldr.mbr place them into all your drives (C:\, D:\)  it should work

I tried all that but now I'm back to the original error message:

(hd0,1)
Filesystem type is ntfs, partition type 0x7
[Linux- bzImage, setup=0x1c00, size=0x1a82cc]
[Linux- initrd @ 0x1f04e000, 0x7918a5 bytes]

:confused:

---

### Post by tuxcantfly on 2007-08-05
> I tried all that but now I'm back to the original error message:

(hd0,1)
Filesystem type is ntfs, partition type 0x7
[Linux- bzImage, setup=0x1c00, size=0x1a82cc]
[Linux- initrd @ 0x1f04e000, 0x7918a5 bytes]

Hmm seems like even the newer builds of grldr don't work on your computer, so installing using Wubi is going to be pretty tricky, so I think you'll just be easier off installing Ubuntu the normal way, using a CD.

---

### Post by tinybit on 2007-08-05
Another test may be done by placing /wubi/boot/linux and /wubi/boot/initrd in a non-NTFS volume and try to load and boot.

If it is OK, then we could know the problem is with NTFS code of grub4dos.

---

### Post by phreakxx on 2007-08-05
hey i have a similiar problem, its my first time booting ubuntu from wubi. well i did hear that the first time it goes thru a configuration... but i get the same thing but mine loads up to the USB stuff and it just stays there i also tryed waiting but nothing happens... on that note im also runing my drive on NTFS... but if it helps... at this point my keyboard wich is USB does not respond to any key strokes... and the lights are off ( caps lock, num pad, scroll lock) and well at this point i cant check if its a USB error because my only keyboard is USB.

ok so incase i got some of u lost in my randomeness my main points are...
1. same issuse on first boot
2. also runing harddrive on NTFS
3. stops at the part were it mentions USB

---

### Post by ago on 2007-08-06
> **phreakxx said:**
> 
3. stops at the part were it mentions USB

As a check, you can try to umplog the keyboard after reboot, the keyboard is not needed in that stage.

---

### Post by plante_ca on 2007-08-06
I have exactly the same problem...
I posted this morning on  Ubuntu-fr this message



Après 45 heures de Linux, j'ai un nouveau problème...  Ça allait si bien...
Hier soir, j'étais en train de lire le livre sur Ubuntu 7.04 à l'écran et essayais certaines choses dans le chapitre sur les utilitaires système et administration lorsque TOUT gèle....
Je ferme l'ordi et tente de redémarrer.
Rien à faire. Dans l'écran " Booting 'Ubuntu' "  après un bon départ rien ne se passe plus. (on verra plus bas ce que j'avais à l'écran).  Comme il n'y a pas encore de données importantes dans mon système, je décide de désinstaller avec sauvegardes et de retenter l'installation.
Rien à faire.  Je désinstalle TOUT et vide les fichiers restants dans la partition et réinstalle en allant encore chercher tout le kit (+ ou - une heure)
Je réinstalle sans succès. Voici le contenu de l'écran (commentaires en italique)...

Booting Ubuntu

(hd1,0)                       quelques écritures et l'écran revient comme ceci
File system type is ntfs, partition type 0x7
   [Linux-bzimage, setup=0x1c00,size=0x1a82cc]
   [Linux-initrd @ 0xif01e00, 0x7918a5 bytes]
Loading, please wait
NO RAID disks
[63.681143] sdb: assuming drive cache: write through
[63.682767] sdb: assuming drive cache: write through
            La, il y a un grand temps d'attente avant la suite de l'affichage, puis

     Check root = bootarg cat/proc/cdmline
     or missing module devices : cat/proc/modules ls /dev

Alert!  does not exist. Dropping to a shell!

Busy Box c1.1.3(Debian 1:1.1.3-3Ubuntu3) Build-in shell (ash)
Enter help 'help'  for a list of builtin command
/bin/sh: can't access tty : job control turned off
(inittramfs)

Evidemment si je fais Help , j'obtiens la liste des commandes possibles mais je ne sais plus quoi faire

Vous m'aidez?????????

If i wait enough i obtain the secand part ....
   check......


but i dont know what to do???

---

### Post by Kissablysoft on 2007-08-06
I have the same error message, except its in English. Need some help on this. Only difference in the two is that I am using on my old computer (an old OptiPlex GX1 with a P2 (400Mhz I think), I have tried to install with Xubantu, ubantu, Kubantu, always the same error. I am stuck on the "Loading, Please wait..." No RAID disks"  for like 5 minutes or so, then I get the rest of the error.
Help me figure this out!!!

---

### Post by plante_ca on 2007-08-06
for Tomtom... and Kissa...

I think i have found the answer. There is something wrong in the disk

I did   CHKDSK -f
 and I ahave my Ubuntu back after 2 reboot!

Look at the tread

[http://ubuntuforums.org/showthread.php?p=3128365](http://ubuntuforums.org/showthread.php?p=3128365)

tell us if it do the job....


Bye

---

### Post by plante_ca on 2007-08-06
iIn my case   it was 
CHKDSK L: -f
because I am using a partition of a disk USB on L: et M:

bye

---

### Post by nortzy on 2009-06-17
When i try to boot Ubuntu i get the message:
Error: Can't find grldr on all devices CTRL+ALT+DEL to restart

this is with wubi, and i tried renaming wubildr and wubildr.mbr to grldr and grldr.mbr but all that did was reboot computer when i select ubuntu.... what should i do?

---

