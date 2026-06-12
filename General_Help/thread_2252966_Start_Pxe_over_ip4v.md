---
title: "Start Pxe over ip4v"
date: 2014-11-16
forum: General Help
---

### Post by aidas2 on 2014-11-16
Hello guys, yesterday I tried to install windows 7 from usb, and changed boot order, and after a restart I got error saying start over ip4v, bmy boot order now

USB hard drive 
USB Floppy/CD
UEFI:IPV4
UEFI:IPV6

If I press in Bios change defaults and exit, nothing happens

---

### Post by aidas2 on 2014-11-16
Up

---

### Post by matt_symes on 2014-11-16
Hi

it sounds like your USB stick with windows on it is not being recognised and so it's defaulting to PXE booting.

See if there is an option in the BIOS to disable LAN boot.

You will then have to discover why the USB stick is not booting.

Kind regards

---

### Post by aidas2 on 2014-11-16
In bios settings i see 
Sata power managment enable
S4/S5 Wake On Lan disable

Enabling it didnt help

After maybe 5min Start PXE over IPv6 goes away and it says
ERROR No boot disk has been detected or the disk has failed

So im thinking maybe computer tries to boot OS from USB but it's not mounted

---

### Post by matt_symes on 2014-11-16
Hi

> **aidas2 said:**
> In bios settings i see 
Sata power managment enable
S4/S5 Wake On Lan disable

Enabling it didnt help

After maybe 5min Start PXE over IPv6 goes away and it says
ERROR No boot disk has been detected or the disk has failed

So im thinking maybe computer tries to boot OS from USB but it's not mounted

I think the BIOS is not recognising that there's an operating system on the USB stick.

5 minutes is a huge timeout for a PXE boot.

I've never come across a BIOS where it was not possible to disable PXE booting but yours maybe the first. I'll leave it up to you whether you want to list all your BIOS options in your next post.

Kind regards

---

### Post by aidas2 on 2014-11-17
Sorry that i didn't post any BIOS Settings, it was hard to even reply with a phone. Now using college computer i'll post some images of Bios settings. I have more pictures but i can insert only 5 per post.

---

### Post by aidas2 on 2014-11-17
Upload 5 more pictures, maybe you will help me.

---

### Post by matt_symes on 2014-11-17
Hi 

Try setting "NIC PXE option ROM download" to disabled.

That may disable PXE booting for you.

Kind regards

---

### Post by aidas2 on 2014-11-17
Now it says
ERROR: No boot disk has been detected or the disk failed.

---

### Post by matt_symes on 2014-11-17
Hi

> **aidas2 said:**
> Now it says
ERROR: No boot disk has been detected or the disk failed.

That sounds like it disabled PXE booting for you and I think that's what you wanted.

So does the internal hard drive have an OS on it ?

Are you still trying to boot from that USB stick with windows on it ?

Kind regards

---

### Post by aidas2 on 2014-11-17
No im not trying to load from USB internal hard drive has installed ubuntu 14.10

---

### Post by aidas2 on 2014-11-17
on internal drive i have installed ubuntu 14.10 but in boot order i can choose USB Hard Drive And Floopy Disk

---

### Post by matt_symes on 2014-11-17
Hi

As I have stated a couple of times I think your BIOS does not think that Window is on the USB stick.

I think you have selected the correct boot option to boot the USB stick.

As I assume you can still boot the internal hard drive, my next question is "How did you create the USB stick with windows on it ?"

If you followed a tutorial on the Internet then please post the link; if not then post, in detail, the steps you took to create the USB stick.

Kind regards

---

### Post by aidas2 on 2014-11-17
Downloaded Windows 7 iso file from [http://techverse.net/download-windows-7-iso-x86-x64-microsofts-official-servers/](http://techverse.net/download-windows-7-iso-x86-x64-microsofts-official-servers/)

Using GParted i formatted USB to FAT 32 

And Using Unetbootin created bootable USB

[SIZE=1][COLOR=#000000][FONT=verdana][SIZE=2][SIZE=3][SIZE=7][SIZE=5][SIZE=4][SIZE=2][SIZE=1][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/COLOR][/SIZE]I Formatted to FAT 32 Because Unetbootin would see USB as NTFS

---

### Post by matt_symes on 2014-11-17
Hi

> **aidas2 said:**
> Downloaded Windows 7 iso file from [http://techverse.net/download-windows-7-iso-x86-x64-microsofts-official-servers/](http://techverse.net/download-windows-7-iso-x86-x64-microsofts-official-servers/)

Using GParted i formatted USB to FAT 32 

And Using Unetbootin created bootable USB

I Formatted to FAT 32 Because Unetbootin would see USB as NTFS

I'm pretty sure the USB pen drive has to be formatted to NTFS to boot windows 7. It will not boot with FAT32.

If you format it with NTFS using gparted, can unetbootin see the pen drive ?

If unetbootin cannot see the NTFS formatted version of the pen drive the you have an older version of unetbootin and need to update it.

Kind regards

---

### Post by aidas2 on 2014-11-17
Tried few other unetbootin versions, but still does not see as NTFS

A lot of people are complaining about this, but it look's like there's no fix for it(?)

---

### Post by matt_symes on 2014-11-17
Hi

The last time I created a windows USB I used a windows machine and the windows tools. This was a window 7 USB stick.

However, according to the linuxandlife.com website, you can use unetbootin version 494. You can get this from source forge.com

I cannot vouch for the validity of this information, however they do say that lower version will not work with NTFS so I thing it's worth trying.

So get that version and give it a go.

Kind regards

---

### Post by matt_symes on 2014-11-17
Hi

Try this link to get the version of unetbootin suggested

[http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/](http://sourceforge.net/projects/unetbootin/files/UNetbootin/494/)

Kind regards

---

### Post by aidas2 on 2014-11-17
I can use windows machine at college but it wont let me to open .exe file without admin username and password. I'll try to use friends computer or talk with Lecturers at college.

---

### Post by matt_symes on 2014-11-17
Hi

> **aidas2 said:**
> I can use windows machine at college but it wont let me to open .exe file without admin username and password. I'll try to use friends computer or talk with Lecturers at college.

I take it that version of unetbootin did not work ?

I may try to create a windows 7 USB stick myself and see if I can find a way under Linux.

Kind regards

---

### Post by aidas2 on 2014-11-23
So hello guys i'm still having problems. 
I successfully made  bootable USB with ubuntu 14.04 inside. But during installation it says  > The installer encountered an error copying files to the hard  disk. So i can't install ubuntu again..
But i can try it without installing with no problems.

My  friend gave me Windows 7 master disc and during installation it says  > Windows cannot innstall required files. The file may be corrupt  or missing.

What can i do more?

---

### Post by aidas2 on 2014-11-23
Thank you guys for your help!

So with startup disk creator I finally installed ubuntu 14.04 LTS

I really miss Windows 7 but i'll stick with ubuntu.

Can I somehow make this topic SOLVED or FIXED?

---

### Post by lisati on 2014-11-23
> **aidas2 said:**
> Thank you guys for your help!

So with startup disk creator I finally installed ubuntu 14.04 LTS

I really miss Windows 7 but i'll stick with ubuntu.

Can I somehow make this topic SOLVED or FIXED?

I'm glad to hear that you're making progress.

You can mark the thread solved using the "Thread tools" menu near the top of the page.

---

