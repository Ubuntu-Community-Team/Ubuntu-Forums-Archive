---
title: "feisty+laptop=dissaster?"
date: 2007-05-04
forum: General Help
---

### Post by curtk69 on 2007-05-04
i tried installing feisty on my laptop, a compaq presario 2100ca  and things didnt go well from the start.
first off it wouldnt resize the hdd so i had to delete  my windows install

now it wont bootup for the first time?

its stuck on some dos login screen with a blinking cursor
i cant type anything, not my login name nor my password it just sits there with the cpu apparantly maxed out since fan runs full tilt and does nothing

wat did i do wrong?

---

### Post by CM Xtasy on 2007-05-04
Did you check if the CD had any defects?

---

### Post by KrazyPenguin on 2007-05-04
Your question is not very clear:

Did you install Feisty off the live cd??

Do you get a Grub menu when you turn your computer on??

---

### Post by cumanzor on 2007-05-04
it's not a DOS screen. A black screen with a blinking cursor probably means something is wrong with the MBR or the partition tables, I'd say, they were corrupted. If this is the case, your best bet is to reinstall. Use the LiveCD and erase the entire disk, then proceed to install Ubuntu

---

### Post by curtk69 on 2007-05-04
no i didnt  check the disk , its a brand new burn, how do you check it?
i downloaded feisty [intel x86 cuz thats what they said was most compatible with my xp2400 and burned an iso
is that what a live cd is?

yes there was a grub menu with a 3 sec dountdown where u could change boot order or something, then it went through all these checks saying  OK 
to the right of each thing

the first time it stalled on bootloader something so i rebooted after listening to my cpu run maxxed out for 5 minutes then it did all the same things and went thru the bootloader and hungup on the ubuntu login:

---

### Post by curtk69 on 2007-05-05
ok i did another clean install , reformatted used whole entire disk and got same errors

which should i choose during install
dns server or 
lamp server

i have no idea what this is about?

---

### Post by curtk69 on 2007-05-05
i think i downloaded the wrong version somehow a server version?
wtf?

---

### Post by curtk69 on 2007-05-05
well i guess i will try installing from my original 6.06 or 6.1  livecd whichever it was

---

### Post by hvbakel on 2007-05-05
If you go to this page: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) you should select the **Desktop edition** of "Ubuntu 7.04 - Supported to 2008" (left hand side)

---

### Post by curtk69 on 2007-05-05
i already tried that site before but was getting server errrors and couldnt download

so i  installed off my old livecd and it worked and updated fully only now there seems to be another problem updating to feisty , a network problem, maybe wireless?
it wont connect to the internet and gives the following error when i double click the network icon in taskbar

please contact the administrator to resolve the following  problem;
SIOCGIFFLAGS error; no such device

---

### Post by ali4949 on 2007-05-05
if you are having wireless problems during the update process, try connecting to a wired connection during the update, this way you don't get disconnected during the update process.

---

