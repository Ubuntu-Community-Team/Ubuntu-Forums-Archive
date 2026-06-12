---
title: "Slow Ubuntu launching"
date: 2021-04-21
forum: General Help
---

### Post by 3ugener on 2021-04-21
Hello there. It's my first thread here, so promise me if it's on the wrong forum branch. I'm recently tried to format my flash drive and accidentally format EFI partition cuz i'm was using terminal commands and picked wrong partition. So, after that i restored grub and my Ubuntu drives correctly. But there was also Windows 10 on my SSD and it's EFI partition also broken. I'm not hurry with restore Windows because it's not so important till i have working Ubuntu. But, the problem is that Ubuntu launching very long now. Grub doesn't see my Windows, as is broken, so what can take so much time to launch Ubuntu now? Loading screen shows my motherboard logo, Ubuntu logo and rotating circle for about 30-40 (with SSD it's really badly), but earlier it takes about 7-10 seconds to launch. I installed Grub Customizer and turned off searching for another OSes but this doesn't affect at all on the situation. Should i necessarily restore Windows so that problem could be fixed?

---

### Post by ajgreeny on 2021-04-21
I can't help with Windows but by removing the EFI partition I am surprised that you can boot any of the OSs on your machine.
However, it sounds as if you have, or had, more than the single EFI partition that is the normal situation even on a dual boot.

See **Boot-Repair** in my signature below and follow the instructions there just to run the Boot-Info-Script.
**Do not run the default repair or any other action just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by CelticWarrior on 2021-04-21
> **ajgreeny said:**
> I can't help with Windows but by removing the EFI partition I am surprised that you can boot any of the OSs on your machine.
However, it sounds as if you have, or had, more than the single EFI partition that is the normal situation even on a dual boot.



Probably because
> [COLOR=#000000]after that i restored grub and my Ubuntu drives correctly[/COLOR]
Meaning: Installed Grub for BIOS by reading an old guide and copy/pasting commands. Effectively turning it into a legacy installation. Unsurprisingly > [COLOR=#000000]Ubuntu launching very long now[/COLOR] and Windows is unbootable. > [COLOR=#000000]there was also Windows 10 on my SSD and it's EFI partition also broken[/COLOR] is almost certainly a misunderstanding. It's the same ESP that was deleted.

---

### Post by ajgreeny on 2021-04-22
CW, thinking about this a bit deeper you may well be correct but it would be useful to see the output of the Boot-Info script, which I am assuming will still see Windows 10 being present even if neither grub or Windows' own bootloader can not boot it at all.

I have never had a Windows installation within the life of Boot-Repair so I'm not sure what is needed for the script to see that it exists but I assume it will find it.

We'll see!

---

### Post by 3ugener on 2021-04-23
Hello lads! Thank you for joining the conversation. This is what Gparted shows:[https://flic.kr/ps/3WsLwG](https://flic.kr/ps/3WsLwG)
There is some Microsoft reserved partiotion and the warning sign says that this filesystem is damaged.

Okay, i will try this one, thank you!
> **ajgreeny said:**
> CW, thinking about this a bit deeper you may well be correct but it would be useful to see the output of the Boot-Info script, which I am assuming will still see Windows 10 being present even if neither grub or Windows' own bootloader can not boot it at all.

I have never had a Windows installation within the life of Boot-Repair so I'm not sure what is needed for the script to see that it exists but I assume it will find it.

We'll see!

---

### Post by deadflowr on 2021-04-23
Use the attachment feature to upload images.
(The attachment feature is the paperclip icon in the toolbar.)
(Use the Reply to Thread option to enable the paperclip in the toolbar, as it isn't available in the Quick Reply option)
or use an online photo sharing site like imgur. And post a link.

---

### Post by 3ugener on 2021-04-23
This is what i've got [https://paste.ubuntu.com/p/6rZssWnrxt/](https://paste.ubuntu.com/p/6rZssWnrxt/)

---

### Post by 3ugener on 2021-04-23
Pal, i've used attachment feature but image was not displayed correctly and there was a little icon near the text.> Use the attachment feature to upload images.

---

### Post by 3ugener on 2021-04-27
So what for now? Should i try to repair Windows partition with the tool that you recommended?

---

### Post by tea for one on 2021-04-27
[COLOR="#0000FF"]Line 225 [/COLOR] - LegacyWindows detected

In order to dual boot on **one** drive, you have to install both systems in the same mode i.e. UEFI mode with GPT is ideal.

Do you have back ups of your personal data from both your Ubuntu and Windows systems?
If not, back up now via a live session.

I would re-install both systems correctly and then restore the back-ups.

Have a look at this info [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

