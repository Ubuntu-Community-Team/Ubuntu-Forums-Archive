---
title: "Laptop screen at lowest brightness on boot"
date: 2013-08-25
forum: General Help
---

### Post by atomicspin on 2013-08-25
I'm running a Toshiba Satellite with a new install of 13.04.  Every time I boot up, the screen brightness reverts back to the lowest setting.  Is there anyway to fix it so it saves the setting that I leave it on?  

I can certainly adjust the brightness, it just goes back to the lowest setting on reboot.  Backlight is on.  

I've tried [COLOR=#000000]setpci -s 00:02.0 F4.B=00[/COLOR] in rc.local to no avail.[COLOR=#000000]

[/COLOR]

---

### Post by carl4926 on 2013-08-25
Power off completely and pull the power and battery.
Re-connect and try again

---

### Post by atomicspin on 2013-08-25
> **carl4926 said:**
> Power off completely and pull the power and battery.
Re-connect and try again

Just tried it and still the same problem.  

Screen is bright until Ubuntu splash screen, then it goes dim.

---

### Post by carl4926 on 2013-08-25
I've had this happen once or twice when a machine goes to powersaving brightness and I reboot and it comes up all dull.
Powering off usually clears it up

What happens when you boot a live CD/USB

---

### Post by bra|10n on 2013-08-25
[https://launchpad.net/ubuntu/+source/toshset](https://launchpad.net/ubuntu/+source/toshset)

[http://ubuntuforums.org/showthread.php?t=1306321](http://ubuntuforums.org/showthread.php?t=1306321)

---

### Post by atomicspin on 2013-08-25
> **bra|10n said:**
> [https://launchpad.net/ubuntu/+source/toshset](https://launchpad.net/ubuntu/+source/toshset)

[http://ubuntuforums.org/showthread.php?t=1306321](http://ubuntuforums.org/showthread.php?t=1306321)

Thanks for the links! 

When I install and run toshset (as root), I get "required kernel toshiba support not enabled."   

I'm on 13.04.

---

### Post by bra|10n on 2013-08-25
[http://linuxforcynics.com/hardware/toshset-required-kernel-toshiba-support-not-enabled](http://linuxforcynics.com/hardware/toshset-required-kernel-toshiba-support-not-enabled)

---

### Post by varunendra on 2013-08-26
> **atomicspin said:**
> I can certainly adjust the brightness, it just goes back to the lowest setting on reboot.  Backlight is on.  

I've tried [COLOR=#000000]setpci -s 00:02.0 F4.B=00[/COLOR] in rc.local to no avail.[COLOR=#000000]

[/COLOR]
Where did you get the "setpci -s" tip, and how did you implement it?

Usually the problem is opposite to what you are experiencing, that is, brightness defaulting to max despite setting it to low or lowest. But the usual workaround (not a fix) should be applicable to your problem too. First, see if the 'fix' (adding "acpi_osi=" to Grub commandline) suggested by Toz in post #2 here can help : [http://ubuntuforums.org/showthread.php?t=2169872&p=12767094#post12767094](http://ubuntuforums.org/showthread.php?t=2169872&p=12767094#post12767094)

If not, a crude workaround is to 'echo' your desired brightness value into your default video device using /etc/rc.local file.

For example, my default video device is "acpi_video0", and it accepts brightness value from 0 to 10. I have added the following line to my /etc/rc.local file -
```
echo 0 > /sys/class/backlight/acpi_video0/brightness
```
..to set it to lowest during startup (it used to default to max).

To find out your available video device(s) and the current brightness value(s) in them -
```
[s]for i in /sys/class/[COLOR="#FF0000"]brightness[/COLOR]/*; do echo $i; cat $i/brightness; done[/s]
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; done
```
Then change the brightness using the "Brightness & Lock" application and run the above code again. Note the device whose value changed, this is your default video device.

Now change the brightness value to what you prefer and run the code again. Note down this preferred  value this time.

If, for example, this value is "6" and the video device is "acpi_video 0", insert the following line in your /etc/rc.local file (above "exit 0" line)-
```
echo 6 > /sys/class/backlight/acpi_video0/brightness
```
Reboot and see if it works. If not, then probably [Toz]("http://ubuntuforums.org/member.php?u=27546") is the expert you are looking for.

---

### Post by yagolf on 2013-12-26
Hey Varunendra, your workaround works for me on ubuntu gnome 13.04 64bit. Nice one! (though I still would like to know the reason for this weird resetting...)
All the best!

---

### Post by varunendra on 2013-12-26
Glad it could help someone :).

I'm not sure about the reason as well, but most probably it is due to unsupported or 'not-properley supported' graphics card, or more likely, non-standard acpi implementation in the BIOS/firmware of the laptop.

Sometimes some additional boot parameters like "acpi_osi=" or "acpi_osi=vendor" etc. in kernel boot line (can be added via /etc/default/grub file) help in handling these devices properly, but there are quite a few variants of such parameters and which one would work sometimes requires quite a number of experiments. If you are interested, please follow the posts by Toz and hopefully you'll get some ways to determine which one you want.

---

### Post by yagolf on 2014-01-23
thanks Varun. Not sure I'll do but I appreciate your help :D

---

