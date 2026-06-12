---
title: "Warnings/Errors on boot-up/shut down"
date: 2015-12-01
forum: General Help
---

### Post by Drowz0r on 2015-12-01
Hello all

I've been having these errors after some updates a while ago. While some errors I was able to eventually resolve these ones seem to remain:

On shut-down these messages occasionally appear:

[https://i.imgur.com/RskvKNZ.jpg](https://i.imgur.com/RskvKNZ.jpg)
[http://i.imgur.com/aFeIdDM.jpg](http://i.imgur.com/aFeIdDM.jpg)
[http://i.imgur.com/yHYYXaV.jpg](http://i.imgur.com/yHYYXaV.jpg)
[http://i.imgur.com/h2ywc5Z.jpg](http://i.imgur.com/h2ywc5Z.jpg)

Here is how my screen sometimes appears on start-up:

[http://i.imgur.com/SK2P8Gt.jpg](http://i.imgur.com/SK2P8Gt.jpg)
[http://i.imgur.com/1IA6Og9.jpg](http://i.imgur.com/1IA6Og9.jpg)

When these errors appear on shut down, the machine never actually switches off, I have to either hold the power button in or do a hard reboot. It is not consistent. Sometimes it happens, sometimes it does not. When these errors appear on start-up, generally nautilus isn't displaying properly. Fonts won't be correct or the theme is missing completely.

---

### Post by y6FgBn)~v on 2015-12-01
Without knowing more regarding the software you have installed I found this link which pertained to your shutdown error messages;

[https://askubuntu.com/questions/617785/how-to-connect-to-l2tp-over-ipsec-vpn](https://askubuntu.com/questions/617785/how-to-connect-to-l2tp-over-ipsec-vpn)

The error messages on startup may be related to this link;

[https://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed](https://askubuntu.com/questions/584248/boot-error-acpi-pcc-probe-failed)

Hopefully these will be helpful.

---

### Post by Drowz0r on 2015-12-01
The first link seems to be regarding a VPN connection? I'm not using any kind of VPN stuff. Is that the software question you had?


Regarding the second link, I actually did update the grub recently for an unrelated reason but it didn't seem to solve the problem. There aren't any multi-monitor settings on my motherboard though.

---

### Post by grahammechanical on 2015-12-01
Linux by nature prints system messages to the screen. Usually these messages are covered by a splash screen both during the loading of Ubuntu and the shut down of Ubuntu.

Keeping the explanation simple enough for me to understand, I see things this way: Linux starts to load and opens a console to print its system messages to. This console is tty1 which we can access with Ctrl+Alt+F1 and at some point Ubuntu needs to login to Linux and then Ubuntu starts to load and by the time the loading gets to the Ubuntu login screen Ubuntu is running on tty7.

If we switch to tty1 we can log in to a Linux console. After logging out we can switch back to Ubuntu on tty7 by Ctrl+Alt+F7.

When Ubuntu shuts down we still have Linux on tty1 to shut down and we may see some messages leftover from the loading process plus messages specific to the Linux shut down process.

The ACPI probe failed message is a common message that appeared during the development period of Ubuntu 15.04 and it seems to be present also in 14.04.3. We do not see that message in 15.10.

What you are seeing are normal system messages. I have noticed that using the open source video driver I get a Ubuntu splash screen but using a Nvidia driver I do not see a splash screen. The messages are not the cause of the failure to shut down. Something is putting a delay in shutting down. The system is most likely waiting for a response from some system service and it is not getting it. It will wait a certain period and then carry on regardless.

Regards

---

### Post by Drowz0r on 2015-12-01
> **grahammechanical said:**
>  It will wait a certain period and then carry on regardless.

I do find that it just hangs on this system message and does not continue to shutdown. I have to press the power button as the only means to shut down my PC when this happens. I have woken up the following morning a few times to find I've hit shut down and the PC has instead hung on this screen.

I did also restore the start-up screen, seemingly called plymouth, but these errors returned. :(

---

