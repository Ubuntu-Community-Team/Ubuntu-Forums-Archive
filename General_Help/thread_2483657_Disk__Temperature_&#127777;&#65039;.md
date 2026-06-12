---
title: "Disk / Temperature &#127777;&#65039;"
date: 2023-02-05
forum: General Help
---

### Post by othmaqsa on 2023-02-05
Hello,
Yesterday I noticed something strange. When I click on Drives to check the disks installed, I find the NVME M.2 SSD + HDD. 
The SSD shows me a temperature of 98°  (208 Fahrenheit ) , it's impossible.
I installed other apps to monitor the temp to see if it's a bug or not, same info, 98°.
I reinstalled Win 11, the disk temperature is in reality 25°-29° 
Is this a bug on Linux? Or is Linux warming up the disks?
I have seen the same topic in another forum, and this bug has been reported in 2016.
Version: Ubuntu 22.04.1 LTS

---

### Post by MAFoElffen on 2023-02-06
You didn't post on how you determined that...

For me, what I do...
```

sudo apt install -y nvme-cli

```
Then find the devide name of your nvme drive
```

lsblk

``` 
Then check the temperature of that dirve
```

sudo nvme smart-log /dev/nvme0n1 | grep 'temperature'

```

---

### Post by othmaqsa on 2023-02-06
The information was mentioned in Ubuntu Disk Utility.

Apparently, this problem has been reported on 2016.

