---
title: "Cannot install Ubuntu!! PLEASE HELP!!"
date: 2007-04-06
forum: General Help
---

### Post by D!mon on 2007-04-06
I'm trying to install ubuntu 6.10 on my computer that is Core 2 Duo E6400 2,13 GHz (2048kB) 1066MHz Socket 775 Box; motherboard PGA775 P-IV i965Q Intel DQ965GFEKR

The problem is that when I load from boot cd it fails with message
```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

I tried everything I could find here on this forums, particularly recommendations from this topic: [http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688)
I tried to boot with all options listed there but no success I keep getting that weird message:((

After that I tried Edgy alternate CD, but after it detected my keyboard it said that "No common CD-ROM drive was detected". I started googling again but failed to find a solution:(
The old debian3.1ra disc gave me the same result.

I changed my dvdrom to the old cdrom from another computer but no success; tried to set up 'legacy' mode for ide drives in bios, the same((

Also I tried booting up from kubuntu 6.06 disc that I ordered on shipit, but computer just hang up :(

It seems that these are common bugs even in Fiesty cds, so is there any solution??
I DO NEED to install ubuntu on this machine, otherwise I'll need to bye another licence from microsoft and stick with windows because it's my work computer

PLEASE HELP, I believe there is a way to solve this problem!!!! Feel free to email, icq, msn or skype me if you want.

Thanks,
Dmitry

Upd: On mirc channel someone said me that JMikron IDE controller (not sure if I have one, the guy with the similar computer does have one) is not supported in 6.06 and 6.10 but I was banned from mirc with message "Open Proxy found on your host" ((
Steel waiting for suggestions! 
Will it be possible to boot from floppy, flash card or usb cdrom??
Here is the link to my motherboard description maybe it will help to find the problem [http://developer.intel.com/design/motherbd/gf/gf_available.htm](http://developer.intel.com/design/motherbd/gf/gf_available.htm), DQ965GFEKR section.

---

### Post by bapoumba on 2007-04-06
@ D!mon: i've moved you exact duplicate thread out of the way.

---

### Post by D!mon on 2007-04-07
any suggestions?
is it possible to install ubuntu from flash card? Or if I'll make clean install on another computer will it work on this computer? Maybe it will work if I'll upgrade kernel when installing on another computer or something like that?

---

### Post by ubu-for on 2007-04-07
> **D!mon said:**
> Or if I'll make clean install on another computer will it work on this computer?

No.

> **D!mon said:**
> Will it be possible to boot from ... usb cdrom??

Perhaps.

> **D!mon said:**
> I changed my dvdrom to the old cdrom from another computer but no success

So it looks like that your mainboard is incompatible with Edgy.

Maybe you try the following.

1. Update your mainboard BIOS

2. Use another IDE port on your mainboard for your CD-ROM

3. Use another IDE cable 

4. Alternative OS: [Ubuntu 7.04 Beta](http://releases.ubuntu.com/feisty/), [Xubuntu 7.04 Beta](http://cdimage.ubuntu.com/xubuntu/releases/feisty/beta/), [Knoppix](http://knoppix.ru/), [openSUSE 10.2](http://download.novell.com/Download?buildid=aAFbhfBgdYM~), [Fedora](http://rhold.fedoraproject.org/Download/mirrors.html)

---

### Post by strabes on 2007-04-07
Have you tried the alternate install CD?

---

### Post by ubu-for on 2007-04-07
> **strabes said:**
> Have you tried the alternate install CD?

Yes. ;-)

> **D!mon said:**
> After that I tried Edgy alternate CD, but after it detected my keyboard it said that "No common CD-ROM drive was detected".

---

### Post by D!mon on 2007-04-07
> **ubu-for said:**
> No.



Perhaps.



So it looks like that your mainboard is incompatible with Edgy.

Maybe you try the following.

1. Update your mainboard BIOS

2. Use another IDE port on your mainboard for your CD-ROM

3. Use another IDE cable 

4. Alternative OS: [Ubuntu 7.04 Beta](http://releases.ubuntu.com/feisty/), [Xubuntu 7.04 Beta](http://cdimage.ubuntu.com/xubuntu/releases/feisty/beta/), [Knoppix](http://knoppix.ru/), [openSUSE 10.2](http://download.novell.com/Download?buildid=aAFbhfBgdYM~), [Fedora](http://rhold.fedoraproject.org/Download/mirrors.html)


Yes, I found quite a lot information about problems with motherboard like mine, even here at ubuntuforums. It seems that this motherboard will work only with 2.6.19 kernel oh higher..  (( I'm really disappointed that my new computer is incompatible with ubuntu((
Possibly I'll try to install debian or fiesty beta tomorrow. But I'll have access to fiesty repo only after release and I can't wait for it because I need working computer now.

But why it won't work if I'll make install at another computer? Isn't it just IDE controller problem?
Possibly I'll try to insta

---

### Post by D!mon on 2007-04-08
Finally I tried to boot from my home sata disk with Edgy 64 installed and whoa it worked!
Don't know if dvd worked well but network video and sound did! And no problems with booting up the system.
Anyway I'm going to install Fiesty Beta amd64 now; live cd works great and even desktop effects work fine from live cd
btw, I tried debian etch, mandriva 2007.0 and OpenSuse 10.2; only OpenSuse was able to load from live cd.

---

