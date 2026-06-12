---
title: "edit grub to boot xp"
date: 2007-03-10
forum: General Help
---

### Post by marshall.robert on 2007-03-10
Hello,

Ive just reinstalled ubuntu on an extended partition and now grub isnt showing xp (it did before but ubuntu was on a primary partition). ive played around with menu.lst but i cant seem to give it the right command to boot into xp (ive gone from it saying 'ntldr cannot be found (or something to that effect)' to it not going past 'starting up...')

could someone please post the code i need to put into menu.lst, or point me in the right direction to getting it to boot xp.

any help will be greatly appreciated

many thanks

-rob

---

### Post by rocketman768 on 2007-03-10
This is for my system. You will need to locate which partition windows is on so that you can modify my stuff below. In case you don't know, (hd1,0) is the first partition on the second hard disk. So, it is equivalent in a sense to /dev/hdb1.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd1,0)
savedefault
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

---

### Post by marshall.robert on 2007-03-10
thanks for the quick reply and cheers for the code

oh and will i need the:

map (hd0) (hd1)
map (hd1) (hd0)

it looks like its only applicable when you have 2 hdd's

-rob

---

### Post by rocketman768 on 2007-03-10
No, you will probably not need the "map" statements.

---

### Post by marshall.robert on 2007-03-10
has not worked, i think its cos i did a repair of xp and didnt boot into it lol, oh well ill make a new install and reformat and partition the hdd again, fun....

many thanks

-rob

---

### Post by rocketman768 on 2007-03-10
Hm, you said it "could not find ntldr"? Insert your XP install cd and get to the recovery console (by pressing 'r' or something somewhere before the install actually begins...it will tell you when to do this). Then, I think the command is "fixboot c:\". Also, there is a "fixmbr" that will overwrite your master boot record (probably where grub is) in order to boot XP. Be careful, but fixboot may help with your problem.

---

### Post by strabes on 2007-03-10
Virtualize!!! [https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

If that's not an option, you can just modify your /boot/grub/menu.lst to include Windows. Here's what the relevant part of mine looks like. This is at the very end of the file: 

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Micro$oft Windows XP LOL!!!!!!!!!!
root            (hd0,0)
savedefault
makeactive
chainloader     +1


You'll just have to change the location of your windows partition. (hd0, 0) refers to the first partition on the first hard disk, where windows ilkes to be installed anyway.

---

