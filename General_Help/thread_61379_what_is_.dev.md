---
title: "what is /.dev"
date: 2005-08-31
forum: General Help
---

### Post by dninja on 2005-08-31
I've just checked mount and found the following odd entry:
 # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda4             4.9G  2.9G  2.1G  59% /
tmpfs                  94M     0   94M   0% /dev/shm
/dev/hda1              45M   19M   24M  45% /boot
/dev/hda3             477M   47M  430M  10% /home
[COLOR=Red]**/dev                  4.9G  2.9G  2.1G  59% /.dev**[/COLOR]
none                  5.0M  768K  4.3M  15% /dev

why is /dev being mounted on /.dev? and why does it actually seem to be a copy of /dev/hda4 in size but an ls shows it to be the same as /dev?

 I've never noticed this before, can anyone shed any light?

---

### Post by Juergen on 2005-08-31
AFAIK is /.dev the same as /dev on systems without udev, with **all** device-nodes possible.
Maybe Ubuntu needs this while booting, until udev kicks in.

If udev is running you should find in /dev only device-nodes for hardware that has its drivers loaded.

I don't know about the funny mounting, but it seems to work ;-)

---

### Post by dninja on 2005-08-31
[QUOTE=Juergen]AFAIK is /.dev the same as /dev on systems without udev, with **all** device-nodes possible.
Maybe Ubuntu needs this while booting, until udev kicks in.

If udev is running you should find in /dev only device-nodes for hardware that has its drivers loaded.

I don't know about the funny mounting, but it seems to work ;-)[/QUOTE]
 What you are saying does seem to be true, /dev is just what I have loaded, /.dev has everything. It seems odd that udev is supposed to remove the need for a /dev with everything in then recreates one called /.dev.

Can anyone shed any light on why?

---

### Post by Juergen on 2005-08-31
Well, if we don't find an udev guru... ;-)

reading this (probably a bit old): [http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html](http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html)
and this: [http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)

it seems you really need static devices at boot and as fallback for devices that aren't supported by udev (yet).

---

### Post by dninja on 2005-08-31
> **Juergen]Well, if we don't find an udev guru...  said:**
> http://webpages.charter.net/decibelshelp/LinuxHelp_UDEVPrimer.html[/url]
and this: [http://www.gentoo.org/doc/en/udev-guide.xml](http://www.gentoo.org/doc/en/udev-guide.xml)

it seems you really need static devices at boot and as fallback for devices that aren't supported by udev (yet).
 oh well, as long as it isn't some kind of rootkit trying to hide itself away I'm happy with that answer.

Trying to google for /.dev was an interesting task for a while :-)

---

