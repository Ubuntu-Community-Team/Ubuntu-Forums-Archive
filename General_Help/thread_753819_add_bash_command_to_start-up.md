---
title: "add bash command to start-up"
date: 2008-04-13
forum: General Help
---

### Post by Kaisersoze on 2008-04-13
Hi, 

I have a laptop with a syntek webcam. After a couple of googles I manage to install the driver to my kubuntu.

The problem is that, by default the image is upside-down. In order to flip it to the right way i have to type in Bash, every boot,  the following:

echo 1 >/sys/class/video4linux/video0/vflip


I would like this to be type automatically at startup. how can this be done? what file do I have to edit and insert this line?

Thank you in advance

---

### Post by artfwo on 2008-04-13
Hi! The most appropriate file for that would be:
**/etc/rc.local**

Hope this helps :)

---

### Post by wdaniels on 2008-04-13
...or possibly as option in /etc/modprobe.conf?

options stk11xx vflip=1

---

### Post by Kaisersoze on 2008-04-13
> **wdaniels said:**
> ...or possibly as option in /etc/modprobe.conf?

options stk11xx vflip=1


hmm.. i dont have that file. should i creat it and paste the above line into the file?

Thanks

---

### Post by Kaisersoze on 2008-04-13
> **wdaniels said:**
> ...or possibly as option in /etc/modprobe.conf?

options stk11xx vflip=1

Pasted it and didnt worked... :(

---

### Post by wdaniels on 2008-04-14
Oops sorry, wrong dist :D  In Ubuntu I think you can just use/create any file under /etc/modprobe.d, so /etc/modprobe.d/options or /etc/modprobe.d/fixwebcam etc.

Remember to reboot or reload the module after for the options to take effect.

---

