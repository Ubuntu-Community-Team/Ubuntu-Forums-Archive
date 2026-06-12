---
title: "LIRC not functioning on boot but I can manually get it working"
date: 2007-09-25
forum: General Help
---

### Post by efface on 2007-09-25
Well after many hellish hours of tweaking Lirc, I finally got it working, irw returns my remote commands!!

Then I rebooted....ruw row

So after some tweaking some more I found that these commands got it working again.

sudo killall -9 modprobe
sudo killall -9 lirc
sudo lircd --device=/dev/lirc0

(yes I realise this is a very sloppy way to resolve the issue)

I changed in lircd.cong the device= section to /dev/lirc0 but it did not help.

Can someone please provide me a solution.  I use this box as a media PC and the whole point is to not have to bust out the keyboard :P

Thanks in advance.

BTW I am using the lirc_atiusb module and have followed the directions to have them compiled into my kernel.

---

### Post by pointone on 2007-09-25
Make sure you're starting it as root, and if you are, make sure you have the .lircrc file in /root.

---

### Post by efface on 2007-09-25
.lircrc only contains information for what program and command to be given for what button.  Do you mean lircd.conf?

---

### Post by orbish on 2007-09-25
No experience with LIRC, but from what i'm hearing, maybe it didn't compile into the kernel correctly?

If it's a module, add it to /etc/modules, restart, see if that does anything.

My stab-in-the-dark.

---

### Post by efface on 2007-09-25
lsmod shows that lirc_dev and lirc_atisub are loaded, I cannot rmmod them as it states they are busy.

Hence I killall -9 modprobe and it kills those modules for me.

---

