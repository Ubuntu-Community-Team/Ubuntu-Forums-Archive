---
title: "Ubuntu freezes shortly after startup"
date: 2006-12-10
forum: General Help
---

### Post by Joseph Duchesne on 2006-12-10
Hi,
I just installed Ubuntu 6.10 and it works fine- for a little bit. Unfortunately after a few minutes of use (generally 2-10), the mouse freezes and a little 2px or so graphics glitch appears near it. The keyboard doesn't respond and the computer is completely frozen. Nothing on screen changes or moves. This is quite frustrating and is effectively rendering my Dell Inspiron 5000 useless. 

What could be causing this, and how should I go about fixing it?
Thank You,
Joseph Duchesne

---

### Post by bscbrit on 2006-12-10
First thoughts -

Start in recovery mode and let the computer run for half an hour or so.  If the computer doesn't freeze the bug would appear to be in the software associated with the desktop, graphics or xorg (roughly).  I would suspect the graphics card or memory. Are you overclocking?  

Boot into the Ubuntu memory test and run that.

Ensure that you have updated all security and bug fixes - it might have been noticed elsewhere and fixed.

---

### Post by CRCarl on 2006-12-10
Something to try - 
 
 First take a backup - 
    
       ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```
       Now edit that file

     ```
  sudo gedit /boot/grub/menu.lst
```

Find your default boot line, it will look something like this; 
```

/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro verbose
```

Add to the end on the line so it looks like this - 

```
/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro verbose no_timer_check noacpi acpi=off noapci nolapci
```

Save and reboot. 

Also try piping /var/log/messages to another file so we can see the log right before the machine locks up;

```
tail -n 0 -f /var/log/messages > errors.txt
```

After the machine locks up, reboot and post the last 20 lines or so of that file here.

---

### Post by Joseph Duchesne on 2006-12-10
This is the only error I get in errors.txt:
Dec 10 10:43:06 Archon exiting on signal 15

My Fan doesn't seem to be turning on, would that cause that? It could also simply be that the computer doesn't have time to get hot enough to use it...

How do I start up in those modes? Is that the escape menu at the beginning of booting?

---

### Post by bscbrit on 2006-12-10
Yes, that's the escape menu at the beginning of the boot.  It should allow you to start in Recovery Mode.

It might not be that your CPU is not getting hot enough - it might be getting too hot and shutting down!  Check why your fan is not working!

---

### Post by Joseph Duchesne on 2006-12-10
> **bscbrit said:**
> Yes, that's the escape menu at the beginning of the boot.  It should allow you to start in Recovery Mode.

It might not be that your CPU is not getting hot enough - it might be getting too hot and shutting down!  Check why your fan is not working!

I think that may be it but I'm mystified as to why it would freeze rather than simply turn off like every other overheating computer I have ever used. The fan may be physically blocked from spinning. I'm going to take the bottom casing off and check.

---

### Post by bscbrit on 2006-12-10
Yes, you're probably correct - a shut down is more likely than a freeze but I still wouldn't rule it out.  If the CPU stops your graphics display might simply keep the last data it had.  I don't know much about this so its all speculation on my part.  All the same, get the fan fixed.

---

### Post by Azakus on 2006-12-10
Most relatively modern CPU's will lock up if they overheat so they don't explode. That would give you a freeze up.

---

### Post by Joseph Duchesne on 2006-12-10
I opened it up and it turns out that the fan assembly was cracked this prevented the fan from moving. I removed the piece that was stopping it. The fan now turns on for maybe 2 seconds on startup, something it didn't do before, but the fan then turns off and stays off. The crash/freeze occurs as usual.

Another note: the device manager lists two fans. I only have one.

---

### Post by Joseph Duchesne on 2006-12-12
Well, I've taken everything apart and fixed a few things:
1. The fan was never turning on. I wired it up to a push on, push off switch on the side. This way I can manually turn the fan on and off when I want to.
2. There was no thermal paste. None. Not even the crapy residue that should have been there. I have a feeling that the previous owner didn't like thermal paste. (I got this laptop with a fried motherboard if that's any indicator). I added thermal paste. 

The result:
The computer now runs perfectly cooly(doesn't even get warm let alone hot like it did before) but unfortunately (although the lack of fan and thermal paste needed to be fixed), **Ubuntu is still freezing!**

The only visible indicator is that the mouse gets messed up. It will half disappear and/or get some random noise in its vicinity. What do you suggest I do now?

---

### Post by pdiddy on 2006-12-25
Hi Joseph,
I installed Ubuntu 6.10 a few weeks ago and it was fine for a while too. But now I am having the same problem for the past week with my Dell Inspiron 6000. About 2-3 minutes after logging on, my laptop completely slows down and freezes!!

I can hear something kicking in inside my laptop and its eating up the CPU. But there are no extra processes showing up on the system monitor.

I have started in recovery mode and ran the following commands:
sudo apt-get update
sudo apt-get upgrade
...but it hasn't fixed the problem. (1 package was kept back: "xserver-xorg")

I have also ran the memtest and received no errors. Actually, the memtest ran for hours without my laptop freezing at all. 

So my laptop didn't freeze when I started in recovery mode, or when I ran the memtest, or if I leave the laptop on the login screen without logging in its fine too. Therefore, I feel it must be a problem with the software.

And the fan seems to be working fine so thats not causing the problem either. 

Have you fixed your problem or can anybody else out there please give me some advice?...because my laptop is completely useless right now!

Thanks - Peter

---

### Post by bscbrit on 2006-12-26
I would recommend that you try to use 'dist-upgrade' rather than just 'upgrade' - the former overcomes some problems with xorg updates that the latter doesn't seem to cope very well with.  The problems might well be linked to xorg, especially as there appears to be a mouse glitch at the same time.

Secondly, I use synaptic from time to time rather than command line - I don't know why / how but it seems to solve problems that I have seen similar to those that you are experiencing.  I cannot explain it nor is there any obvious logical reason because they both use the same software for much of the task.  But it is always worth a try. :-)

---

### Post by leeley on 2006-12-26
Just a thought, do you have a mouse attached or are you using a touch pad or both?:confused:  If so have had this setup since loading Ubuntu or have you added to the config.

Lee

---

### Post by Joseph Duchesne on 2006-12-26
I am using an internal mouse.

---

### Post by pdiddy on 2006-12-27
thanks bscbrit,  

i ran the dist-upgrade and my laptop ran for about 20 mins (thats a lot longer than before), but then it started to freeze again. 
 
You said that you use synaptic from time to time rather than command line - do you mean the synaptic package manager - and if so, what should i run in it to try to fix my problem?

Thanks a lot.

---

