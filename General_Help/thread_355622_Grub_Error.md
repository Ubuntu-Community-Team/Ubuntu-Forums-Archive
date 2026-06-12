---
title: "Grub Error"
date: 2007-02-07
forum: General Help
---

### Post by Sierra_Dave on 2007-02-07
Hi,

I had windows and Dapper running fine on laptop[compaq evo n1000v] w/ grub.  In effort to update windows driver, I lost gub. I go straight into windows w/o boot options.  

I tried the fix using Ubuntu live CD, but after I used terminal to enter grub...the "return" key no longer functioned.

I got a "W" instead of a carriage return.  I could not use any other command.  Tried it twice and switched keyboards w/o success.

sudo grub
  find /boot/grub/stage1w   <--- "w"  

Man...I hate windows software!

Any help would be appreciated. 
Thanks
Dave

---

### Post by r4ik on 2007-02-07
Is there any keyboard layout ?
Preferences -Keyboard

---

### Post by Sierra_Dave on 2007-02-07
Hi,

There is the us standard keyboard and several compaq prefernces under prefernces/keyboards, but not one for this model.  The carriage return works fine in terminal up to the point of using the "grub" command.  Then kaboom.

:confused: 
Dave

---

### Post by r4ik on 2007-02-07
Not sure if this will work but would you try Ctrl Alt F1 log in and try these instructions please ?

[http://www.arsgeek.com/?p=655](http://www.arsgeek.com/?p=655)

Ctrl Alt F7 to get back.

---

