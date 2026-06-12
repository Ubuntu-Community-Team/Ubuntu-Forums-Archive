---
title: "[SOLVED] Ubuntu 7.10 Boot problem"
date: 2008-05-11
forum: General Help
---

### Post by melenor on 2008-05-11
Alright recently i upgraded my "Athlon 64 3000+" to a "Athlon X2 4200+" and my 2GB RAM to 4GB RAM, after the upgrade my ubuntu 7.10 installition would freeze and boot. I have tested RAM and found no problems. When i booted into recovery mode it also frooze on boot and i got this error as my last lines. I have tried upgrading to 8.04 but ran into almost same problem so i thought to try to go back to this and upgrade from inside ubuntu 7.10. 

[	9.332000] ata3: timeout waiting for ADMA IDLE, stat=0x440
[	9.332000] ata3: timeout waiting for ADMA Legacy, stat=0x440
[	9.332000] ata3.00: Exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0

[	9.332000] ata3.00: (CPB resp_flags 0x11: CMD error)

[	9.332000] ata3.00: cmd c8/00:f8:3f:a0:23/00:00:00:00:00/e3 tag 0 cdb 0x0 data 126976 in
[	9.332000] ata3.00: res 51/40:00:da:23/00:00:00:00:00/e3 Emask 0x9 (media error)

Thank you for your help.

---

### Post by melenor on 2008-05-11
I still need help anyone out there at all? thanks.

---

### Post by Tomatz on 2008-05-11
Can you replicate the problem with another os (eg xp) as the issue sounds hardware related. Also does your board support a dual core processor. 

Maybe flashing your bios with an updated bios may fix the issue :)

---

### Post by melenor on 2008-05-11
XP works fine, in fact it works better now. how would i be able to flash my motherboard, and how do i know what to flash it with?

---

### Post by Tomatz on 2008-05-11
> **melenor said:**
> XP works fine, in fact it works better now. how would i be able to flash my motherboard, and how do i know what to flash it with?

Goto your boards manifacturers site and download the latest bios update for _your_ board. 

Instructions should be provided on howto flash your bios with the download (usually done by floppy). Most manifacturers provide a bios update utility that you can use under windows.

---

### Post by melenor on 2008-05-11
My BIOS is already up to date

---

### Post by melenor on 2008-05-11
My BIOS is already up to date

---

### Post by Tomatz on 2008-05-12
Have found this:

[http://ubuntuforums.org/archive/index.php/t-472056.html](http://ubuntuforums.org/archive/index.php/t-472056.html)

Apparantly the error indicates a bad HDD.

Hopefully its just disc errors. As you cant boot ubuntu you can use the gparted live cd:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

Just burn the .iso to disc and boot with it in the tray ;)


Hope it works for you.

---

### Post by melenor on 2008-05-12
yup, it was my hard drive. to test that theory i simply unplugged one of my hard drives and tried to boot liveCD and it worked. i then figureing it couldn't hurt plugged the hard drive back in to see if i could just use partition editor in ubuntu and i had to delete the old 7.10 partition, because that seemed to be the only one that would only effect ubuntu and not XP and then i installed 8.04 and so far no more problems.

---

### Post by Tomatz on 2008-05-12
Cool ;)

Hopefully the problem is solved. If it is you could mark the thread accordingly so others who come across the same issue can get an easy fix.

---

### Post by melenor on 2008-05-12
... sorry for asking this, i feel kinda dumb but i forgot how to mark the thread solved.

---

### Post by Tomatz on 2008-05-12
Nah..

..you dont know till you ask ;)


Thread tools (just above the top post in the page) , mark thaead as solved

---

