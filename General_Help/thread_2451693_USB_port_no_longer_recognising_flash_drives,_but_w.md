---
title: "USB port no longer recognising flash drives, but working otherwise"
date: 2020-10-09
forum: General Help
---

### Post by lesliek2 on 2020-10-09
I use Ubuntu 16.04.

One of my USB ports has just begun to give me trouble. Until now, it worked fine.

Now, it works to charge the battery in my wireless keyboard. It also works normally when I plug in my usb hard drive.

However, it will not recognise my flash drives anymore. I've tried two different flash drives. Neither is recognised. However, if I plug either of them into my wife's computer (a Mac), the flash drive works as normal. The same applies to my Kindle.

Any suggestions gratefully received.

Leslie

---

### Post by TheFu on 2020-10-09
Use a different USB port on the same system
or
use different USB flash drives. They do wear out.

---

### Post by lesliek2 on 2020-10-09
Thanks for taking the trouble to reply TheFu. Since the flash drives and the Kindle are recognised when plugged into another computer, I believe that none  can have worn out.

---

### Post by ActionParsnip on 2020-10-09
When you unplug a USB storage do you use the safe remove feature in the OS before you physically unplug the device?
What file system do you use on your USB storage?

---

### Post by TheFu on 2020-10-09
> **lesliek2 said:**
> Thanks for taking the trouble to reply TheFu. Since the flash drives and the Kindle are recognised when plugged into another computer, I believe that none  can have worn out.

The USB connections may be wearing out inside the ports on your Linux machine.  

Another test would be to boot from any Ubuntu/Fedora/TinyCore ISO installer and choose "Try XXXXX". This will provide a live environment off the installer. How does the problem flash storage work then?  

Can you boot some non-Linux OS in that way and test too?  Perhaps Windows?

The goal is to simplify and test until the problem is understood. We begin with "it doesn't work" and need to determine the "it doesn't work when x, y, z, a, b, c are true."  Just "it doesn't work" is very nebulous.

What about other USB devices - do webcams, 3.5inch storage with power, usb microphones work on the same port?

Is the problem port USB3-A or USB3-c or USB2?  Try other ports.  Make a chart for what works and what doesn't work.

As asked above, which file systems work and which do not?  Some file systems need libraries added. They aren't standard on Linux.  exFAT is 1 example that needed a package installed to work at all on 16.04.  I don't have any exfat storage here - MSFT used to have nasty copyright and patents for that file system, so I've avoided it.  That changed about a year ago - not bad now - unless you want native POSIX permissions (which I do).

---

### Post by Autodave on 2020-10-09
I run into the same problem quite often.  What I have done to alleviate a lot of the problem was to purchase a *powered* USB hub.  I plug all of my USB sticks into that.

---

### Post by lesliek2 on 2020-10-09
I always unmount before unplugging.

I don't know which file system(s) I use. All I can say is that until a day or two ago, I could use the same flash drives, not only on a computer running Ubuntu 16.04, but also on one running Windows 10 and Mac 10.14. I believe that means that I'm using an ancient Windows file system, FAT 32? I seem to recall that name.

---

### Post by lesliek2 on 2020-10-09
TheFu, you made me realise something. The computer that I mainly use and the one on which I'm having the problem can also be booted up in Windows, so I did that. I had exactly the same problem with the flash drives! That made me think that the problem might be at the booting-up stage, maybe some problem caused by a recent power outage. (I get quite a few of those, living in the country, as I do.) I had a look at the BIOS settings, hoping there were some USB settings that got scrambled that I could change, but there weren't. Maybe they don't have those in newer BIOSes.

I'll try to boot up in some other Linux distribution (I think I have some CDs somewhere that I can boot from) and see whether the flash drives are recognised in it.

Thanks again.

---

### Post by TheFu on 2020-10-09
USB connectors wear out all the time.  USB controllers fail too.  I've seen both.

---

### Post by helen314 on 2020-10-09
Just out of curiosity - define "port not recognized".
I assume you do mean port and not specific USB device.

Can you "see" / identify the port and device  on Linux using "lsusb" ?

Any change you are unwillingly exceeding USB port power rating ?
( don't get offended but you stated you do not know your OS )



Some of the "old wife's tails"  ( saying, not political statement ) about 

"remove in software " before un-plugging was probably true in (experimental) USB 0.0 version.

Plugin-in devices plugs SELDOM wear out under normal daily usage. 
"Memory sticks" USB life span is limited until NEXT bigger memory chips are invented -
perhaps few years.

---

### Post by The Cog on 2020-10-09
Normally, when you plug something into a USB port, a number of messages are appended to /var/log/syslog. Try this:

1) Open a terminal and run "sudo tail -f /var/log/syslog" then press enter a few times to gain some blank space.
2) Insert the USB stick and observe the new events being logged
3) Try again with another usb port. See if there is any difference between the working and the problematic ports.

Post the results here. Any error messages or differences is particularly interesting of course.

---

### Post by TheFu on 2020-10-09
I always use **dmesg -w**.  syslog does have the same information, but it is just more to type, gets other stuff mixed in, and I'm lazy. ;)

In a soon-to-happen linux release, dmesg will require sudo. Seems some slightly sensitive data may get into dmesg files.  Decades ago, most /var/log/ files required root to view, so the sudoers would be setup to allow view-only access to specific people. Looks like we're headed back to the olden days. Perhaps the old guys new some stuff after all?

---

### Post by lesliek2 on 2020-10-09
When I inserted the flash drive into the port that's causing the trouble, nothing at all was added to the output.

I'm thinking that those who've tried to help me with this will brand me a coward, but I'm giving up on this, for a reason I'll explain.

My computer has three USB ports. One was occupied by a dongle for a Logitech wireless mouse, another by a dongle for a Logitech wireless keyboard and the third one is the one that's causing me the trouble. I found a program called Solaar that allowed me to use one of the two dongles for both Logitech devices. The USB port freed up by omitting one of the dongles works as it should, so I can ignore the one that only works with my external hard drive and with my charging cable for my wireless keyboard and not with my flash drives.

In practical terms, I'm back where I was before one port went funny.

Thank you again to those who tried to help.

---

