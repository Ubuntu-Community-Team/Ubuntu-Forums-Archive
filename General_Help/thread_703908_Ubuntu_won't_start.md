---
title: "Ubuntu won't start"
date: 2008-02-21
forum: General Help
---

### Post by pdowling on 2008-02-21
Hi,

Tried looking at other threads, but didn't see anything to help.  Perhaps searching wrong.

I am currently running Ubuntu 7.1 as follows:

 - Two hard drives
 - One hard drive has
   + the ext3 partition with Ubuntu on it
   + an NTFS partition with Windows XP on it
 - A second hard drive is FAT32 with only data files

Recently I found that my computer would completely hang trying to run Ubuntu.  I tried running different kernels from GRUB, same result.  Tried disconnecting some hardware, same result.

Windows XP loads fine!

Fortunately most of my critical data was on the FAT32 partition so I can still access most of it from Windows.  However, I really miss my Linux!!

Anyway here is a screenshot showing where it freezes up.

[IMG]http://farm3.static.flickr.com/2277/2282987008_b03cb79eb7.jpg[/IMG]

Any thoughts?  At a minimum does anyone know a good procedure for me to access the ext3 partition so I can copy files from there to the FAT32 partition and ultimately back them up.  Worst case if I can back up the files on the Ext partition I don't mind reinstalling if needed.

Thanks,

Peter

---

### Post by uberlube on 2008-02-21
add 'irqpoll vga=791' into your boot options during grub.

---

### Post by pdowling on 2008-02-24
Thanks for the response.  irqpoll and vga setting didn't seem to help.

However, I did realize from another thread that Ubuntu would _eventually_ start if I waited long enough.  So I tried some of that "Usplash" stuff to see if that was it.  Managed to get my splash screen working, but the freezeup I'm getting occurs before the splash screen.

An irq issue does seem to be pretty close to the mark though.  I've noticed additional symptoms after some experimentation...

1. I had a Mybook external hard drive plugged in to the computer.  This took a long time before it would show ready so I disconnected it.  

2. I have a usb based wireless keyboard and mouse.  I noticed that after linux successfully got to the  gnome login screen that the keyboard and mouse didn't work.  Took about a full minute before suddenly the light came on and the keyboard and mouse started working.

After I log in all behavior appears more or less normal.  Although in general after moving from Feisty to Gutsy things feel a bit slower.

Anyone have any additional suggestions based on the above symptoms?

The very odd thing is that I've been using Gutsy since it came out and only just started having this long delay after grub menu for only about two weeks now.

It doesn't feel like a hardware problem as Windoze behaves normally on startup and I haven't changed any hardware on the system (other than using the Mybook external hard drive which I got a couple of months ago).

Thanks...

> **uberlube said:**
> add 'irqpoll vga=791' into your boot options during grub.

---

