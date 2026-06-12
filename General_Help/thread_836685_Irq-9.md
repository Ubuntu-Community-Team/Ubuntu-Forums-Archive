---
title: "Irq-9??"
date: 2008-06-21
forum: General Help
---

### Post by asharness on 2008-06-21
can any1 explain to me why when I goto terminal and then to top, something call IRQ-9 is using 27-40 % cpu-even at idle. I can barely run a program, it make everything so delayed

---

### Post by spiderbatdad on 2008-06-21
Could be configuration problem with wireless network? Post  dmesg or read through it.```
dmesg > ~/Desktop/dmesg.txt
```If you post it here, right click the file and create an archive, then upload it as an archive, otherwise the text file may be too large.

---

### Post by asharness on 2008-06-21
no wifi but heres the file

---

### Post by asharness on 2008-06-21
sorry heres the file

---

### Post by spiderbatdad on 2008-06-21
no file...use manage attachment tool below...upload as an archive.

---

### Post by asharness on 2008-06-21
file failed to upload three times

---

### Post by spiderbatdad on 2008-06-21
Have you right clicked on the file and selected "create an archive?" Make sure it is the archive you try to upload.

---

### Post by JBull on 2008-06-21
During boot on my machine I noticed the ACPI power management uses IRQ 9.  And I'm having ACPI issues with my machine.  I don't have a solution but that may be a lead for you.

---

### Post by asharness on 2008-06-21
to large to fit so change the name to .txt

---

### Post by asharness on 2008-06-21
jbull i had the same problem. do you have a 2nd hdd for ubuntu? How is it connected if so

---

### Post by asharness on 2008-06-21
That was so much easier than I made it out to be
I learned some thing new!

---

### Post by JBull on 2008-06-21
> **asharness said:**
> jbull i had the same problem. do you have a 2nd hdd for ubuntu? How is it connected if so

No 2nd HD.  The only one is a Western Digital Parallel ATA.  There is also a CD-ROM drive on the second PATA.

My bios is fairly recent, the board is only about three years old and supports P4 with 478 socket.  

Anyway, this is off-topic of your problem so I'll check out of the discussion sicne I have no other suggestions for a solution.

---

### Post by spiderbatdad on 2008-06-21
Yes. it looks like some problem with apic in the bios...seem to be missing a little info near the top of that file. I think you need to try a few boot parameters to see what will work. Unfortunately, can't always get it the first time...so you may have to experiment a little. If you end up failing to boot (unlikely but possible) don't panic, just boot into recovery and fix the file.

The file that needs to be edited is /boot/grub/menu.lst Edit with nano in superuser mode.```
sudo nano /boot/grub/menu.lst
```
I say nano, so you feel comfortable with command line editing, in case you end up using recovery mode to re-edit the file. Graphically, the same file can be edited with gksu gedit /boot/grub/menu.lst.

To save the file in nano: crtl-o then enter to confirm, them ctrl-x to exit.

Scroll down to this section:```
# savedefault=true

## ## End Default Options ##

title		Ubuntu hardy (development branch), kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=####'s ro **lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

delete --quiet splash and make it look like example above...at the end of the line begining with the word 'kernel': lapic pci=routeirq.

If that doesn't fix the problem try **irqpoll**only irqpoll, not lapic pci=....etc.

If that doesn't fix it, try **acpi=force **

---

### Post by asharness on 2008-06-21
whats the command for supermode?  Im a nuub but I have used it before, and willing to learn

---

### Post by spiderbatdad on 2008-06-21
"sudo" ```
sudo nano /boot/grub/menu.lst
``` This is temporary root in user space. From recovery mode, you would not need 'sudo' as you would be logged in as root. Note recovery mode is only necessary should you run into a problem that prevents the system from booting.

---

