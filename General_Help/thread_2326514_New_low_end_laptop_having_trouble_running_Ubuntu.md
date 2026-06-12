---
title: "New low end laptop having trouble running Ubuntu"
date: 2016-06-01
forum: General Help
---

### Post by The musmula on 2016-06-01
So I just bought an Acer Es15 (aka ES1-531) and I knew that a dual core 1.6GHz CPU will suck but this doesn't seem like normal sucking. It has an Intel Celeron N3505 CPU, 4GB RAM and a hard drive, no ssd. Is it normal to lag on YouTube video playback? I'm a web developer and I just scored an internship in Germany so that's pretty much the only reason I bought this, I can't currently afford anything else but this thing lags when playing back CSS animations that worked just fine when I coded them on my 4 year old desktop PC which has a similar CPU (could be a bit faster, I doubt it though because I payed the exact same amount of money for that desktop PC in 2012 and I can't believe I could get a pile of crap in 2016 for that cash).

I guess what I'm asking is: is this "normal"? What do you think I should do? Try a different distro maybe?

While I was writing this I also noticed that some fan was constantly turning on and off... maybe it was the hard drive, like I said: I just bought the thing so I can't really tell the sounds of the parts apart.

also, I installed the system in UEFI mode and I couldn't run it in uefi mode so I had to switch back to legacy... could that affect performance?

---

### Post by oldfred on 2016-06-01
UEFI or BIOS should not matter.

I prefer gpt partitioning and configuring for both UEFI and BIOS with both the ESP - efi system partition and a bios_grub partition. Then you can change how you boot if desired without reinstalling.

All Acer require you to set trust on the .efi files from UEFI.
       Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

The Intel graphics may not have enough horsepower for Unity and YouTube? If so then Lubuntu or Xubuntu may be better.

But I have an i5 and with YouTube have has some slowness when trying to scroll down when it is playing. And that is with newest Firefox.
Perhaps something in the flash vs. HTML5 changes.

Have you tried Chromium?

---

### Post by Chelidze on 2016-06-01
I have a similar laptop and here is my expiriance with it.
First of all I should agree with you how are they allowed to sell such underpowered hardware is beyond my understanding. If you install windows 10 on it only spying process will take 100% of CPU power (of course when they are running). About your desktop CPU generally they ar much faster I would say a 7 yo desktop CPU will smoke that laptops CPU.

Now about Ubuntu, unity isn't a light weight desktop environment at all, it's opposite to that. Plus most probably your Firefox isn't using hardware acceleration (yes Linux port is not the best, the devs say that and they blame x11)
So your underpowered CPU is forced to decode video. So you get leg and slow system.
 I would recommend you installing xubuntu and using chrome, 4 GB of RAM will be sufficient for chrome.

---

### Post by The musmula on 2016-06-02
Thanks guys for your replies. I'll try Xubuntu right away

Actually, this is amazing. I'm still downloading the Xubuntu iso but meanwhile I installed Chrome and everything is fine now... CSS animations work okay, YouTube video playback doesn't lag... amazing
Thanks everyone

---

### Post by mastablasta on 2016-06-02
it means Firefox or Flash that is present isnt' handling the graphics acceleration propperly.

---

