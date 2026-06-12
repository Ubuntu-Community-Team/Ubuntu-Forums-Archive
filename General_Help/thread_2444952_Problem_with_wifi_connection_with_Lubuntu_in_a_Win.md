---
title: "Problem with wifi connection with Lubuntu in a Windows 10 computer"
date: 2020-06-06
forum: General Help
---

### Post by jamesmck on 2020-06-06
[COLOR=#242729][FONT=Arial]All wifi options are grayed out when I use either full install of Lubuntu on a USB SSD or a simpler persistent install on a USB stick when these have been created on a Windows 7 computer and then booted into a Windows 10 computer. The same inability to get wifi happens with a Lubuntu Live dvd booted into the Windows 10 machine. I do not have a second Win 10 machine to test to see if it is the OS or this specific computer. Suggestions appreciated. The Win 10 is a refurbished Lenova Thinkpad x131e, originally Win 7, but redone with Win 10 by the refurbisher.[/FONT][/COLOR]

---

### Post by CelticWarrior on 2020-06-07
What other OS or OSes is/are installed is irrelevant. That it had one Windows version and has since been upgraded to another is also irrelevant.

You have a problem with the WiFi device not being detected or not having the required drivers installed, something that likely would happen the exact same way if Lubuntu was the only OS there. Please read: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by jamesmck on 2020-06-07
I am a little confused here.  Where is the location of the problem likely to be?  Not in the network driver residing in the Windows OS (which is, nevertheless, up to date). Where then?  Maybe in the full installation of my SSD, but surely not in the Lubuntu Live Disc.  Might any BIOS setting be involved?

---

### Post by CelticWarrior on 2020-06-07
A little is an understatement, I'm afraid. I'm also afraid you'll make a mistake somewhere and end up not booting either OS.

What I tried to explain in the previous post is very basic stuff: Whether a specific hardware, namely the WiFi, doesn't work in Lubuntu it has nothing to do with Windows* in dual boot, let alone with the Windows version it might have been upgraded from.

* The exceptions are very rare, so rare we seldom consider it, when Windows has been incorrectly shut and/or is suspended or hibernated. Any Windows 8 or newer actually has some sort of hibernation by default called Fast startup. It's important to [know it and know why you don't want it]("https://www.windowscentral.com/how-disable-windows-10-fast-startup"), especially when dual booting.

For troubleshooting WiFi please always post in the ["Networking & Wireless"]("https://ubuntuforums.org/forumdisplay.php?f=336") section and,  again, please read and do what it says in ["Before posting in the Neworking & Wireless"]("https://ubuntuforums.org/showthread.php?t=370108") sticky thread. Basically use and alternative network connection (Ethernet, USB tethering from your phone, etc.), follow the link to download and run this script, post results in your thread. AGAIN, rthat it works in Windows just tells us the hardware is working, everything else is irrelevant.

---

### Post by jamesmck on 2020-06-07
I am thinking that a USB WiFi dongle might be a way around this. I will try that.  Thanks for all the suggestions.  BTW, this is not dual-boot, just boot directly to a full install on an external USB solid state drive.  And, the same lack of recognition happens when booting to a &#8220;live&#8221; DVD.  One further note, I have a Broadcom network adapter on the offending computer, and I see from the web that it has many issues with Ubuntu.

---

### Post by guiverc on 2020-06-08
[https://askubuntu.com/questions/1247701/unable-to-connect-wifi-with-lubuntu-live-disc]("https://askubuntu.com/questions/1247701/unable-to-connect-wifi-with-lubuntu-live-disc?")

---

### Post by ActionParsnip on 2020-06-09
What is the output of:
```

sudo lshw -C network; lsb_release -a; uname -a; sudo rfkill list

```
Thanks

---

