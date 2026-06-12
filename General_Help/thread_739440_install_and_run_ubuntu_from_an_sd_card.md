---
title: "install and run ubuntu from an sd card"
date: 2008-03-29
forum: General Help
---

### Post by |{urse on 2008-03-29
I've scoured the net for a whole 3 minutes (whew) and cant seem to find this. Any ideas? anyone tried this?

---

### Post by |{urse on 2008-04-21
no-one? perhaps if i did this with a boot cd?

---

### Post by danwood76 on 2008-04-21
Standard SD cards have very low data throughput so are not ideal for launching an OS.
Plus you also need to have the hardware to interface with the card and so makes it more tricky.

USB sticks are better for booting ubuntu and such like.

Why would you want to boot from SD anyway?

---

### Post by |{urse on 2008-04-25
thx for replying! Simply because i want to make a router, doesn't need to be fast but it does need to look very black box and professional so i cant have a usb stick hanging out or rattling around inside. I'd use a hard disk but it needs to be solid state.

---

### Post by |{urse on 2008-04-25
or i can get an embedded board and load a kernel, make a toolchain (gasp) and try out arm interfacing lol but i dont want to go through all that just for a  cheap and easy router. I'm very familiar with other distributions but would like to have ubuntu in the product. Customers love the name @ our company.

---

### Post by danwood76 on 2008-04-26
The ideal thing would be to use flash memory direct, You can get x86 embedded processors, the new intel atom looks pretty nice.
It depends how much development time you have and what your budget is.

A memory stick is not the way to boot anything that needs to be reliable.

---

### Post by |{urse on 2008-04-27
I'm honestly not trying to be rude or anything but I'm looking at your last post and thinking "Wow, This guy is really sidestepping the question" how do you know booting from sd is unreliable? have you done it? and if so would you care to tell me how you did?

---

### Post by danwood76 on 2008-04-27
I have never booted an OS off an SD card.
I have built devices that use SD cards for storage and to read data with. The max bandwidth of SD cards is based on the hardware you interface with, I have reached some good speeds (up to 10Mb/s) but it tends to fluctuate, different cards can output different speeds and tend not to go as fast as they're rated.
Compact flash is a bit more reliable speed wise.

The main issue you will have is getting the BIOS of the system to boot load off a card reader.
Personally if I was going to design a router I would use some flash memory to store the bootloader and system software, some kind of microcontroller/microprocessor to process data, a chunk of RAM to stick the OS in, and some NICs.
Ideally you could use a MIPS processor running linux with the use of some common network ICs and spend some time developing some stable OS software.

Im not side stepping the issue, but using a standard motherboard and SD will be unreliable, it may not even work due to the card reader ICs probably not having drivers in the BIOS to allow booting, even bootloading.

I would lean towards MIPS over ARM, its a lot more widely used, also realtek chipstes tend to use MIPS, you can buy almost routers in a chip from them and an SDK. (Onboard NIC, Flash & RAM Interface)

---

### Post by |{urse on 2008-04-27
I totally agree with you on that, if it were my way it would be MIPS. and the os needs to be hotswappable as well as totally removeable and solid state to boot (as in to boot = also)! So unfortunately i dont have the budget to throw a battleship mtron in a hotswap bay at it lol. Thank you for your thoughts on this. Think I'm gonna scrap the whole idea and go a different route.

---

