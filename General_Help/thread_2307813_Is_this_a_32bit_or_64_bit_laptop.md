---
title: "Is this a 32bit or 64 bit laptop"
date: 2015-12-28
forum: General Help
---

### Post by michael-piziak on 2015-12-28
Attempting to install Ubuntu on this laptop below
is it 32 bit or 64 bit?  It had Windows 7 vista 32 bit on it
But has an intel core 2 duo

I couldn't get the 64 bit 12.04 lts to boot - it took forver and didn't boot
Now it's taking forever to get a 32 bit 14.04 lts to boot

Just has the Ubuntu with flashing dots on screen like forever

Computer is below:

[http://www.pcworld.com/product/131847/toshiba-satellite-l555-s7916-notebook.html](http://www.pcworld.com/product/131847/toshiba-satellite-l555-s7916-notebook.html)

p.s. I tried to install a 32 bit 12.04 lts on it, and it reported the cd/dvd drive is not connected.

---

### Post by Bashing-om on 2015-12-28
michael-piziak; Hello again .

What tale does:
```

cat /proc/cpuinfo

```
tell ?

[INDENT][INDENT]ask the system
[INDENT][INDENT][INDENT]it does not lie
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by howefield on 2015-12-28
> **michael-piziak said:**
> ...is it 32 bit or 64 bit?  It had Windows 7 vista 32 bit on it..

Looks like 64 bit capable.

> Just has the Ubuntu with flashing dots on screen like forever

Try pressing the escape key to reveal the text boot process, you may get a clue on the screen as to what is happening.

---

### Post by oldfred on 2015-12-28
My old laptop from 2006, purchased just days before the release of Vista in Jan 2007, has core2 Duo and in 2009, I converted to 64 bit.
But video is so weak that full Ubuntu will not run. I have 12.04 on it and still use it, sometimes. But am about to retire it as my new desktop is so fast compared to the old laptop.
To get laptop usable I had to install fallback/flashback/gnome-panel. Full Unity just required too much graphics horsepower.
Others may suggest Lubuntu or Xubuntu as lighterweight GUI.

       But fallback discontinured but rename flashback very similar
[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

            [https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)
    This is what I used, but similar procedures for 14.04 which I use on my new system.
 12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
      
 sudo apt-get install gnome-panel
sudo apt-get install gnome-tweak-tool

---

### Post by michael-piziak on 2015-12-28
A lot of I/O errors and No Medium Found over and over when pushing escape using 14.04 lts 64 bit boot drive.

The 32 bit version of 14.04 lts will install.

But do any of you think I should just go with Xubuntu or Lubuntu on this old computer.

I'm fixing it for a date I had.

---

### Post by matt_symes on 2015-12-28
Hi

> **michael-piziak said:**
> A lot of I/O errors and No Medium Found over and over when pushing escape using 14.04 lts 64 bit boot drive.

The 32 bit version of 14.04 lts will install.

But do any of you think I should just go with Xubuntu or Lubuntu on this old computer.

I'm fixing it for a date I had.

As howefield said, the CPU is definitely 64-bit capable and will run a 64-bit OS.

It sounds like you may have a corrupted 64-bit image or a problem with some of the laptop's hardware.

Are you installing using a USB stick or a CD/DVD ROM ?

Anyway, as for Xubuntu or Lubuntu, the laptop I'm posting this post on is an older laptop than your laptop and it runs 64-bit Xubuntu just fine. It does have 4G of memory.

```

matthew-xu-16-04:/home/matthew:0 % grep -m1 "model name" /proc/cpuinfo
model name      : Intel(R) Core(TM)2 Duo CPU     T7250  @ 2.00GHz
matthew-xu-16-04:/home/matthew:0 % 
```

Kind regards

---

### Post by michael-piziak on 2015-12-28
The 64 bit version of 14.04 lts is installing quite smoothly after a very long initial wait to get to the first screen.

An ocassional error came up - error reading the medium, I chose "ignore" and it continued oni it's merry way.

I'll keep everyone updated if it works and if it is fast enough - she just wants to do facebook.

One of my missions, in life, is to install Ubuntu for free on anyones system that has a computer that has come to a screeching halt because of that OTHER operating system!

I have installed ubuntu on about 15 computers for other people.

Michael

These terminal codes won't work until I can get a full install.

My last attempt was with a sandisk 14.04 lts and when I thought all was going ok, it got stuck in the middle of the major install.

So I formatted another sandisk usb and am installing again, hoping the first sandisk is corrupt thumb drive.

But I can't get to terminal yet.

---

### Post by matt_symes on 2015-12-28
Hi

> **michael-piziak said:**
> These terminal codes won't work until I can get a full install.

My last attempt was with a sandisk 14.04 lts and when I thought all was going ok, it got stuck in the middle of the major install.

So I formatted another sandisk usb and am installing again, hoping the first sandisk is corrupt thumb drive.

But I can't get to terminal yet.

There's no real need to get to a terminal as your CPU is 100% 64-bit capable. 

My terminal command output was for your informational purposes, so that you could see that your CPU chip is newer than mine.

If you want to be convinced that your CPU is 64-bit capable then run this modification of Bashing-om's command (copy and paste into the terminal) and look for *lm* in the output.

```
grep -owm1 lm /proc/cpuinfo
```

Here's what the output will look like on a 64 bit capable machine.

```

matthew-xu-16-04:/home/matthew:0 % grep -owm1 lm /proc/cpuinfo
lm
matthew-xu-16-04:/home/matthew:0 %
```

There are other commands that will tell you the CPU type but your CPU is definitely 100% 64-bit capable.

Good luck with the installation.

Kind regards

---

### Post by efflandt on 2015-12-28
If you try to boot 64-bit Ubuntu on a CPU that is not capable, you would get some sort of error like "Trying to boot X86_64 on i686". So if it boots at all with a 64-bit Ubuntu version, it should be capable.

Both a Dell laptop from 2005 and Toshiba laptop from 2006 with core 2 duo were 64-bit capable (both have 2.5 GB RAM). But the Toshiba is dead slow for games due to integrated Intel graphics, the Dell has faster legacy ATI X1300 mobile graphics. Only a low end Compaq from 2005 that a friend had was not (it had a Sempron which then was an Athlon64 crippled to 32-bit). My old HP desktop from 2004 was one of the first 64-bit capable PCs, it has an early Athlon64 3200+ (2 GHz) and also ATI X1300 graphics. Although, I have not booted any of those lately.

---

