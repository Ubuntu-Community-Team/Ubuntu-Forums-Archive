---
title: "System Freeze (Hotplug)"
date: 2005-10-19
forum: General Help
---

### Post by nudnick on 2005-10-19
I've decided to go ahead and make the switch on my laptop to Linux. My friend told me that Ubuntu was the best route for a Linux newcomer. A few months ago I ordered a CD and proceded to install it on my laptop. After some fuss (wouldn't recognize my PCMCIA or CDROM) I got it installed but I couldn't get it to boot all the way. It would always freeze on the "Loading Hotplug system". I tried a few things my friend reccomended but no suffice. I decided to wait until Breezy Badger came out and tried again. I just installed Breezy and I still get the same problem as before, except this time it did recognize my PCMCIA and CDROM. I was hoping someone with more knowledge than myself could help me out or point me in the right direction.

My laptop is a Sager NP3880-V

---

### Post by nudnick on 2005-10-21
I talked to someone and they told me to preform the following to disable PCMCIA.

Add "init=/bin/sh" to the end of the kernel line in GRUB and boot.

When the command prompt comes up I was told to put this in:

mount /proc
mount -o,rw /
mv /etc/init.d/pcmcia /etc/init.d/pcmcia.disabled
sync
mount -o remount,ro /
reboot -d -f -i


When I typed in "mount -r,rw /" I got the following mesage:

/dev/hda2 already mounted or / busy
According to mtab, /dev/hda2 is already mounted on /

I proceded to the next step "mv /etc/init.d/pcmcia /etc/init.d/pcmcia.disabled" to get the following message:

mv: cannot move '/etc/init.d/pcmcia' to '/etc/init.d/pcmcia.disabled' : read-only file system

Did I do something wrong?

I tried removing "ro" from the kernel line and I still get a read-only message...

---

### Post by ymmotrojam on 2005-10-21
Speaking of this, mine does something that isn't directly harmful in any way, but it pauses for a second or two at the hotplug when booting... It doesn't say whether it failed or was ok... it's just blank and it continues on to the next thing.

---

### Post by nudnick on 2005-10-21
Someone has got to know how to get around this. I've been struggling with this for the past few days - any assistance would be greatly apreciated.

---

### Post by Tsume on 2005-10-22
Same problem 75% of the time on a Dell Latitude CS.

Disabling PCMCIA is not a solution as I need it for my internet.  This laptop doesn't have onboard wireless OR ethernet OR a modem.

---

### Post by jarturoar on 2005-10-22
what about passing the noapic parameter in the boot?

---

### Post by Dajazzz on 2005-10-22
Hi 

I have a DELL LATITUDE LS (500Mhz)
I also have sometimes this problem. (no matter breezy or hoary)

i just restart my laptop and then its mostly working fine....
BUT WHY DOES IT ALWAYS HAPPEN WHEN I'M SHOWING MY UBUNTU TO SOMEONE ELSE????

---

