---
title: "Fixing Kpilot sync with palm PDA in Ubuntu 7.04 'Feisty'  (and others)"
date: 2007-10-13
forum: General Help
---

### Post by martinbendle on 2007-10-13
I use Kpilot to keep my palm up to date with my computer (and visa versa), and have run into trouble many times with getting it to work.

This appears to apply to Ubuntu Feisty, Edgy and possibly others, along with other distros (Fedora 7 being one)

From what I can tell, the vast majority of problems can be fixed by doing the following first:

load the visor module (not loaded by default in Feisty for me), the lack of the visor module stops /dev/ttyUSB# from showing up, (I spent hours trying to find a more complicated cause for my problem, and few posts mention to check for visor):

[FONT="Courier New"]sudo modprobe visor[/FONT]

make sure that you have linked the ttyUSB0 or ttyUSB1 (in /dev/)  to /dev/pliot (technically i think you're 'sym' linking in the other direction, but, either way, it works):

create the file /etc/udev/rules.d/10-local.rules with the following content (all on one line):  

BUS=="usb", SYSFS{product}=="Palm Handheld*", KERNEL=="ttyUSB[13579]", SYMLINK+="pilot", NAME=="%k", GROUP=="wheel",  MODE=="0666" 

this command should do it (for those that would like to cut and paste it, rather than fiddle with an editor):

[FONT="Courier New"]sudo echo "BUS==\"usb\", SYSFS{product}==\"Palm Handheld*\", KERNEL==\"ttyUSB[13579]\", SYMLINK+=\"pilot\", NAME==\"%k\", GROUP==\"wheel\",  MODE==\"0666\"" > /etc/udev/rules.d/10-local.rules[/FONT]

(note that it is likely that not all of the options are essential, but this works fine for me.  If you suspect that too many options is your problem, I would suggest removing them from the last one and work backwards one at a time)

Then just make sure that kpilot is looking for the device /dev/pilot (Settings > Configure Kpilot > Device  and set "Pilot Device" to "/dev/pilot") and that all the other settings (though the gui in kpilot) are how you would like them.

If this doesn't work... then (and only then) start looking for something more complicated.

Best of luck, and I hope this helps.

---

### Post by Triskal on 2007-10-15
In addition to the above, I have had to do the following with my Treo 680.  The order is important.

1.  Plug Treo into USB
2.  sudo rm -f /dev/ttyUSB?
3.  Open KPilot
4.  Press Sync button on the Treo

It starts syncing automatically.  You'll probably have to kill the kpilotDeamon before/after this process in order for it to work smoothly each time.

---

### Post by Bogzla on 2007-10-16
I've been trying to get my 680 and kubuntu / kpilot to play together for an age

Finally i can sync without booting the windows partition

I had to follow both bits of advice (if I didn't follow triskal's steps all I got was an input/output error in kpilot)

Big thanks :D

---

### Post by crusty_collins on 2007-10-24
I am not an expert but I think that "ttyUSB[13579]" is really a regex character class.  Since the palms use two ports.   So this would select 1 or 3 or 5 etc ?

---

### Post by crusty_collins on 2007-10-24
Also, in 7.04 there are already rules for some of the palms.  I commented the existing ones out in 60-libpisock.rules and 60-symlinks.rules

THE ABOVE IS WRONG.    DO NOT EDIT THESE TWO files.

While everything worked once after my edit I could not get synced up today.

This is what I ended up with.

custom rules.

BUS="usb", SYSFS{product}="Palm Handheld*", ATTRS{product}=="Palm Handheld*|Handspring *|palmOne Handheld", KERNEL="ttyUSB[13579]", NAME=="%k", SYMLINK+="pilot", GROUP="wheel", MODE="0666"

---

### Post by skyjacker on 2007-10-24
martinbendle, I have tried for 4 months to get my Palm to sync. All I needed to do was "sudo modprobe visor" to get mine going. THANKS for the advice.:):)

---

### Post by megamania on 2007-10-25
I'm trying to sync my tx with kpilot.

I use wireless connection (net:any), so I'm supposed not to be involved with the USB settings, right?

Anyway, sync (I'm actually selecting the "backup" option) starts but my Palm freezes somewhere close to the end. I've tried this endless times.

Any ideas? I find kPilot and kdePim great, but I really need to get a complete sync...

---

