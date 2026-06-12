---
title: "make faster on high-end pcs?"
date: 2007-12-16
forum: General Help
---

### Post by stinkinrich88 on 2007-12-16
Hello,

One thing I've noticed about linux is that, unlike windows, it runs at a more constant speed regardless of what hardware it is running on. But I bought and made this super duper high end PC and I want it to go really really fast! So stuff like caching the gnome menu at startup, keeping firefox in memory even when closed, loading more stuff into memory on startup, I have 2gigs of RAM! Let's start using it!

any ideas would be brilliant, thank youuu!!

---

### Post by TidusBlade on 2007-12-16
I have 2GB aswell, and find all distros almost the same speed. But if you want the extra performance you could try using a distro designed for low-end pc's. Ones that spring to mind are Damn Small Linux, Fluxbuntu, Xubnutu and Puppy Linux, and Feather linux.

---

### Post by stinkinrich88 on 2007-12-16
> **TidusBlade said:**
> I have 2GB aswell, and find all distros almost the same speed. But if you want the extra performance you could try using a distro designed for low-end pc's. Ones that spring to mind are Damn Small Linux, Fluxbuntu, Xubnutu and Puppy Linux, and Feather linux.

thanks for the speedy response! But what I really want is to get / adapt ubuntu to be suited to a high-end PC rather than a low end PC, by taking advantage of my dual cores and tonnes of memory. Maybe I'll look into 64bit ubuntu again, not sure how good it is atm.

---

### Post by r-mo on 2007-12-16
What you're talking about is this I think, so it's coming but not here yet

[https://wiki.ubuntu.com/AutomaticBootAndApplicationPrefetchingSpec](https://wiki.ubuntu.com/AutomaticBootAndApplicationPrefetchingSpec)

---

### Post by stinkinrich88 on 2007-12-17
ahh excellent! So that will also keep stuff in memory even when I close it I take it. Don't see why I can't get using right away! Don't you think?

---

### Post by kpkeerthi on 2007-12-17
Linux already makes good use of your RAM. Read up on [Linux Memory Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management"). Also, CPU speed and performance are [not directly proportional]("http://www.tech-faq.com/cpu-speed.shtml"). 

In short, you are getting the best your hardware could deliver.... with Linux.

---

### Post by stinkinrich88 on 2007-12-17
> **kpkeerthi said:**
> Linux already makes good use of your RAM. Read up on [Linux Memory Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management"). Also, CPU speed and performance are [not directly proportional]("http://www.tech-faq.com/cpu-speed.shtml"). 

In short, you are getting the best your hardware could deliver.... with Linux.

Sure it makes good use but I want even faster! For example, I want firefox to load as fast as it does after I've closed it as it does when I un-minimise it. It's pretty simple, there's gotta be a way! I'd like Ubuntu to pile a load of programs that I use regularly into RAM for as long as it can at startup.

---

### Post by danwood76 on 2007-12-17
> **stinkinrich88 said:**
> Sure it makes good use but I want even faster! For example, I want firefox to load as fast as it does after I've closed it as it does when I un-minimise it. It's pretty simple, there's gotta be a way! I'd like Ubuntu to pile a load of programs that I use regularly into RAM for as long as it can at startup.

Linux is extremely efficient in terms of performance
I have a Core 2 Duo E6420 @ 3.6GHz at home with 2 gigs of RAM and my PC is way faster running gutsy than windows is with the same hardware.

A good thing would be to re compile your kernel with your CPU setup correctly and optimised for desktop performance.
for example the interrupt timer set to 1000 Hz gives better desktop performance.

there is a guide somewhere on these forums for recompiling the kernel the ubuntu way and which optimisations to add its quite simple and normally recompiles your graphics drivers if you installed them as .deb s

regards,
Danny

---

### Post by stinkinrich88 on 2007-12-18
ahh thanks, sounds good, bit complicated and I don't really understand how that makes a difference but I'll look into it.

Thanks guys, any other ideas would be great too!

---

### Post by danwood76 on 2007-12-18
Well the interrupt timer will be quite critical, its how many times a second the computer looks for input or interaction from the user, for servers you set it low, to something like 100 Hz (100 times a second) as they are normally left alone and the userspace is not needed so much. setting it higher will mean that the system is more responsive to user input and processing userspace.

There are other options aswell, like setting the processor type will allow the kernel to be compiled with better multi processing and more optimisations for the instruction sets available with the processor.

There is a good guide on these forums to recompiling the kernel and for the optimisations aswell.

regards,
Danny

---

### Post by Dixon Bainbridge on 2007-12-18
> **stinkinrich88 said:**
> Sure it makes good use but I want even faster! For example, I want firefox to load as fast as it does after I've closed it as it does when I un-minimise it. It's pretty simple, there's gotta be a way! I'd like Ubuntu to pile a load of programs that I use regularly into RAM for as long as it can at startup.

Why do you need apps to start 1 second quicker? Is your time that precious? :)

---

### Post by stinkinrich88 on 2007-12-18
lol, unfortunately I'm a perfectionist. I just thought there would be a simple solution though, you know, like an auto-trayer without the tray icon, can't be hard. Obviously not though. Maybe I'll make one one day.

Anyone else interested I found this useful sticky:

[http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192)

---

### Post by danwood76 on 2007-12-18
> **Dixon Bainbridge said:**
> Why do you need apps to start 1 second quicker? Is your time that precious? :)

I think apps loading slowly would be quite a benefit if your time was precious but you were paid by the hour!

---

