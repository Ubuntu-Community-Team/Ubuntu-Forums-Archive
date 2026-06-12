---
title: "dont boot"
date: 2007-07-31
forum: General Help
---

### Post by alnavegante on 2007-07-31
Windows vista. 
Intalled  wubi in a 20Gb disk (only for wubi, originally free ntfs). 
On boot appears this message: 

  " booting 'find/wubi/boot/grub/menu.lst' "

and the computer is freeze. 
some help, please?


p.d. very very nice project. Congratulations

---

### Post by ago on 2007-07-31
Is there a white space between "find" and "/wubi..."
what version are you using?

---

### Post by alnavegante on 2007-07-31
yes, there is a white space. And i have installed wubi on last Friday using the current version at home page.

If you need the exactly number version, please tell me where i can find it... i am take a look over the installation disk, but i cant find the number...


thanks

---

### Post by ago on 2007-07-31
it's the file name. You can also try the latest build:

[http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-234.72.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-234.72.exe)

---

### Post by alnavegante on 2007-07-31
i have tried... but obtain exactly de same message.


how i did...
1. run the new installer.
2. the installer detects de previos version and delete it.
3. reinstall automatically... very quickly.. i think that the installer use the existing ubuntu iso in the original installer folder.


more things? thanks

---

### Post by ago on 2007-07-31
Do you see any other message other than "find ..."?
Also press esc rapidly after you select ubuntu, you should get a sort of shell. Then type

find --set-root /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst

---

### Post by alnavegante on 2007-07-31
ok, i will prove this... but tonight, now i dont have time.
thanks

---

### Post by alnavegante on 2007-07-31
ok, press "esc" and appears some options, i select command-line  and wrote the first part: "find --root/wubi..."  and them my computer is freeze (i am waiting for 20 seconds... and its a x2 5200+  if something will happen must occur i this 20 seconds )...

more things? thanks

---

### Post by alnavegante on 2007-07-31
and there is no other message..

---

### Post by ago on 2007-07-31
> **alnavegante said:**
> ok, press "esc" and appears some options, i select command-line  and wrote the first part: "find --root/wubi..."

it's

find --set-root /wubi/boot/grub/menu.lst

you can also try to type

kernel (hd

then hit tab to show available options, select one of them and hit tab again, etc...

---

### Post by alnavegante on 2007-08-01
try to type:
 "kernel (hd" 
is this expresion correct?

---

### Post by alnavegante on 2007-08-01
"kernel (hd"

is this expresion correct??

---

### Post by ago on 2007-08-01
hit tab

---

### Post by tinybit on 2007-08-01
1. at the grub prompt, type:

geometry (hd0)
geometry (hd1)
geometry (hd2)

and post the output.

2. try "root" the partition which has caused the mentioned problem. Like this:

root (hd?,?)

and post the output.

3.try "fstest" the partition, like this:

fstest on
debug 0x7FFFFFFF
testload (hd?,?)/.../.../your_menu.lst

if there are too many messages, you may try debug 0xFFFFFFFF instead.

post any output messages.

---

### Post by KOri on 2007-08-01
Im having the same problem alnavegante described. The installation process completes normally but I get the "Error 17 File not found error" apparently when looking for menu.lst. Ive tried "find --set-root" with different paths (/wubi/boot/grub, /boot/grub, /grub ... etc.) with no success. I installed wubi on a secondary hd, maybe this is whats causing the "file not found error"? Is there a configuration file where the path to the /wubi/ directory can be modified?

JIC, my specs:
1.5GB RAM
P4 3.0Ghz
Win XP SP2
ATI X1600
hd1: 120GB
hd2: 300GB (wubi lives here)

---

### Post by KOri on 2007-08-01
OK, got it to work. GRUB didnt seem to like the fact that menu.lst was in (hd1,0), so I uninstalled and reinstalled to (hd0,1) and everything went smoothly. 

alnavegante: do you have multiple hard disks?

---

### Post by ago on 2007-08-02
Can you still run the tests tinybit mentiond on hd1,0? That would be helpful for us.

---

### Post by KOri on 2007-08-02
OK, I couldnt follow through with tinybit's instructions because I no longer have a menu.lst in (hd1,0) to testload. but here's the geomtry info:

geometry (hd0)
drive 0x80(lba) C/H/S 16383/255/63
Sector Count / Size 263192895/512
Partition 0 ntfs type 0x7
Partition 4 ntfs type 0x7

geometry (hd1)
drive 0x81(lba) C/H/S 38914/255/63
Sector Count / Size 625153410/512
Partition 0 ntfs type 0x7

---

### Post by bean123 on 2007-08-02
Can you try the following command:

cat (hd1,0)[TAB]

This will list the files in (hd1,0)

Then, you can choose a file that exists only in (hd1,0) , and use the following command:

find --set-root /FILENAME

BTW, your second harddisk is 305G ? maybe it's the 137G problem. you can use fstest to test it:

fstest inode X:\#0

fstest inode X:\#5

fstest list X:\

fstest inode X:\FILENAME

fstest comp X:\FILENAME

fstest must be run inside Windows. X: is the drive letter of your (hd1,0) partition.

The latest fstest can be downloaded at:

[http://grub4dos.sourceforge.net/grub4dos/](http://grub4dos.sourceforge.net/grub4dos/)

---

