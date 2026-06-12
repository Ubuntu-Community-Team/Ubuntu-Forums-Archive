---
title: "Console on boot"
date: 2014-01-23
forum: General Help
---

### Post by n-sallis on 2014-01-23
So this is my first post and I'm not sure where it needs to go (feel free to move it if you do). I've been using Ubuntu off and on for the past year or two, and have decided to make my main computer (lenovo y500 laptop) run ubuntu. Everything runs well (though I can't take advantage of the ssd on boot because it boots too fast and the rest of the system is not ready yet and thus just doesn't boot [or so I'm told]). However, when I boot my system, it boots to a black console (the whole screen is black with a white underscore blinking in the corner). It sits there with that for about 30 - 50 seconds and then precedes to boot (this is after the grub menu). I've run several commands from other forums trying to find the problem, and all I've found are some warnings about acpi. Any Ideas?

ps. I can type in the black console (I've tried running startx, but it doesn't seam to do anything)
pss. I'm not dual booting. I'm all on one partition (accept for the swap partition) running unity. My Ubuntu version is 13.10. the linux kernel is the newest (3.11.something I think).

---

### Post by jeanjd63 on 2014-01-23
Hello

I think you can try to open a console : CTRL+ALT+F1 an connect with yours user and password. 
Then you can do :
[B]sudo  apt-get  update
sudo  apt-get  upgrade[/B]
and
**reboot**

---

### Post by n-sallis on 2014-02-03
that doesn't seam to do anything. I'm all up to date. I'm thinking grub might be waiting on some subsystem to load before it caries on with the boot since eventually everything boots up fine, but I have no way of knowing what that subsystem is or how to fix it. My laptop might not be the fastest, but it's certainly faster than my old hp laptop which boots in like half the time my lenovo does, so there's definitly something bad going on. Also, back when I had Windowz my computer would boot in like 3 seconds. I know it was booting from the ssd back then, and that seams impossible with ubuntu in my situation, but I would expect a boot time of less than 30 or 40 seconds.

---

### Post by jeanjd63 on 2014-02-04
You can try this,
On first line of grub you press "e" like "Edit" and on line :
"linux  /boot/vmlinuz......  quiet splash"  you suppress "quiet splash" and boot with CTRL+X or F10.
Now you can see where the boot take many time.

---

### Post by n-sallis on 2014-02-04
looks like it's taking a long time to mount my swap partition to ext5 :( any segestions? I have 8 gb of ram, so I doubt I even use swap much.can I format my swap partition so it dowsn't try to mount that any more or something? or tell it to mount it later. I also have an ssd which I could use as a swap if that would make mounting faster.

---

### Post by jeanjd63 on 2014-02-04
It's not a good idea to put a swap on ssd. You can better suppress this swap if you have 8 Go of memory and you don't use hibernation.
Thirst in /etc/fstab comment the line  of swap (add a # in start of line) and test if the boot is faster :
**sudo  gedit  /etc/fstab **

---

### Post by n-sallis on 2014-02-04
The boot time hasn't improved :( There weren't any errors, but it didn't really help my speed. Also, as before, after the blinking underscore I'm getting a tty1 console requesting login before the gui actually starts up and takes over, which leads me to believe that something is set wrong in some startup file/config file.

---

### Post by n-sallis on 2014-02-13
If this helps, most of the time is spent in the tty1 and sometimes I have to actually use it to log in and then do start to get the GUI going. does anyone have a clue as to why the tty is popping up before the GUI? could it be that something is set wrong or a subsystem is not ready yet? If so, how might I fix the problem?

---

