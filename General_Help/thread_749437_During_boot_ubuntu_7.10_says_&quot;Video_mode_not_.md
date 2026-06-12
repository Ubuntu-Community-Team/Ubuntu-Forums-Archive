---
title: "During boot ubuntu 7.10 says &quot;Video mode not supported&quot;"
date: 2008-04-08
forum: General Help
---

### Post by lotakoka on 2008-04-08
Hi
I have installed UBUNTU 7.10 on my desk top which has HYUNDAI L70N monitor in DUAL boot option with windows xp.
After installation it display "Video mode not supported" if select normal boot. Then tried to boot in recovery mode and got prompt. After existing from prompt i get desktop working and everything looks ok.
Question why UBUNTU works in recovery mode but not in normal mode. Is there any setting to change to refelect above LCD monitor ?

Thx

---

### Post by ajgreeny on 2008-04-08
Try removing quiet splash from the end of the kernel line in your **/boot/grub/menu.lst** file.  I suspect your usplash screen is set to the wrong resolution for the screen, and this can stop the boot process completely.  You can also set the correct resolution in /etc/usplash.conf as root ```
sudo gedit /etc/usplash.conf
```

Hope this helps.

---

### Post by cotcot on 2008-04-08
You could try to add vga=771 to the kernel line in fstab :
> title		Ubuntu Gutsy 64 bit (on /dev/sda8)
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6485392e-a2fe-4709-a013-24e53d0ecd24 [COLOR="Red"]vga=771[/COLOR] ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

---

### Post by lotakoka on 2008-04-08
Hi
Cotcot
Do you know where fstab is located ? 

THX

---

### Post by ajgreeny on 2008-04-08
I think cotcot meant in /boot/grub/menu.lst, the same file I referred you to.  However, to answer you fstab is in /etc.  It is a plain text file but can omly be edited as root with ```
sudo gedit /etc/fstab
```.  It tells the system where the partitions are that need to be mounted at boot time.

---

### Post by lotakoka on 2008-04-09
removing quiet splash from the end of the kernel line in my /boot/grub/menu.lst file worked trick. But during booting i see lots of text rollowing over screen . How can i avoid that ?

---

### Post by ajgreeny on 2008-04-10
I don't think you can, though you could try just putting back "quiet" in the menu.lst file but still leave out the word "splash".  I've never tried that but it may work, or at least reduce the amount of scrolling text.  However, you should be able to get the system to show the usplash screen as long as the resolution in /etc/usplash.conf is set to something your monitor can handle.

---

