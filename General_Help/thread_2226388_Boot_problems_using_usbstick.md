---
title: "Boot problems using usbstick"
date: 2014-05-27
forum: General Help
---

### Post by chillabis on 2014-05-27
Hi i have installed various linux systems based on Debian and Ubuntu and they all have the same problem.
I'm using a 16bg Kingston DataTraveler G2 and installed linux like it was a regular hdd through VMware Workstation. 
And I'm getting this problem att boot up:

[IMG]http://s9.postimg.org/o3bi46xn3/IMG_0086.jpg[/IMG]


The usb works fine in windows and inside VMware Workstation.
Is there a way to fix this?

---

### Post by gordintoronto on 2014-05-27
I don't know what is causing your problem, but here is an approach which works:

Burn the ISO to a DVD, boot from it, and install to the USB stick.

---

### Post by chillabis on 2014-05-31
Did some googling... Many answers says it's a bug in the the newer kernels. I'm doomed.

---

### Post by C.S.Cameron on 2014-05-31
> **gordintoronto said:**
> I don't know what is causing your problem, but here is an approach which works:

Burn the ISO to a DVD, boot from it, and install to the USB stick.

+1 
This method works for me with all recent Ubuntu versions, although I usually install from a Live USB rather than from Live DVD.

Although it might be a problem with the computer.
Have you tried the stick in other computers?

---

### Post by chillabis on 2014-06-01
> **C.S.Cameron said:**
> +1 
This method works for me with all recent Ubuntu versions, although I usually install from a Live USB rather than from Live DVD.

Although it might be a problem with the computer.
Have you tried the stick in other computers?

Yes some time ago but not recently. I only own one computer.
Even Unetbooting doesn't work either. I bought a brand new usb Kingston Datatraveler G4 16gb it's the same problem...

---

### Post by chillabis on 2014-06-01
> **C.S.Cameron said:**
> 
Although it might be a problem with the computer.

I think so too, tried to boot from the cd with no usb's connected and i get the same error.
So my HDD's isn't working properly.. I'm so newb at this. Is there a way to fix the harddrives?

---

### Post by chillabis on 2014-06-01
> **C.S.Cameron said:**
> 
Although it might be a problem with the computer.

I think so too, tried to boot from the cd with no usb's connected and i get the same error.
So my HDD's isn't working properly.. I'm so newb at this. Is there a way to fix the harddrives?

---

### Post by Robel_Lakwe on 2014-06-01
Robel Lakwe - have you  tried to take it to Geek squad ?

---

### Post by sudodus on 2014-06-02
Welcome to the Ubuntu Forums :-)

Please read this wiki page to get some ideas what to do.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I conclude from your first post, that you are running Windows. Instead of trying inside wmware, try to make the USB boot drive directly from Windows with Unetbootin. There is a detailed tutorial at this link

[Paul Sutton's Unetbootin how to]("http://zleap.net/unetbootln-usb-how_to/")

It will help us help you, if you specify your computer

- Brand name and model
- CPU
- RAM
- graphics chip/card
- wifi chip/card

- UEFI or BIOS
- Windows version

---

### Post by chillabis on 2014-07-03
I found a solution but I don't know how to do it. :S

In this thread: [https://bbs.archlinux.org/viewtopic.php?pid=1107838](https://bbs.archlinux.org/viewtopic.php?pid=1107838)
Someone is mentioning 
[COLOR=#333333][FONT=sans-serif]
" Add
  options libata atapi_passthru16=0
  
  to /etc/modprobe.d/modprobe.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]

 Add
 FILES="/etc/modprobe.d/modprobe.conf"

 to /etc/mkinitcpio.conf[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
 Rebuild kernel image with:
 mkinitcpio -p linux[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]
 reboot"

The thing is i don't know how to do it. I installed using VMware Workstation. How do i use "[/FONT][/COLOR][COLOR=#333333][FONT=sans-serif]mkinitcpio" to rebuild the kernel on the usb and not the the live-iso i booted from?

Edit: And where is this modprobe.conf and mkinitcpio,conf files in Ubuntu?[/FONT][/COLOR]

---

