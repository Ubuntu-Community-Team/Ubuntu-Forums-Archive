---
title: "Live CD using UCK: How to Include Personal Data Files"
date: 2014-04-21
forum: General Help
---

### Post by scrollheaven on 2014-04-21
I've been messing with UCK (Ubuntu Customization Kit) for the purpose of making a LiveCD to do my online banking with. 

I figured out how to include KeePass2 in a LiveCD. But how do I put my KeePass2 data file with my passwords in it on the desktop of the LiveCD?

I can't find this information anywhere in the forums or in Google searches.

---

### Post by scrollheaven on 2014-04-24
Turns out UCK is neither the simplest solution nor the most up to date. The easiest way to get bootable media with a password manager is to use a USB flash drive, 8 GB or more. Then use one of Pendrive Linux's installers or use the Startup Disk Creator in Ubuntu. I used the latter (in a Ubuntu Gnome 14.04-LTS guest on a Windows 7 host in VirtualBox)  and setup a persistence file of 4GB. Once you have your bootable flash drive all set up you can copy and paste documents like a password file to the root level of the flash drive; when you boot off the flash drive they'll appear in /media/cdrom and you can copy and paste them somewhere in your home directory if needed. So far as using KeePass2, once you boot off your flash drive you can open the Ubuntu Software Centre and install KeePass2 with a couple of mouse clicks. I originally tried using apt-get in the terminal, which doesn't work too well, but Ubuntu Software Centre gets the job done;-)

---

