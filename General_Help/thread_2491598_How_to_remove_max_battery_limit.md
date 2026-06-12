---
title: "How to remove max battery limit?"
date: 2023-10-14
forum: General Help
---

### Post by luncaaa on 2023-10-14
Hello!

I have Lubuntu installed in a computer but, for some reason, the maximum charge is limited at 50% and I do not recall changing any setting related to the battery. The computer is kind of old so maybe that's the problem, but I'm not sure... Can this limit be removed?

This is what I mean:

(sorry for not taking a screenshot instead - I am writing this in another computer because that one is old and would take a lot of time to send it there)

---

### Post by #&amp;thj^% on 2023-10-14
What make and model is it?

---

### Post by luncaaa on 2023-10-14
It's an Acer Aspire V5-123

---

### Post by #&amp;thj^% on 2023-10-14
Dang if it was a Lenovo I could help you.
But Acer has a utility for windows: [https://i.stack.imgur.com/AJT6J.png](https://i.stack.imgur.com/AJT6J.png)
Acer Care Center, or have you checked your bios for such a setting?

---

### Post by luncaaa on 2023-10-14
I have entered the BIOS using F2 when I turn on my computer but I cannot find any setting related to the battery, and I do not have Acer Care Center installed. I also can't find any setting related to the charge limit in Lubuntu's configuration. I don't remember if I had this problem when Windows was installed or not. Is there maybe any command which changes this limit? Or is it a problem with the battery itself?

---

### Post by #&amp;thj^% on 2023-10-14
> **luncaaa said:**
> I have entered the BIOS using F2 when I turn on my computer but I cannot find any setting related to the battery, and I do not have Acer Care Center installed. I also can't find any setting related to the charge limit in Lubuntu's configuration. I don't remember if I had this problem when Windows was installed or not. Is there maybe any command which changes this limit? Or is it a problem with the battery itself?
That application is a Windows Only.
Hopefully this might help you [https://community.acer.com/en/kb/articles/75-acer-internal-battery-reset](https://community.acer.com/en/kb/articles/75-acer-internal-battery-reset)
On my Lenovo's  i use this:
```
ls /sys/bus/platform/drivers/ideapad_acpi
``` 
Now for me not sure about yours though I'm looking @
```
bind  module  uevent  unbind  VPC2004:00

```
For my reset now I'll use:
```
# echo 0 | sudo tee /sys/bus/platform/drivers/ideapad_acpi/VPC2004:00/conservation_mode
```
I'm very doubtful that Acer would work with that, so that Link i showed is your best course of action ATM

---

### Post by luncaaa on 2023-10-14
I tried the reset thing and now the limit is at 47% - How can I know if I reset it properly? Is there an indicator or something?
And those commands don't seem to work on acer as it says that it couldn't find the file or directory. These are the directories I have:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=292856&stc=1[/IMG]

---

### Post by #&amp;thj^% on 2023-10-14
pull the charging brick out of the wall socket/plug (wait 30 40 seconds), and then plug it back in. (Don't pull it from the Laptop)
It should now show "charging with a lighting bolt" icon.

I was very sure the commands were worthless on an Acer, but thanks for the feedback might be useful for someone else.
Also have a look here: [https://manual.lubuntu.me/stable/3/3.2/3.2.12/power_management.html](https://manual.lubuntu.me/stable/3/3.2/3.2.12/power_management.html)

---

### Post by luncaaa on 2023-10-14
Nono, it did not work because there is no "ideapad_acpi"
However, in the image you can see that:
- In the drivers folder, there is "acpi-fan", "acpi-ged" and "acpi-wmi"
- In the "sys/bus" folder, there is "acpi", and "sys/bus/acpi/drivers" contains: ac, battery, button, ec, hardware_error_device, hpet, thermal, tpm_crb and video

---

### Post by luncaaa on 2023-10-14
Ok, so I have tried running the following commands:
```
cat /sys/bus/acpi/drivers/battery/PNP0C0A:00/power_supply/BAT1/charge_full_design
```
This returns "2500000"
And this:
```
cat /sys/bus/acpi/drivers/battery/PNP0C0A:00/power_supply/BAT1/charge_full
```
This returns "1187000"

using "sudo tee" instead of "cat" returns "permission denied"... what can I do? I'm sorry if these question seem dumb, I don't really know much about linux commands.
I have also tried investigating a bit and it seems like this could be caused because the battery is dying and there is nothing I can do other than buying a new one... Is this the only alternative?

---

### Post by Holger_Gehrke on 2023-10-14
How old is that battery ? The first screenshot says it's designed to hold 37 Watt Hours and can hold 18.62 Wh and has a charge of 12.7 Wh currently. Batteries lose capacity as they age. A short search for this machine says Acer introduced them in 2013. If that's the age of your machine and the battery hasn't been changed, then 50% of design power is about what I'd expect. While there are some things that one can do to rechargeable batteries to get some capacity back - depending on the technology / chemistry used - these are usually tricky, risky, and should be left to people who know what they're doing (so not me ...).

Holger

---

### Post by #&amp;thj^% on 2023-10-14
> **Holger_Gehrke said:**
> How old is that battery ? The first screenshot says it's designed to hold 37 Watt Hours and can hold 18.62 Wh and has a charge of 12.7 Wh currently. Batteries lose capacity as they age. A short search for this machine says Acer introduced them in 2013. If that's the age of your machine and the battery hasn't been changed, then 50% of design power is about what I'd expect. While there are some things that one can do to rechargeable batteries to get some capacity back - depending on the technology / chemistry used - these are usually tricky, risky, and should be left to people who know what they're doing (so not me ...).

Holger

Couldn't have said it better...+1
We gave it our safest try's it is time to start looking for a replacement.
Maybe not today but should be on the to do list. ;)

---

### Post by TenPlus1 on 2023-10-15
From what I've seen Kubuntu power settings has an option to change those values.

---

### Post by luncaaa on 2023-10-15
Okay, I will see if I can buy a new battery. Thank you all!

---

