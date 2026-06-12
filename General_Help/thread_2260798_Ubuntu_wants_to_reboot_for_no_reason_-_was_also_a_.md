---
title: "Ubuntu wants to reboot for no reason - was also a problem with windows"
date: 2015-01-14
forum: General Help
---

### Post by lion3 on 2015-01-14
One of the reasons I finally decided to install Ubuntu (besides the fact that we finally have a system that can hold a dual boot) is that windows kept rebooting without warning.

The good news is that Ubuntu is kind enough to ASK if I want to reboot or shut down without automatically shutting down my system, however it keeps acting as if I told it to shut down when I did not.

This happens as often as every 5 minutes at times, other times everything is good for an hour or so.

My system:
My system:OS: Win 7 pro service pack 1 x64 dual boot with Ubunto 14.04
Motherboard: Asus M5a97 le r2.0
Processor: AMD fx8320
Graphics card: ONM xfx1-pl 
Hard Drive: WD blue 1tb
Power Supply: Coolmax I-500
Memory: DDR3 1600 Adata 4gb

Everything on the system is brand new, so it's not a virus, or something similar.

A local shop checked it out and found nothing wrong with the hardware, but thought it could be the motherboard. We replaced the motherboard and that didn't solve it.

I was told to try windows updates, and that stabilized it for a couple days, and now it's back to its old tricks.

Now that it's doing it in Ubuntu as well as windows, I'm hoping that someone can help me figure out what is wrong.

Thanks much!

---

### Post by dragonfly41 on 2015-01-14
I suggest start with testing memory cards. Memory: DDR3 1600 Adata 4gb

There is a memory check in ubuntu boot menu options .. try that

Next .. try running with one of the cards removed (if you have two 2GB cards).

Then if that memory card works swap the two cards to test again to isolate faulty card.
Clean the cards edges before reinserting in slots.

...

Another cause could be hdd temperature causing reboot due to overheating ..

to monitor temperature ..

sudo apt-get install lm-sensors
sudo apt-get install hddtemp

then run sudo hddtemp /dev/sda

or sudo sensors

---

### Post by lion3 on 2015-01-14
> **dragonfly41 said:**
> I suggest start with testing memory cards. Memory: DDR3 1600 Adata 4gb

There is a memory check in ubuntu boot menu options .. try that

Next .. try running with one of the cards removed (if you have two 2GB cards).

Then if that memory card works swap the two cards to test again to isolate faulty card.
Clean the cards edges before reinserting in slots.

...

Another cause could be hdd temperature causing reboot due to overheating ..

to monitor temperature ..

sudo apt-get install lm-sensors
sudo apt-get install hddtemp

then run sudo hddtemp /dev/sda

or sudo sensors

Thanks! 

