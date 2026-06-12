---
title: "Display Problem"
date: 2008-05-29
forum: General Help
---

### Post by SoFly on 2008-05-29
Firstly, I'd like to say hello to everyone!

I discovered Ubuntu a while ago but didn't bother installing it since I never actually needed it. And then I came across this software called Virtual Box, so I though I give Ubuntu a go.

Now the thing is, I used Ubuntu from the CD i have without installing it and it worked perfectly, so I installed it, through Virtual Box.

I restarted the OS (in Virtual Box; the disk not in computer anymore) and when it loaded up, the display was all messed up.

Then, I made a new virtual machine and ran Ubuntu from the CD again and the display's fine. Again, if I run it without the CD from the installed version the display gets messed up. :(

Here's a screenshot:

[http://i27.tinypic.com/5f2bex.jpg](http://i27.tinypic.com/5f2bex.jpg)

Anyone got any suggestion as to how I can fix this?

Dunno if it makes a difference but I'm using it on Windows XP.

Would really appreciate your help, thanks.

---

### Post by SoFly on 2008-05-30
Right, I've been told that there is some problem with the 'xorg.conf' file and I need to reset it or copy it from the Ubuntu CD. I can't seem to find it in the CD, so how would I go about resetting it? :confused:

---

### Post by bingoUV on 2008-05-30
Install guest additions as described here. [http://hamid11771.com/2008/05/install-virtualbox-additions-for-an-ubuntu-804-guest/](http://hamid11771.com/2008/05/install-virtualbox-additions-for-an-ubuntu-804-guest/) . Using this, it should improve graphic image.

---

