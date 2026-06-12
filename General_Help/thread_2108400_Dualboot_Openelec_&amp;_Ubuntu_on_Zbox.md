---
title: "Dualboot Openelec &amp; Ubuntu on Zbox"
date: 2013-01-24
forum: General Help
---

### Post by jgoodfel on 2013-01-24
Hello all - Total newbie here, so please forgive me if this answer should be obvious. I have a zbox that is currently running Openelec. I would like to set it up for dualboot with Ubuntu. I've downloaded and created a bootable USB for Ubuntu using a windows 7 machine. However, I don't know how to install it on the Openelec box (remember, newbie). The box doesn't boot from the USB upon reboot. Thus, it seems i have a couple of options. 
 
1) should I configure the Zbox to boot from USB? If so, how is this done?
2) should I install a browser on the zbox and install the second boot directly from the Ubuntu.com site? 
3) is there a third, more direct option that I don't see? 
 
Any help would be GREATLY appreciated!
 
Thanks
J

---

### Post by oldfred on 2013-01-24
Not familiar with Openelec. What boot loader does it have?

Does your system support booting from USB? You should be able to get into BIOS or use one time boot key (f12 on my system but varies) to change boot order.

You then can boot into live mode and see if Ubuntu runs ok and has drivers for your system. 

How large is hard drive?

---

### Post by jgoodfel on 2013-01-24
Thank you very much for replying!  It uses the Syslinux boot loader.  My system *should* support booting from USB, but I do not know how to adjust the bios from within the OS.  I have been able to interrup the boot-up process by hitting DEL.  However, this gives me a Boot: prompt and I don't know what command to use here.  
 
Not sure of the size of the hard drive as I'm not currently in front of the box, but I'd guess it is around 250GB.   
 
I hope this helps.  
J

---

### Post by oldfred on 2013-01-24
BIOS is normally a screen with many start up settings.

Do you get a quick startup screen with info on BIOS key or one time key mentioned, otherwise you need to read manual or search for way into BIOS.

---

### Post by jgoodfel on 2013-01-24
Ok, fortunately I have discovered a solution to this issue. As it turns out, the problem was with the USB stick that I was using. I tried another one and it booted from USB correctly.

---

### Post by nyran20 on 2013-02-28
Can you elaborate on your solution?  I'm also thinking about a Zbox and I'd have to dual boot too for my needs.  I'm looking for something like in this youtube video...it's in the first 45 seconds he has the option to choose one or the other.

[http://www.youtube.com/watch?v=TUy0fyjFcRI](http://www.youtube.com/watch?v=TUy0fyjFcRI)

---

