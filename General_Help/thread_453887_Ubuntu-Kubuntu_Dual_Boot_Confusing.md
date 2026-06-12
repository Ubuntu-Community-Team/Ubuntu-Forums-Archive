---
title: "Ubuntu-Kubuntu Dual Boot Confusing"
date: 2007-05-24
forum: General Help
---

### Post by dc12volthippy on 2007-05-24
I just installed Kubuntu as a secondary operating system to go with regular Ubuntu, so I re-partitioned the hard drive (Ubuntu 60%, Kubuntu 40%). I restart the system, and I expected the BIOS to say something like: "Select OS:
Ubuntu 7.04
Kubuntu 7.04"
But no! It says something like "Select OS:
(These are the Kubuntus)
Ubuntu-2.0.6.15-generic
Ubuntu-2.0.6.15-generic(safe mode)
Something-else-I-don't-remember

OTHER OPERATING SYSTEMS:
(These are the Ubuntus)
Ubuntu-2.0.6.15-generic (on /sda1)
Ubuntu-2.0.6.15-generic(safe mode) (on /sda1)
Something-else-I-don't-remember"
How do I make it so it just says something like:"Select OS:
Ubuntu-2.0.6.15-generic
Kubuntu-2.0.6.15-generic"
Or: "Ubuntu 7.04
Kubuntu 7.04"

If this is not possible, is there a way to make it less confusing?

---

### Post by afoglia on 2007-05-25
> **dc12volthippy said:**
> I just installed Kubuntu as a secondary operating system to go with regular Ubuntu, so I re-partitioned the hard drive (Ubuntu 60%, Kubuntu 40%).
[...]
[I]s there a way to make it less confusing?

Yes.  If you haven't put any other files on the system, I'd start from scratch.  Ubuntu and Kubuntu aren't two completely separate operating systems.  Kubuntu is the core Ubuntu packages with a different desktop environment, KDE as opposed to Ubuntu's GNOME.  That's why they look the same to Grub.  They use the same kernel (core program).  So instead of installing two copies of the same kernel.  Unless you have a very good reason, you might as well run them both on the same hard drive.  Here's how:

1. Install Ubuntu.
2. Then install the kubuntu-desktop package.  (The synaptic package manager is probably the easiest way.)  That will install the kubuntu packages.  There might be a question about whether you want gdm or kdm to run automatically.  Choose either.
3. Now you can choose between Ubuntu and Kubuntu when you log in.  There will be a "session" button on the login screen.  Press it and choose GNOME if you want the traditional Ubuntu desktop, KDE for Kubuntu.  You won't have to worry about keeping track of which kernel to boot in grub; it will choose the most recent for the default.

Benefits: You'll use less hard drive space.  You'll won't need to worry about "sharing" files between the different installations.  And not only can you switch between Ubuntu and Kubuntu without rebooting, you can use Kubuntu applications in Ubuntu and vice versa.

(I think your boot messages (usplash) and default login screen will say kubuntu, but that's not important.  You can switch that easily enough after, just ask, or you can try install kubuntu first and then ubuntu-desktop.)

If you don't want to start from scratch, you can probably just follow these steps on your existing Ubuntu install and then use the partition editor to erase the original Kubuntu partition, and increase the surviving partition.  And you'd probably need to reconfigure grub with "sudo dpkg-reconfigure grub".

Personally I have all three of the main Ubuntu variants installed.  I stick with Xubuntu, but I'm often more familiar with the KDE apps in Kubuntu.

Now, if you don't want to do that, you can edit /boot/grub/menu.lst to denote which kernel is which, but updating grub might cause your changes to be lost.

---

### Post by dc12volthippy on 2007-05-25
> **afoglia said:**
> 
Now, if you don't want to do that, you can edit /boot/grub/menu.lst to denote which kernel is which, but updating grub might cause your changes to be lost.

What changes are you speaking of?

---

### Post by afoglia on 2007-05-26
> **dc12volthippy said:**
> What changes are you speaking of?

If you look in /boot/grub/menu.lst, you'll see a bunch of general menu settings, and then a bunch of options of the form:

```
title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=[...] ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=[...] ro single
initrd          /boot/initrd.img-2.6.20-15-generic
```

(I've redacted the UUID's for clarity.)

Basically, these are lists of different boot states.  (Usually) the first will have a "savedefault" line meaning that it's the default.  Anyway, find the Kubuntu ones and add a K in front of "Ubuntu" in the title.  That should be it.  (But like I said, when you upgrade the kernel, those changes might disappear.)

Obviously, this file is write-protected so you'll have to edit it from a terminal command with "gksudo gedit /boot/grub/menu.lst"  (or in Kubuntu, "kdesu kate /boot/grub/menu.lst").

I'm not sure which installation you'll have to do this in.  Perhaps only Ubuntu.

---