How do I run the boot option memory check? (I'm totally new to ubuntu, so I'm clueless here.

It's one single 4gb stick, so no ability to install one stick at a time.

Will try the temp monitors too - should I know what to look for, or will it have something as easy to follow as a green/yellow/red area that tells me something is wrong?

The shop allegedly tested the memory & the temps, but I certainly don't mind testing it again!

---

### Post by lion3 on 2015-01-14
On the temp tests, here's what I got:

lion@Dochiel:~$ sudo hddtemp /dev/sda
WARNING: Drive /dev/sda doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/dev/sda: WDC WD10EZEX-60M2NA0:  no sensor
lion@Dochiel:~$ sudo sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +14.9°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       40.18 W  (crit = 125.02 W)

radeon-pci-0100
Adapter: PCI adapter
temp1:        +52.0°C  (crit = +120.0°C, hyst = +90.0°C)

---

### Post by dragonfly41 on 2015-01-14
Temp seems o.k.

With a single 4Gb memory card I guess you can only check that it is securely seated in slot.

When rebooting Ubuntu from the GRUB menu select memtest.

memtester can also be installed to run without need for rebooting.

sudo apt-get install memtester

Might have to consider other options if nothing shows in memtest.

---

### Post by lion3 on 2015-01-18
sudo apt-get install memtester did absolutely nothing, unfortunately.

I also tried using memtest from grub with no luck - I hit shift repeatedly and NOTHING happens. I did find a page that told me how to use memtest and that I needed to install something else (can't find the particulars now as I'm on another machine, and search isn't being helpful) anyway something about changing the timing when it boots. However I did that and still no grub and no memtest. :(

We've also tried: 

Switching out hard drives - happened on both, so not a hard drive problem.
Switching out graphics cards - no luck here either. We DID learn that the graphics card was SUPPOSED to come with a driver cd (it didn't) and finally downloaded and installed correct drivers, but still no luck.
Pulling the CMOS battery and letting that reset. Again, didn't make a difference.

Hubby doesn't think it can be the memory because it's an intermittent problem, but I wonder if he's correct about that?

At this point about the only things we can't rule out (that I can think of) are the BIOS and the memory.

Thanks for your help.

---

### Post by dragonfly41 on 2015-01-18
Just to recap on clues so far .. in a process of elimination .. 

Brand new system.
Random rebooting occurs in both Windows and Ubuntu.
Replaced motherboard. 
Switched hard drive.
Switched graphics card.
Tried CMOS battery.
Not yet run a full memtest.

In addition to BIOS and memory there are other possible causes which might rarely cause reboot.

These are ..

Glitches in power supply.
Intermittent cable connections.

Have you tried running on battery only mode for a while?
Or mains only mode for a while (with battery removed)?

It is just possible that there might be a BIOS virus. 
Perhaps a reflash of BIOS might be another option.  But this requires a bit more technical nowhow and I would leave that for now..

I would still try a long run of memtest.  When you boot up you should see memtest as an option before starting Ubuntu. Also the packages I have installed (viewed through Synaptic Package Manager) are ..
memtester
memtest86+

However .. was the original RAM board retained in the replaced motherboard? If a new RAM board it is unlikely that the fault is there. If not it could still be the root cause.

If this is a new system have you tried changing system under retailer's warranty .. or credit card insurance (credit card company can also be approached if faulty goods bought by credit card)?

---

### Post by dragonfly41 on 2015-01-18
Curious .. I tried searching against each of your (named) hardware components and came across this .. which seems to originate from you ..

[http://www.sevenforums.com/bsod-help-support/357143-possessed-computer-rebooting-constantly.html](http://www.sevenforums.com/bsod-help-support/357143-possessed-computer-rebooting-constantly.html)

> 
My system:
OS: Win 7 pro service pack 1 x64
Motherboard: Asus M5a97 le r2.0
Processor: AMD fx8320
Graphics card: ONM xfx1-pl 
Hard Drive: WD blue 1tb
Power Supply: Coolmax I-500
Memory: DDR3 1600 Adata 4gb


This parallel thread might give other readers some clues.

---

### Post by lion3 on 2015-01-18
Hi again Dragonfly41 and thanks for your continued help.  The problem seems to be getting worse if that's any help in identifying it. LOL! Managed to get it booted all of 6 times today over the past 8 hours. Where before it would most often allow a reboot, now it refuses to boot at all except occasionally. Also, if it helps, the system is more likely to start up after it sits idle for an hour or so.  There is no memtest option at any point when starting ubuntu. I've tried to find it to no avail. There IS an "advanced options" but the only option with that is system recovery. (Which warns me that it will kill all my data.)  Not sure what you mean by battery only mode. It's a desktop, so I'm not sure what battery you're referring to.   The original RAM hasn't been replaced, so that's what I'm considering as the next option.  Hubby had also suggested a possible BIOS virus as something we can look into.  Don't think it's the cables as trying the different hard drives required different cables.  The power supply was tested by our local shop. They didn't notice anything wrong with it.  The system is handbuilt, so no ability to just return the whole system for a new one, sadly.  The computer was originally a used system that had a bad motherboard.   At the time we replaced the power supply and graphics card, but then realized the motherboard was the culprit.  Since then we rebuilt everything - the only original part is the case.  All parts are under warranty (with possible exception of the power supply & graphics card) it's just a matter of identifying WHICH part is the problem and waiting for shipping back and forth.

---

### Post by dragonfly41 on 2015-01-18
You've confirmed that the repair shop swapped the motherboard but did not swap out the memory card. That was daft of them. Go to the shop and ask for a swap out memory card.

I was referring to my laptop which has a battery which should run with power off.  But I now see that you have a tower PC.  So belay my idea.  Incidentally note that having the tower side panel off does not necessarily help with cooling since a closed system can be better .. provided that you've hoovered out any dust from the fans.

You say that the power supply was tested by the local shop.   But did they check from power supply to mains in .. in your tower case?

> 
the only original part is the case.


This makes it much tougher to diagnose since there are many possible single points of failure in a rebuild.

By way of example here is a thread which cites a faulty reset switch causing glitches which cause reboots.

[http://www.tomshardware.co.uk/answers/id-1792345/computer-randomly-restarts-bios-replacing-ram-power-supply.html](http://www.tomshardware.co.uk/answers/id-1792345/computer-randomly-restarts-bios-replacing-ram-power-supply.html)


[B]
[later edit][/B]

Here is one thread explaining how to install memtest.

[http://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu](http://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu)

---

### Post by dragonfly41 on 2015-01-18
Further thought before I sign off for today.

You could create a live USB flash copy of Ubuntu using unetbootin and try running live USB .. in **Try** mode not Install mode .. for a period to see if you experience reboots.  You will also see memtest as a grub option.

---

### Post by dragonfly41 on 2015-01-19
Correction to earlier suggestion (previous post) to use unetbootin to create live USB .. 
apparently unetbootin does not add memtest86+ to boot menu

[http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/16666/diagnose-hardware-problems-with-an-ubuntu-live-cd/)

> 
Note: If you used [UNetbootin]("http://www.howtogeek.com/howto/13379/create-a-bootable-ubuntu-9.10-usb-flash-drive/") to create an Ubuntu flash drive, then memtest86+ will not be available. We recommend using the [Universal USB Installer]("http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/") from Pendrivelinux instead (persistence is possible with Universal USB Installer, but not mandatory).


Also read some more tips here .. [http://www.dedoimedo.com/computers/linux-hardware-troubleshooting.html](http://www.dedoimedo.com/computers/linux-hardware-troubleshooting.html)

---

### Post by sudodus on 2015-01-19
... or use ***mkusb*** which copies/clones /flashes the iso file to a pendrive, so memtest will be there in the boot menu. It will look like you boot from a CD/DVD.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by lion3 on 2015-01-19
LOL I finally got it figured out.

I'm both embarassed and laughing my butt off at the same time.

Since I couldn't do the memtest (and in the past day or so we couldn't get the computer to boot for more than 3 minutes at a time) we figured memory was one of the last things left. So I spent 8 hours hiking across town to several different stores trying to find one that had memory compatible with our system.

Came home and stuck the brand new memory in and...fail once again.

Now a week or so ago, I'd said out of the blue, "honey what about the switch on the restart button."

"That's silly, can't be that," he said.

So after once again trying the new memory, switching out with the old graphics card and the old (less strong) power supply, we were noticing that by now the computer wasn't even responding to the reboot button.

What's the one thing in common with all the things we tried? Yeah, the elderly case.

Hubby stripped the restart wires and hotwired it like an old car and ... damn....booted right up and is working like a dream.

LOL and now I've got 8gb ram instead of only 4.

Sometimes it's the stupid simple stuff.

---

### Post by mc4man on 2015-01-19
Glad you got it, was just reading thru from start & noticed last post >solved.
The clue was in your very 1st. post, guess it fell by the wayside
( Ubuntu only *asks* if you want to shut down under very limited circumstances. Either from clicking on the shutdown or restart option in the session indicator or from a signal from  the power button.

---

### Post by sudodus on 2015-01-20
Congratulations and thanks for sharing the solution :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by dragonfly41 on 2015-01-20
> 
Now a week or so ago, I'd said out of the blue, "honey what about the switch on the restart button."

"That's silly, can't be that," he said.


But .. see post #10 ..

> 
By way of example here is a thread which cites a faulty reset switch causing glitches which cause reboots.

[http://www.tomshardware.co.uk/answers/id-1792345/computer-randomly-restarts-bios-replacing-ram-power-supply.html](http://www.tomshardware.co.uk/answers/id-1792345/computer-randomly-restarts-bios-replacing-ram-power-supply.html)




QED

---

### Post by lion3 on 2015-01-20
> **dragonfly41 said:**
> But .. see post #10 ..




QED

LOL Yup! You must have posted that while I was out hunting down memory. Didn't even see it when I went to post my "fixed it" post.

Thanks so much for your help!

---

### Post by Penguin360 on 2015-01-21
Glad you get your computer working again. Hope you get return your new memory card? Or use it in another computer?

---

