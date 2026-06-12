---
title: "Cannot boot into kubuntu after Wubi install"
date: 2007-10-17
forum: General Help
---

### Post by guenthk on 2007-10-17
After I have installed the kubuntu version of Wubi-7.04.04 on Windows XP Professional, ubuntu appears in the Windows boot menu, but if I select it then GRUB reports

   root (hd0,6)
   error 27: no such partition

(Actually, "no such partition" should be GRUB error 22 rather than 27.)

Here the contents of my "C:\boot.ini":

[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptOut
c:\wubildr.mbr="Ubuntu"

Perhaps I should also mention that there exists another file "C:\boot.ini.comodofirewall" which seems to belong to my Comodo firewall, but I don't know anything about its purpose.

---

### Post by guenthk on 2007-10-17
In the meantime I have remembered that I had moved the wubi folder to another drive before my first boot attempt. This is probably the reason for the reported boot error.

Now I wonder, of course, whether I can anyhow correct this error by manually editing any configuration files, or will I have to repeat the entire lengthy installation process?

---

### Post by ago on 2007-10-17
Hmm there should not be any "root (hd0,6)"
Look into menu.lst

---

### Post by guenthk on 2007-10-17
Now I have reinstalled the kubuntu version of Wubi completely from scratch on my C drive, but the result remains the same:

root (hd0,6)
error 27: no such partition

Here is my C:\menu.lst:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ed8f3799-32f3-4e2b-80e9-9108de579cac ro quiet splash locale=de_DE
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=ed8f3799-32f3-4e2b-80e9-9108de579cac ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd0,6)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ed8f3799-32f3-4e2b-80e9-9108de579cac ro quiet splash locale=de_DE
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd0,6)
#kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=ed8f3799-32f3-4e2b-80e9-9108de579cac ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
 

If, as you say, (hd0,6) is wrong: what would be the correct hd spec? Can I simply correct it in menu.lst?

Btw: Is t Ok that a GRUB menu (reflecting the above menu.lst) appears after I have selected ubuntu on the Windows boot menu?

---

### Post by ago on 2007-10-17
Wubi does not use any "C:\menu.lst", the menu.lst file is in the wubi folder. Try to rename the C:\menu.lst -> C:\menu.lst.old

---

### Post by guenthk on 2007-10-18
You were right: The "C:\menu.lst" was in the way. After removing it I could successfully install Kubuntu, except for the fact that I couldn't log in then to my new Kubuntu, see separate thread.

Many thanks!

Klaus.

---

