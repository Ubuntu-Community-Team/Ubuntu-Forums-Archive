---
title: "Crazy Stuff happening when I put computer in sleep mode, try to restart it and again"
date: 2015-10-19
forum: General Help
---

### Post by ashinsky123 on 2015-10-19
Correct me if I'm not asking in the right forum but something has happened to my computer and I've tried everything I could think of but nothing worked. So recently when I put my computer to sleep and then try to turn it back on the Wi-Fi networks aren't there and the only way I've been dealing with this is by restarting my computer... twice (I'm sure this is only me because no one else in my family has this problem). I don't know if it's at all related to my next problem or not, but I will say it anyway. My other problem is that when I DO restart the computer once, the Dell logo comes up and then I just get a purple screen (as if it's starting to boot up Ubuntu). So, I restart it again and this time I am shown a box with three options (before Ubuntu even boots up): I don't remember them exactly but I think they are: "Start Ubuntu", "Advanced options", and something else that I've never used. Then, the only way to get my computer to work is to choose the "advanced options" and from there I choose one that includes, in parentheses, startmd, or something like that. Sorry if this is not clear enough but it's been happening way too often and it wastes my time... I still have work to do and then this happens. :mad: anyway if anyone could help me out here I'd really appreciate it, thanks! :)

---

### Post by touko-herranen on 2015-11-11
Yes, I have the exact same issue as you described on my HP Pavilion 13". I have to use these prefixes in GRUB in order to get Ubuntu started and screen brightness + wireless working:  
[FONT=system]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor acpi_osi='!Windows 2013' acpi_osi='!Windows 2012'"[/FONT]

Without these I will get the purple screen every time after GRUB selection. I wonder if these sleep->reboot->purple-screen issues are actually related to some of these configuration and power interface stuff.

---

