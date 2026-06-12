---
title: "Bootable CD creation"
date: 2008-06-04
forum: General Help
---

### Post by kontika on 2008-06-04
Hi,

I have 2 questions:

1. An installed Ubuntu can automatically recognise the hardware and load the appropriate drivers at boot time? What if I install it on my laptop with a Pentium-m processor with an Nvidia graphic card and try to boot the system on a desktop P4 with an Ati card? Will it work just like it works with the live CD?

2.
I installed Ubuntu on my USB hard drive today. Unfortunatelly my laptop is not able to boot from USB port, so I would like to create a CD which with I will be able to boot the system from the external HDD. How can I make a CD like this? (I'm using grub)
I digged a lot on the net, but I couldn't find a good description about creating boot CDs.

Thx,
konti

---

### Post by KingTermite on 2008-06-04
As far as the not booting from USB, did you try different USB ports? I assume you already have USB set in BIOS prior to hard drive in boot order.

I mention this because I made a pendrive linux bootable pendrive a few weeks ago and spent a few hours trying to figure out why it wasn't working. It turned out that my laptop only boots from USB ports on side, not the ones in the back. Not sure why.

---

### Post by kontika on 2008-06-04
Unfortunatelly the BIOS doesn't support USB boot:(

---

### Post by rraj.be on 2008-06-04
Surelly the answer for your first questionwill be

There wont be any chances of booting more than 60%

due to your driver issues.

and regarding your second question can i know whether you want to create a system rescu disk or a Boot loader disk or a custom live cd.

---

### Post by kontika on 2008-06-04
Thanks for your post ! I want to create a boot loader CD with which I can boot with grub and start Ubuntu from the external HDD

---

### Post by rraj.be on 2008-06-04
You can use SUPER GRUB DISK.


This will  help you.

[www.geocities.com/supergrubdisk/]("www.geocities.com/supergrubdisk/")

And its already late night for me here.

Hope this will solve your problem.

Good night.

---

### Post by kontika on 2008-06-05
Supergrub is almost OK:) The problem with it is that the bios can't recognise the USB HDD at boot time, so supergrub can't see the partition in it.
Any oher idea?

---

### Post by rraj.be on 2008-06-05
I think there is an option to boot from usb port.

I think it can be seen in BIOS.

I think Just enabling

```
Boot from removable device

Enable usb boot
```

will solve this.

Then set your device priority as firt to usb.

A latest laptop will surely suport usb boot.

Just try this.

could i know if this not work,.

---

### Post by kontika on 2008-06-05
No. The bios of my laptop doesn't support booting from USB devices. I've checked it. It a 3 years old laptop.

---

### Post by rraj.be on 2008-06-05
I think this cpuld help.

```
sudo -i
cd /home
mkdir -p iso/boot/grub
cp /boot/grub/* /home/iso/boot/grub
mkisofs -R -b boot/grub/e2fs_stage1_5 -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso

```
--------------------------------------------------------------------------------------------
EDIT: try this one too

```
[http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html")
```

--------------------------------------------------------------------------------------------

If you want to make a GRUB Floppy look here.

```
[http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy]("http://www.gnu.org/software/grub/manual/html_node/Creating-a-GRUB-boot-floppy.html#Creating%20a%20GRUB%20boot%20floppy")
```

---

### Post by kontika on 2008-06-05
iso9660_stage1_5 is not exists in my enviroment. Should I re-install grub, or what? is it in an other package?

---

### Post by rraj.be on 2008-06-05
Try this.

```
sudo -i
cd /home
mkdir -p iso/boot/grub
cp /boot/grub/* /home/iso/boot/grub
mkisofs -R -b boot/grub/e2fs_stage1_5 -no-emul-boot -boot-load-size 4 -boot-info-table -o grub.iso iso
```

---

### Post by kontika on 2008-06-05
No luck:( weird characters appeared on the screen at boot time:(

---

### Post by rraj.be on 2008-06-05
K. i am a bit confused what to recommend.

i will try to get  some other go.

Dont think i am answerring unrelated to your question.

Booting from a Pen drive will reduce your life time of that drive and it will not be that much speed when compared to live cd  

[Because live cd takes full and direct control of your ram but this pen drive wont]

It's better  to go with a clean install because it will just take 20 minutes.


i will get a solution for this .

i need your file list of grub

just post the output of

```
ls /boot/grub

```

---

### Post by kontika on 2008-06-05
```

ls /boot/grub
default  
e2fs_stage1_5 
installed-version 
menu.lst 
reiserfs_stage1_5
stage2
device.map 
fat_stage1_5 
jfs_stage1_5 
minix_stage1_5 
stage1 
xfs_stage1_5

```

I installed the system to an external HDD, not to a flash drive.

Again: Basically what I want to do is a CD with which I can boot the computer and start the linux kernel. After the kernel has started from the CD it will enter to my the ubuntu system on my external HDD.
Understand? sorry, my english is a little bit poor:(

---

