---
title: "Hibernate - Boot problem"
date: 2014-12-06
forum: General Help
---

### Post by abdul3 on 2014-12-06
Hello

I was trying to repair MBR because i wanted to uninstall elementary OS. To do so, i tried to repair using samsung recovery solution but when it finished, i find out that there was no GRUB. I tried using live ubuntu usb to use boot-repair but as i have a 64-bit cpu, it failed too. I had to go eat so i put in hibernate mode. But till then i am unable to boot up any device.

All devices are detected by bios but when i choose the device to boot from, blinking cursors appear and then system boots again so it is in a boot loop. 

I tried to reset default values of bios but it did nothing. In my opinion, the real problem is that bios doesn't really boots it displays "system resuming". How i can hard reset bios ? I tried to clear cmos in order to do a reset bios, i couldn't find it.

I don't even know if i explained correctly my problem. Please help me !

Thanks

---

### Post by nerdtron on 2014-12-06
Hmm.. it's just that the BIOS doesn't which to boot, possibly you deleted/corrupted the MBR? This is not related to the BIOS.

Let's see, what OSes are initially installed? Is this dual boot? What is the output of boot-repair?

---

### Post by abdul3 on 2014-12-06
First of all, thanks for answering !
I had windows seven and elemeltary OS installed. Yes, it was dual boot. Boot-repair just told me to install boot-repair-disk because i had 64-bit version. 
Now, i can not boot from live usb or windows 7 usb or live cd rom or any other device. 
Appreciate any help !

---

### Post by abdul3 on 2014-12-12
Can somebody help me please ?

---

### Post by abdul3 on 2014-12-13
Hello, 

I just had to replace the hard disk and it worked! I think MBR was corrupted and it was causing troubles. 

Thank you very much nerdtron for your help !

---

