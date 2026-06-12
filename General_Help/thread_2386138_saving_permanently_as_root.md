---
title: "saving permanently as root"
date: 2018-03-01
forum: General Help
---

### Post by Hat-trick on 2018-03-01
My VAIO has a backlit keyboard but I lost the functionality with the Trusty release a couple years ago. No big deal.  If I want to turn it on temporarily I just open a terminal and type

```
gksudo gedit '/sys/devices/platform/sony-laptop/kbd_backlight'
```

Then I change the value in the file and save. Now I have a functioning backlight.  But it's only temporary and the value reverts back on the next reboot.  Is there any way to make these changes permanent?

---

### Post by cruzer001 on 2018-03-01
And what are you running these days?  Still on Trusty?

My Dell laptop has keyboard light settings built into BIOS (25, 50, 75 and 100%).  Maybe Sony does too?

I have nothing in /sys/devices/platform/ but I'm on the new Gnome and I expect its different from yours.

---

### Post by Hat-trick on 2018-03-01
I have the latest LTS ubuntu 16.04.3

Unfortunately there's nothing in the BIOS with those settings.  I dual boot Win 8 and the keyboard lights up every time in Windows. I think what I'm looking for is a script that gets executed at boot. I have no desire to recompile the Linux kernel and play with the defaults

---

### Post by kerry_s on 2018-03-01
what do you change using gedit? i'm sure it can be automated with a command placed in rc.local

---

### Post by cruzer001 on 2018-03-01
I had a look around and this one thread seems to be the most promising.  Maybe with a bit of experimenting you can make it work.

[https://ubuntuforums.org/showthread.php?t=2167787](https://ubuntuforums.org/showthread.php?t=2167787)

Good luck

---

### Post by steeldriver on 2018-03-02
Yes that's the way to do it - you can't save anything "permanently" in /sys because it's a RAM based filesystem so any changes will be lost on reboot

Note that 16.04 might not run rc.local by default, it's possible you will need to enable the rc-local.service unit

---

### Post by Hat-trick on 2018-03-03
> **kerry_s said:**
> what do you change using gedit?

a text file with a number value.  the default is -1.  I change it to 1 and the keyboard light works again.

> **steeldriver said:**
> Yes that's the way to do it - you can't save anything "permanently" in /sys because it's a RAM based filesystem so any changes will be lost on reboot

Note that 16.04 might not run rc.local by default, it's possible you will need to enable the rc-local.service unit

So what are my options?

---

### Post by SeijiSensei on 2018-03-03
I'm using the Kubuntu 18.04 beta, and I didn't need to activate the rc.local service.  I just put the command I wanted to run in /etc/rc.local like I have for years.

OP, try editing the file /etc/rc.local as root with sudo and put this command in the file above any "exit 0" line that might be there already:

```
echo '1' > /sys/devices/platform/sony-laptop/kbd_backlight
```

You don't need sudo since rc.local is run with root privileges.

---

### Post by Hat-trick on 2018-03-03
> **SeijiSensei said:**
> I just put the command I wanted to run in /etc/rc.local like I have for years.

Wow, that worked! I never thought I'd see this day.  Thank you, brother!

---

