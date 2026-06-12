---
title: "No keyboard detected at booting PC"
date: 2024-08-24
forum: General Help
---

### Post by satimis on 2024-08-24
Hi all,

MS wireless keyboard 2000
Ubuntu 24.04

Occasionally booting the desktop PC, Warming "no keyboard detected" popup.  The PC continues to boot.  I can't login.  I have to re-plug the USB receiver several times then the keyboard works and I can type in password.

Another time while working, the PC freezes.  I have to hard reboot the PC.   Would it be the problem of the keyboard?  I have to purchase a new keyboard?

Please advise.  Thanks

Regards

---

### Post by currentshaft on 2024-08-24
-b

---

### Post by satimis on 2024-08-24
> **currentshaft said:**
> sudo dmesg
journalctl -b

Run those commands and look for errors pertaining to the keyboard or USB bus.
Hi,

Thanks for your advice.

Run following commands on Terminal:
$ sudo dmesg > dmesg_printout.txt
$ journalctl -b > journalctl_printout.txt

no error message popup.  But I'm not allowed to upload them here because exceeding the limit of file size allowed.

Regard

---

### Post by satimis on 2024-08-24
Hi@currentshaft,

Again.  Performed following test on Terminal:

```

$ sudo dmesg | grep keyboard > dmesg_keyboard.txt
$ sudo dmesg | grep "USB bus" > dmesg_usb_bus.txt

$ journalctl -b | grep keyboard > journalctl_keyboard.txt
$ journalctl -b | grep "USB bus" > journal_usb_bus.txt

```

The printout files are attached here.

Regards

---

### Post by currentshaft on 2024-08-24
m

---

### Post by satimis on 2024-08-25
> **currentshaft said:**
> The log output will be very long, you'll have to manually examine it for errors and indications of what's wrong.

Leave these two commands running in terminal windows and monitor them when the problem happens:

sudo dmesg -wHT
journactl -f
Hi,

It would be difficult for me to check those 2 output files unless having some key points to check.

Leaving those 2 commands on Terminal:
If the PC freezes, on hard-reboot the outpout will be lost.

In recent 2 days "keyboard not found" not happens.  I'll keep watching further.  Thanks

Regards

---

### Post by currentshaft on 2024-08-25
4

---

### Post by satimis on 2024-08-25
> **currentshaft said:**
>  - snip =

Use "journalctl -b 1" to view logs from the previous boot.
Thanks.  I'll check it if problem reoccures.

Regards

---

### Post by satimis on 2024-08-29
Hi@currentshaft,

Finally it happens after several days of silence.

Starting PC
Warning " no keyboard detected"
After booting up the PC,  I re-plug the bus of MS keyboard to another USB port.   MS keyboard is still unable to work.
Then I plugin the bus of logi keyboard.  The keyboard is detected and work without problem, including its mouse.

I restart the PC with MS keyboard bus plugin on an USB port of the PC.  The warning " keyboard not detect" still popup.  Then I plugin the bus on the USB port of the Dell 4K display.  Now MS keyboard works .

It is very strange to me.

Then on Terminal I run;
journalctl -b 1 > keyboard_problem.txt

Unforunately the file size exceeds the limit.  I can't upload it here

---

### Post by sudodus on 2024-08-29
You can upload big chunks of text to

[https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/)

and post a link to your particular pasted chunk (something like)

[https://pastebin.ubuntu.com/p/wCG9fgVYxG/](https://pastebin.ubuntu.com/p/wCG9fgVYxG/)

---

### Post by satimis on 2024-08-29
> **sudodus said:**
> You can upload big chunks of text to

[https://pastebin.ubuntu.com/](https://pastebin.ubuntu.com/)

and post a link to your particular pasted chunk (something like)

[https://pastebin.ubuntu.com/p/wCG9fgVYxG/](https://pastebin.ubuntu.com/p/wCG9fgVYxG/)
Hi@sudodus,

Thanks for your advice.

I have done it.  The link is here;
[https://pastebin.ubuntu.com/p/jXc63qXc53/](https://pastebin.ubuntu.com/p/jXc63qXc53/)

Regards

---

### Post by philhughes on 2024-08-29
This is may be the key:

```
Aug 23 10:24:55 2TBPCIeSSD kernel: usb 7-4.3: device not accepting address 4, error -71
```

I had a problem with a USB hub not recognizing some drives. I had the error:

```
kernel: usb 2-2: device not accepting address 8, error -62
```

Whilst troubleshooting the problem, I plugged the hub into another PC, and that would bootloop at the BIOS. Replaced the hub, problem solved.

But if you search "device not accepting address 4, error -71", you will come up with similar posts going back many years. A lot of them are solved by reaplcing hardware.

---

### Post by satimis on 2024-08-29
> **philhughes said:**
>  - snip -
Whilst troubleshooting the problem, I plugged the hub into another PC, and that would bootloop at the BIOS. Replaced the hub, problem solved.

But if you search "device not accepting address 4, error -71", you will come up with similar posts going back many years. A lot of them are solved by reaplcing hardware.
Thanks for your advice.

The funny thing happened here is using the MS keyboard on my spare PC.  It works without problem.

I think it is the time to purchase a new keyboard.  The MS keyboard has been used for >6 years, including my daily working PC.  It is time for me to build a new PC.  I'll find time searching for hardware, CPU AMD Ryzen 9 with 64G DDR4 RAM onboard, 2TB PCIe 4.0 SSD for OS only.  I have spare 4TB WD magnet drive for data storage, also 2TB USB external SSD for data sharing between PCs.

Regards

---

