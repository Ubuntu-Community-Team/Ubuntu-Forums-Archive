---
title: "acer aspire es1 411 issues"
date: 2015-11-07
forum: General Help
---

### Post by maclenin on 2015-11-07
I've installed xubuntu 14.04 on an acer aspire es1 411.

BIOS set to legacy before usb install.

ALL seems to be working beautifully, except:

1. shutdown -r and -h / +0 or now (and other flags) work intermittently. "Restart" and "Shut Down" icons via "Log out" dialog are similarly irregular. When they don't work, laptop freezes at the splash stage: laptop falls silent but screen freezes / stays on. Have to "hard shutdown" via power button to shutdown / reboot.

2. suspend - laptop screen remains dark when trying to wake from suspend. Touchpad has no effect. Have to "hard shutdown" to re-activate the machine.

3. usb - there are also usb-related error messages appearing at start-up, which I will turn to after resolving 1 and 2!

Again - all else (thus far) works perfectly.

Thanks for any guidance!

UPDATE: [http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa](http://askubuntu.com/questions/524894/boot-and-shutdown-issues-on-aspire-e-11-model-e3-111-c0wa) <--- minimally reduces rate of failure - still experiencing shutdown issues.

---

### Post by sudodus on 2015-11-07
Sometimes it helps to use a [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808), for example **acpi=off** or **noapic**. You can try several boot options.

---

### Post by maclenin on 2015-11-07
**!eltitbus | eman 8rg**

Thanks - will give those few an og and report back....

---

### Post by maclenin on 2015-11-11
...bios and boot options and blacklists - oh my! Not a one is providing resolution to this legacy bios conundrum....

Shutdown -halt...
```
sudo shutdown -h now
```
...and shutdown -reboot...
```
sudo shutdown -r now
```
...work sporadically.

One piece I have NOT been able to try is [this]("http://ubuntuforums.org/showthread.php?t=2277311&p=13348428#post13348428") - as I have not found a way to disable xHCI (there are no references to it in my bios)....

The other "options" seems to beg a UEFI re-install - which I'd rather not have to do - as all else with my current set-up seems to be working well.... 

Thanks for any additional "legacy" clues....

---

### Post by sudodus on 2015-11-11
For me hard shutdown is *ctrl + alt + delete* (when it works) or *pressing the power button for four seconds*, which can easily damage the file system.

```
sudo shutdown -h now
``` is soft and OK

Another soft shutdown is

***[alt] SysRq R E I S U O***

and soft reboot

***[alt] SysRq R E I S U B***

See this link.

[wiki/Magic_SysRq_key](https://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by maclenin on 2015-11-11
I hear that - thanks - I've updated the shutdown terms (which I misrepresented in my flustered state)....

Yes - hard, for me, is anything other than using 'shutdown'....

The problem is I have a similar acer (aspire e1 "570") with an identical (legacy) xubuntu install, which I am able to shutdown any which way (softly) - without issue:
```
sudo shutdown -h +0
sudo shutdown -r +0
```
I should be able to do exactly the same on my "411"....

EDIT: Indeed, the magic sysrq commands work as advertised (I used **[altgr]** in place of **[alt]**). You can't script it - create a "REISUB" launcher, for example - because it would kill itself before it reached 'b' or 'o'?

---

### Post by sudodus on 2015-11-11
No, I don't think you can script SysRq REISUO. Learn it by heart or write it down on a paper :-)

There might be some other method to fix your shutdown problem.

Sometimes it helps to flush the buffers before trying to shutdown:

```
sync
```

Another possibility is to change some setting in the BIOS menu: 'trial and error' - make a note (on a paper) which setting you change, so that you can come back to a working setting afterwards.

---

### Post by maclenin on 2015-11-11
If the laptop can be shutdown - softly - using REISU* - shouldn't this provide some sort of clue (assuming we know how shutdown works / goes about its business) as to why shutdown -r and shutdown -h are NOT working? What process could be preventing shutdown from completing its job? Is there a way we can isolate the point at which (or during which process) shutdown fails? Can we run / debug shutdown in the terminal?

...though I was looking forward to making pretty red and orange buttons for REISUO and REISUB, respectively.

**echo b > /proc/sysrq-trigger** is the 'reboot' command, so I would expect **echo o > /proc/sysrq-trigger** to be the 'off'? Trouble is 'e' and 'i' are killers....

Thanks, again, for the guidance!

---

### Post by maclenin on 2015-11-13
For the time being, I will continue playing with [magic]("https://en.wikipedia.org/wiki/Magic_SysRq_key")...

...for re**b**oot:
```
[altgr] [sysrq] r e i s u **b**
```
...for power **o**ff:
```
[altgr] [sysrq] r e i s u **[B]o**[/B]
```
...until a "better" shutdown solution presents itself.

!niaga sknahT

---

### Post by sudodus on 2015-11-13
emoclew era uoY

---

### Post by maclenin on 2015-11-19
...a quick 'down'date:
```
[altgr] [sysrq] r e i s u **o**
```
...does not work - screen and drive freeze at the depress of '**o**'....

Is there a way to "neuter" the BIOS - e.g. flash the proprietary firmware and replace it with generic ('ubuntu') firmware - so we don't have to deal with any "SecureBoot" / UEFI entanglements - etc...just let me use the hardware in the way XUBUNTU intended?

Switiching the BIOS to "Legacy" (pre-install) - as indicated in the OP - has proved a NON-solution....

I can reboot - using reisub - I just can't power off - by any means (other than "hardly")....

!drawnO

---