[https://askubuntu.com/questions/749537/patriot-blast-ssd-100c](https://askubuntu.com/questions/749537/patriot-blast-ssd-100c)
[https://www.pclinuxos.com/forum/index.php?topic=154272.0](https://www.pclinuxos.com/forum/index.php?topic=154272.0)
[https://ubuntuforums.org/showthread.php?t=2312021](https://ubuntuforums.org/showthread.php?t=2312021)

i have the same problem.

Maybe it s a bug/glitch in ubuntu, or the disk is not in SMART database of SMARTCTL , maybe ?

---

### Post by TheFu on 2023-02-06
I suspect your mean the Gnome Disk Utility.  If there's a bug, that's were it would be ... assuming the drive is reported the correct data and the sensors package has support for the motherboard and/or SSD being used.  It is hard for any software to know about new hardware, as you can understand.  Manufacturers don't always provide the needed information.

For example, the Ryzen AM4 motherboards I have don't have sensors support in the kernel that I run on one of them, but on the other it is working. Eventually, I'll have the version that supports it and be able to access temperature data on that 2nd AM4 motherboard.   Ah ... someday.
```

nvme-pci-0900
Adapter: PCI adapter
Composite:    +43.9°C  (low  = -273.1°C, high = +84.8°C)
                       (crit = +84.8°C)
Sensor 1:     +43.9°C  (low  = -273.1°C, high = +65261.8°C)
Sensor 2:     +59.9°C  (low  = -273.1°C, high = +65261.8°C)

```
Gotta love such useful information, though I don't have any clue where sensor1 and sensor2 are.
SMART says:
```

temperature                         : 42 C
Temperature Sensor 1                : 42 C
Temperature Sensor 2                : 66 C
```

Would be nice if the outputs agreed, right?

---

### Post by othmaqsa on 2023-02-06
Yes, that's right, indeed, I meant Gnome Disk Utility.


It's in Gnome Disk Utility where the KINGSTON A2000 NVME M.2 480G shows me the incredible temp 98 degree / 208 F.


Should I just ignore it?


Because I immediately installed WIN 11 to be sure, and on HWINFO, the same disk shows me between 24 and 27 degrees.

---

### Post by lucant on 2023-02-06
In another distribution, I asked about my wifi card that reached a very high temperature... The answer was that they didn't know why, that I would have to open my machine and measure the temperature with a thermometer... The answer seemed to me unsatisfactory, but I concluded that if the temperature was that high, I would feel it.

---

### Post by TheFu on 2023-02-06
> **othmaqsa said:**
> Yes, that's right, indeed, I meant Gnome Disk Utility.


It's in Gnome Disk Utility where the KINGSTON A2000 NVME M.2 480G shows me the incredible temp 98 degree / 208 F.


Heat dissipates fast in these components.  From second to second, it can change.
Do you have the current firmware for that SSD loaded?  I saw that Kingston released updates, so check that.  If you want to cheat with a Linux guy who is sponsored by Kingston to get different access into their support channel, you can look up the Bald Nerd and see if he can't help.  It could just be a bad sensor too that rather than fix in hardware, they updated the MSFT drivers, but not any others.  Hard to say.  If it is new and this matters to you (I think it should), then I'd start the RMA process.  Sometimes even good vendors have a few bad parts.

---

### Post by mIk3_08 on 2023-02-06
> **othmaqsa said:**
> 
It's in Gnome Disk Utility where the KINGSTON A2000 NVME M.2 480G shows me the incredible temp 98 degree / 208 F.
Should I just ignore it?
This is not normal you can't just ignore this one. 98 degree is not a joke. mine is only 48 degree. Can you run the command below in your terminal and post the result here in thread wrap with code. To run the terminal in your desktop just press ctrl and alt + t or just find it in your Ubuntu System installed applications. Regards and cheers.
```
hostnamectl
```

---

### Post by ActionParsnip on 2023-02-07
Don't M.2s have like a firmware you can update or something? Maybe that'll help

---

### Post by othmaqsa on 2023-02-07
In WIN 11, at this moment, the temp of this SSD Drive is 24 degree.

Why in Ubuntu the temp of this drive show 98 degree ?

A lot of guys have the same problem, this problem has been reported to Ubuntu since 2016.

Maybe it's a problem regarding the SMARTCTL DATABASE ?

[https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/1581594](https://bugs.launchpad.net/ubuntu/+source/libatasmart/+bug/1581594)
[https://forums.linuxmint.com/viewtopic.php?t=318201](https://forums.linuxmint.com/viewtopic.php?t=318201)
[https://forums.linuxmint.com/viewtopic.php?t=328651](https://forums.linuxmint.com/viewtopic.php?t=328651)
[https://ubuntuforums.org/showthread.php?t=2312021](https://ubuntuforums.org/showthread.php?t=2312021)

I repeat again, in WIN 11 at this moment, the temperature of this SSD is no more than 27 degree.

---

### Post by othmaqsa on 2023-02-07
There is no firmware to this SSD for Linux. Only Windows.

---

### Post by othmaqsa on 2023-02-07
I want to resolve this problem. I want to keep Ubuntu. No the disk in not a new disk. I have it since more than 1 year. The disk work great in WIN 11 and Ubuntu. The only problem I have, is when I check the temp of this SSD in WIN (24 to 27 degree) and the same disk in Ubuntu show 98 degree.

---

### Post by othmaqsa on 2023-02-07
Another information: 
Assumed that the PC is off all night.
I turn it on the next day.
The disk displays 98 degrees on startup.


So there's something wrong

---

### Post by othmaqsa on 2023-02-07
WIN 11 VS Ubuntu (TRY UBUNTU with USB KEY)

[https://zupimages.net/viewer.php?id=23/06/qey9.png](https://zupimages.net/viewer.php?id=23/06/qey9.png)
[IMG]https://zupimages.net/viewer.php?id=23/06/ghx6.jpg[/IMG][https://zupimages.net/viewer.php?id=23/06/ghx6.jpg](https://zupimages.net/viewer.php?id=23/06/ghx6.jpg)
[IMG]https://zupimages.net/viewer.php?id=23/06/qey9.png[/IMG][IMG]https://zupimages.net/viewer.php?id=23/06/ghx6.jpg[/IMG]

---

### Post by TheFu on 2023-02-07
> **othmaqsa said:**
> In WIN 11, at this moment, the temp of this SSD Drive is 24 degree.

Why in Ubuntu the temp of this drive show 98 degree ?

Any chance that your locale settings are mixing °F and °C?

> **othmaqsa said:**
>  There is no firmware to this SSD for Linux. Only Windows. 
You are confused.  Firmware gets installed into hardware.  If the vendor only makes the installation tool for Windows and you use that to update the firmware, then Linux benefits too.  If they only support Windows for "flashing" new firmware, I'd find a better vendor.

---

### Post by othmaqsa on 2023-02-07
Have you see this 2 screenshots ?

[https://www.zupimages.net/up/23/06/ghx6.jpg]("https://zupimages.net/viewer.php?id=23/06/qey9.png")
[https://www.zupimages.net/up/23/06/qey9.png](https://www.zupimages.net/up/23/06/qey9.png)

---

### Post by othmaqsa on 2023-02-07
[COLOR=#000000]Any chance that your locale settings are mixing °F and °C? ?

[/COLOR]No, in Ubuntu, the temp show: 98 degree / 208 F

In WIN, the temp show in this moment: 22 degree

[COLOR=#000000]
[/COLOR]

---

### Post by othmaqsa on 2023-02-07
Check here: [https://pasteboard.co/Wlu3kZNFX03h.png](https://pasteboard.co/Wlu3kZNFX03h.png)

---

### Post by TheFu on 2023-02-07
> **othmaqsa said:**
> Have you see this 2 screenshots ?

[https://zupimages.net/viewer.php?id=23/06/qey9.png](https://zupimages.net/viewer.php?id=23/06/qey9.png)
[IMG]https://zupimages.net/viewer.php?id=23/06/ghx6.jpg[/IMG][https://zupimages.net/viewer.php?id=23/06/ghx6.jpg](https://zupimages.net/viewer.php?id=23/06/ghx6.jpg)

The URL is empty when I use dillo.  These forums support image uploads, though text is always preferred.  Linux isn't Windows.

---

### Post by othmaqsa on 2023-02-07
[IMG]https://zupimages.net/viewer.php?id=23/06/ghx6.jpg[/IMG]I try to add all images directly here, but there is no way.[IMG]https://zupimages.net/viewer.php?id=23/06/qey9.png[/IMG]

---

### Post by coffeecat on 2023-02-07
> **othmaqsa said:**
> [IMG]https://zupimages.net/viewer.php?id=23/06/ghx6.jpg[/IMG]I try to add all images directly here, but there is no way.[IMG]https://zupimages.net/viewer.php?id=23/06/qey9.png[/IMG]

Yes, there is. Below the Quick Reply message editor there is a button that says, "Go Advanced". Click on that to open the advanced editor and then click on the paper-clip icon in the toolbar to open the Attachment Manager.

---

### Post by othmaqsa on 2023-02-07
Check the difference between the SSD Celsius in WIN and UBUNTU.

As you can see, a lot of difference.

When I boot with WIN, I have 22 degree Celcius.

When I boot with pendrive with UBUNTU and access to GNOME DISKS, I can see 98 degree Celcius.

---

### Post by TheFu on 2023-02-07
I avoid GUI programs for many reasons.  I know that it is often just another layer between what I want and what 20% of the functionality some GUI designer thought I needed.  That's just 1 reason to use CLI commands ... fewer complexities between the information we want for a programmer to screw up.

Gnome is responsible for their "Disks" application. Have you opened a bug with them?  It isn't like Canonical can do anything about it.

---

### Post by lucant on 2023-02-07
When I switched from Endless OS to Ubuntu 22.04.1 on my new laptop, there were a lot of ACPI errors on startup... I'm no linux expert, researching this I saw that my Bios was on the latest version, and how everything worked, probably the kernel looked for components on the motherboard that didn't exist. I simply said that I only wanted to know about critical errors (loglevel=3)... The problems were 'camouflaged' because there was nothing I could do. Maybe in a later kernel...
I believe your case is +/- around...

---

### Post by Paulgirardin on 2023-02-20
This is a bug.
I can't recall all the details ,but bear with me.
There is a S.M.A.R.T. attribute for SSDs that reports aging for the drive. On a new drive it starts at 100 and counts down with age.
It is being misreported as a temperature by some applications.
I noticed this when I installed a new KINGSTON SA400M8120G  M.2 drive. The Gnome Extension I used showed 100 °C 
I corresponded  with the Extension's Dev and it became evident it was a problem with S.M.A.R.T.
My Kingston has steadily "cooled down" and is now showing 88 °C - and still going strong!
(of course the first thing I did was check the M.2 with a IR emissivity thermometer - it was ~38 °C which was ambient for the inside of the PC case that day)

edit:

I think it is a confusion between the two Attributes below:

231  Temperature   
Temperature, monitored by a sensor somewhere inside the drive. Raw value  typicaly holds the actual temperature (hexadecimal) in its rightmost  two digits.

And:
232  Available Reserved Space
The attribute is used in SSDs to denote the remaining reserved space. The value counts down, typically from 100 to 0. The Raw value is vendor-specific.

---

### Post by chamilie on 2023-12-30
[COLOR=#000000]Thank you very much @Paulgirardin for the informations. My problem started after an Ubuntu update a month ago.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293258&stc=1[/IMG]
The Gigabyte SSD is always at 100°C, as soon as I turn on my computer. 
The computer fan is very noisy all the time. When using my laptop without the charger, the battery runs out very quickly. There is no process consuming more than 10% of the CPU.
I don't have a clue on how to solve it. Can someone help me please?
[/COLOR]

---

### Post by MAFoElffen on 2023-12-30
I see there has been 4 firmware revisions for that drive. 
RE: [https://smarthdd.com/database/GIGABYTE-GP-GSTFS31256GTND/](https://smarthdd.com/database/GIGABYTE-GP-GSTFS31256GTND/)
Have you tried to update the firmware first to see if that will correct that?

---

