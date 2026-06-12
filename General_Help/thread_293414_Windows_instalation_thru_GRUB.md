---
title: "Windows instalation thru GRUB"
date: 2006-11-05
forum: General Help
---

### Post by matoxxx on 2006-11-05
Hi there,
i need to install windows on my extended sdaa6 partition and i came across this howto
[http://tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html](http://tldp.org/HOWTO/Linux+Win9x+Grub-HOWTO/proc.html)

I edited my menu.lst file  the way author suggested but windows install cd wont start telling me something like i have inaccesible acces path or what.

my menu,lst - is syntax for booting from cd corrent , cause author made them for Red Hat distro. Any suggestion ?
```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

title           Windows XP
	        map (hd0,0) (hd0,5)
	        map (hd0,5) (hd0,0)
	        rootnoverify (hd0,5)
	        chainloader +1
                makeactive

title           Win Boot Disk
	        map (hd0,0) (hd0,5)
	        map (hd0,5) (hd0,0)
	        chainloader (cd)+1
```

In the GRUB manual there is a section for booting cdrom from grub but i must burn iso which has stage2_eltorito implemented within.
Help me please ...

---

### Post by matoxxx on 2006-11-05
Bump

---

