---
title: "Ubuntu 12.04 Live USB Crashing"
date: 2013-12-24
forum: General Help
---

### Post by stangdaman on 2013-12-24
My parents were asking me about new operating systems and I suggested that they try Ubuntu. I loaded it as a live usb but every time they start it up they run for a few seconds and then it hangs up and you have to do a hard reboot. It's not exactly making the intro to Ubuntu too appealing. The last time I tried it I got a message asking me to downgrade the graphics mode but when I said ok to that it locked up again. Any ideas would be helpful. I have tried a few different versions (13.10 wouldn't boot, 12.04 64bit booted but locked up, 12.04 32bit gave the error message before locking up).

Their system specs are as follows:
Dell XPS 210
Core2Duo 1.8ghz
4gb RAM (not sure what speed)
AMD Radeon X1300 Pro (I believe this is what it has for a video card)

---

### Post by stangdaman on 2013-12-24
So, I tried installing as a dual boot but it looks like it's having the same issue. So it's not the live disc that's the problem. I'm thinking maybe video card problems but I'm not sure.

---

### Post by stangdaman on 2013-12-25
Does anyone know if there are any logs or anything that I can take a look at to see what might be causing it to crash. I don't know if maybe it's just a driver issue or something.

---

### Post by grahammechanical on 2013-12-25
What I usually do in this situation is

1) at the first purple screen press Enter
2) at the language screen select a language (default is English) and press Enter
3) at the next screen with Try Ubuntu - Install Ubuntu, press F6
4) look for a small drop down menu at the bottom right of the screen an select nomodeset and press Enter.
5) press Esc to get back to the Try - Install screen
6) Select Try Ubuntu and press Enter.

We may need to use a combination of those F6 options to get the live session, and from that an installation, working on certain machines.

Please explain to your parents that the Ubuntu Live/Installation disk has to be a one size fits all kind of thing but there is such a great variety of hardware that it is impossible to be anywhere near perfect. But the developers do try.

This kind of issue can be caused by the machine needing a proprietary video driver and as it is proprietary it cannot be included on the Installation disk for ethical reasons. During the installation process the user has the opportunity to make his own choice about using non-open source or proprietary software. We can tick to install third party software and that will install a proprietary video driver for us. We can also install proprietary video drivers after installation.

In this way, Ubuntu seeks to satisfy those who have ethical reasons for not using proprietary code and those who have no objection to installing proprietary software. Oh, by the way, having another operating system on the machine, especially Windows 8, can bring with it its own issues.

Regards.

---

### Post by stangdaman on 2013-12-25
At this point I have it installed. I'm just trying to figure out what is wrong with the install that is causing it to keep crashing. Is there a particular log I should be paying attention too? Is there any information that I could post that would be helpful?

---

### Post by stangdaman on 2013-12-25
I'm testing now but I believe I fixed the problem. It turns out this machine does not have the amd card like the dell page said but has an old intel integrated graphics card (intel 82g965). I found that there were some issues that people had been seeing with this previously and the fix I am linking to below fixed it. It appears to have worked on this machine too. If it crashes again I will update to indicate as much but if anyone else has this issue this fix seems to work.

[http://askubuntu.com/questions/37663/screen-windows-and-menus-are-flickering-horribly/37679#37679](http://askubuntu.com/questions/37663/screen-windows-and-menus-are-flickering-horribly/37679#37679)

---

