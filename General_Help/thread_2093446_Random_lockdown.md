---
title: "Random lockdown"
date: 2012-12-10
forum: General Help
---

### Post by zesterer on 2012-12-10
Hi there,

I am new to these forums but have been using Ubuntu 12.10 for about 2 months now. It's been amazing do far, but for one problem. It occasionally freezes or locks down - even the time stops changing, the mouse freezes and all music stops. At first I thought it was a lack of RAM, but I found out with the use of a screenlet that it can do it at as low as 43% RAM usage. It's not happened enough to become a major problem, but it occurs on average once every few hours (but with no clear pattern). I am often not using very CPU/GPU/RAM intensive programs, or doing anything particularly strange. It just locks down and I need to reboot. I can't even do Ctrl+Alt+F2 to open the console and use 'sudo unity' or 'sudo startx' to restart the GUI, so I guess it's an internal problem.

Any ideas anybody? I would be very grateful to receive help on this problem, however small!

Barry Smith

---

### Post by tgalati4 on 2012-12-10
What is the make and model (and age) of your computer?  Older computers suffer from capacitor problems, lifting chips, and general failure of I/O bridges.  These will give the symptoms that you describe.  Of course you can't rule out the power supply either.  In your BIOS you may have a readout of voltages under "Health" or "Performance Monitor".  Check your voltages with a voltmeter.

I had a client that lost his on-board sound on his 5-year old desktop machine.  No problem, put in a $10 sound card and he's good to go.  Two months later his USB ports crap out.  No problem, put in a $10 USB card.  Two months later his machine only boots intermittently.  Put in a new motherboard for $90.  These things happen.

---

### Post by zesterer on 2012-12-11
Thanks for the reply:

I don't think it's a hardware problem, more an internal ubuntu problem, although my computer can get very hot sometimes (the fan doesn't work properly) However, this usually only happens when playing games and other CPU and GPU intensive tasks. Windows 7 never freezes like this, although it can bluescreen due to too much heat. Is this ubuntu a equivalent?

Btw it's a hp intel inside dual core laptop with 1.5 GHz CPU and 2GB ram.

Thanks,

Barry Smith

---

### Post by tgalati4 on 2012-12-11
Open a terminal and run 

```
dmesg | tail -f
```

Go about your normal daily routine and keep an eye on the terminal for error messages to pop up.

Yes, Ubuntu behaves differently to hardware failures than Windows.

But before this, run memtest for 30 complete passes.  This will take overnight.  Memtest should show up in the bootup Grub menu.  If not, then grab any live CD, boot with it and run memtest.  Faulty RAM can also cause issues.

---

