---
title: "Edgy shutdown freeze"
date: 2007-01-08
forum: General Help
---

### Post by VoodooSteve on 2007-01-08
I recently upgraded to Edgy from Dapper. Now when I select to shut down the computer, I see the Ubuntu logo and the progress bar going backwards. But, when it reaches the end, and I hear "most" of the hardware in my computer shut off, the logo and empty progress bar remain on the screen indefinitely. Any ideas?

---

### Post by hardyn on 2007-01-08
hardware?  ATI video by chance?

need WAY more info (hardware).

---

### Post by VoodooSteve on 2007-01-08
I am currently running a P3 1GHz, 256MB RAM and a nVidia GeForce4 MX 440 64MB. Need any more info?

---

### Post by FloEppo on 2007-01-09
What happens if you open console and you issue a :

```
sudo shutdown -h now
```

---

### Post by ckroeker on 2007-01-09
I have the exact same issue.

My hardware is: a PIII 500 with 192MB of RAM and a 10GB harddrive, integrated CM8738SWIEC audio, integrated intel 82810 graphics, a usb mouse and ps2 keyboard.

I tried: > sudo shutdown -h now with no new response from the system.

Any more ideas?  Thanks.

---

### Post by Nikola.srb on 2007-01-09
I have exactly the same problem ...  after unloading of kubuntu comes to the end, hard drives turn off, but cooler on CPU is still working, so I need to turn it off with power button :(

any ideas ?

---

### Post by hardyn on 2007-01-09
they are all older machines, what about booting with with the acpi=no option? (you will have to check accuracy of my syntax, should be all over the forum).  I have had trouble with old machines not shutting down, even with windows 2000.

---

### Post by ckroeker on 2007-01-10
Hi again,

Unfortunately turning acpi off does not fix the problem... thanks for the suggestion though!  Other tips or ideas?

---

### Post by FloEppo on 2007-01-11
Yes, I noticed that. Turning off acpi won't solve the problem. It advances (I have a blinking cursor now instead of the ubuntu empty progres bar) but still no shutdown. Maybe anyone have an idea what can cause this?

---

### Post by FloEppo on 2007-01-12
Nobody has any idea? That's really weird. I have 2 other distro installed (Slackware 11 and Fedora Core 6) and none of those have this problem on the same machine. It makes you think, eh?

---

### Post by Nikola.srb on 2007-01-13
It's rather wierd that this problem can stay unsolved forever...   I know few more people with same problem on Edgy, so it's not that rare thing.   But it's anoying to have to wait beside your machine to turn it off.  I cant use any automated shutdown becouse it wont work...
pls help us !

---

### Post by Akita on 2007-01-13
Please, lease, please file an official bug report. Countless things like this get beaten to death here and the developers never hear about them.

The closest I found doing a quick launchpad search was: 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43961]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/43961")

That's a confirmed kernel (upstream) bug in Dapper.

File &| look for bugs here: [https://bugs.launchpad.net/ubuntu]("https://bugs.launchpad.net/ubuntu").

---

### Post by NoWhereMan on 2007-01-13
acpi=force ?

---

### Post by FloEppo on 2007-01-17
Just wanted to let you guys know that I have solved this problem on my machine. In my case was module snd_hda_intel . If this is unloaded before the "poweroff" command then system will shutdown normally. Issue a "rmmod snd_hda_alsa" in the rc.X file before the "poweroff" and machine will shutdown as it should be. It appears that this hangs up in X at exit. The problem does not occur if X is not started (e.g. boot with recovery mode and then issue a shutdown -h now or poweroff).
As I said, in my case was that specific module, who know, maybe this helps.

---

### Post by notfalling on 2007-01-27
Hi, I was able to correct this on my older Athlon (850 socket-a) by adding acpi=force to my menu.lst file.

```

sudo gedit /boot/grub/menu.lst

```

Replace this:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet  splash

```

With this:

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro **acpi=force** quiet  splash

```

Now my computer shuts down and powers off like it did with Breezy. :)

Hope that helps someone!

---

### Post by shakma on 2007-01-30
I can't remember who posted this, but I found this a while ago, and it worked for me today on my HP Pavilion ("old machine").

"in my case, the following solved the issue:
1. gksudo gedit /boot/grub/menu.lst
2. add "acpi=force" at the end of kernel line, eg from my old menu.lst:
kernel /boot/vmlinuz-2.6.15-25-k7 root=/dev/hda1 ro quiet splash acpi=force
3. save and exit gedit
4. after the restart, it should work

I did it in Dapper, and have to do that in Edgy with every kernel change"

This worked for me *exactly* as stated.  Thanks to whomever originally posted it!  Ubuntuforums forever!

Peace.

---

### Post by ckroeker on 2007-01-31
Thank you to NoWhereMan, notfalling, and shakma for their "acpi=force" suggestion - it fixed this bug for me.  Yay!  No more sitting there holding down the power button!

-c

---

### Post by Redeyes_Gambit on 2007-02-14
No Joy here sadly. Forcing the ACPI made the drum start up sound play endlessly and then the system freezes LOL.

Make sure you backup your grub menu.lst BEFORE making this modification!

---

### Post by jmeuf on 2007-02-17
Hi,

my PC is quite recent (ASUS P5AD2 Deluxe, Intel 3,6GHz) and was properly switched off under Dapper. But now I can't do it under Edgy. I tried the 'acpl=force' trick without success.

Keep in touch.

---

