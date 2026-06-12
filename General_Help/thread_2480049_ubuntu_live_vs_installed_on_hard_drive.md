---
title: "ubuntu live vs installed on hard drive"
date: 2022-10-17
forum: General Help
---

### Post by gregorystevens on 2022-10-17
hi
if I run ubuntu live from a usb flash drive, would websites that I visit be able to know that I am running ubuntu live and it's not installed on my hard drive?

---

### Post by grahammechanical on 2022-10-17
This my uneducated opinion.

You would still be running Ubuntu through the machine's hardware. The connection to the website would start with Ubuntu and the web browser and then go through the machine's network adapter on to the router/modem and then on to your Internet Service Provider's servers and then through who knows how many Internet servers until it reaches the web site selected.

Regards

---

### Post by #&amp;thj^% on 2022-10-17
> **gregorystevens said:**
> would websites that I visit be able to know that I am running ubuntu live and it's not installed on my hard drive?

Your ISP would/could and who knows how many of the sites you visit would have that capability; 
This returned from a script we use here in UF:
```
The 'system-info' script was booted from an installed system

The 'system-info' script seems to be running locally
```
Yours would show Live, or something like it.
If you want to check follow this: [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
EDIT: Live shows as follows:
```
The 'system-info' script was booted from a Live Image Environment (LIE).

The 'system-info' script seems to be running locally

The Linux Kernel Command Line use to boot was: 
BOOT_IMAGE=(hd0,gpt4,msdos1)/live**/vmlinuz boot=live quiet splash --**
```
***TheFu has it best worded in post#7

---

### Post by C.S.Cameron on 2022-10-18
Use a VPN. I use HideMe

---

### Post by ActionParsnip on 2022-10-19
There is no difference. The browser identifies the OS it is running in and the browser ID. Nothing more

---

### Post by HermanAB on 2022-10-19
BTW the Live versions are horribly slow.  Next time consider doing a normal install on your flash drive or SD card.

---

### Post by TheFu on 2022-10-19
> **gregorystevens said:**
> hi
if I run ubuntu live from a usb flash drive, would websites that I visit be able to know that I am running ubuntu live and it's not installed on my hard drive?

In theory, no, but in practice, every browser has a signature and browsers that haven't been installed have a specific signature that is well known by the tracking services around the internet.  The EFF has a tool that will show you how unique your browser is based on the other browsers they've seen over some period of time.  Google will find that tool easily.  Run it with any browsers you like to get a feel for unique aspects.  Between the IP, which provides a general location and the 50 browser things they can see (like battery level, canvas size, screen size, resolution, ..... ) our broswers are fairly unique.

A VPN can help, but people often use VPNs with bad security that leaks all sorts of other information ... including the browser signature, so if you mix the use of the browser with and without a VPN, they will know it is you.

Being anonymous on the internet isn't easy. 1 tiny mistake can screw it up.  These things are part of OPSEC, which can be fun to read up about.  OPSEC is hard and even the CIA fails in some really dumb ways from time to time.  Some of their failures are in a weekly FBI podcast.  [https://www.youtube.com/watch?v=bM0PmwOlifE](https://www.youtube.com/watch?v=bM0PmwOlifE) might be interesting. There are many others.

---

