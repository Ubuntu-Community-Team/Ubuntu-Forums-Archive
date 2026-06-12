---
title: "Asus ROG cannot boot"
date: 2015-07-12
forum: General Help
---

### Post by erebus314 on 2015-07-12
I am a rare user of ubuntu and I really don't understand how to use it very well. I believe I have 14.04 installed although I use it so little I'm not certain. It may be 14.10.

Anyway I used it yesterday to do some photo editing and it ran quite a large update. I rebooted back into windows and finished my work. Now I am switching my laptop on today and instead of it booting into windows as it normally does (usually to get ubuntu I need to press escape and then select windows from the asus boot menu, and I get the ubuntu boot menu) it instead loaded up 'GNU GRUB version 2.02~beta2-9ubuntu1.3" with the prompt 'grub>'

I have been looking online for some fix to this and the best I have found is here:

[https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)

But I get quite different results. When I run ls I get:

(hd0) (hd0,gpt6)...(hd0,gpt1)

Which I think I understand from the website. But when I run 'ls (hd0,5)/' for example I get 'error unknown file system'

The only thing I can read is (hd0,1) which gives me "efi/"

I then run ```
ls (hd0,1)/efi
``` and I get:

./../ Microsoft/ Boot/ asus/ ubuntu

Repeating this to check ubuntu I find:

./ ../ shimx64.efi grubx64.efi MokManager.efi grub.cfg

Checking asus I find:

./ ../ bcd bcd.log BCD.LOG1 BCD.LOG2 en-GB/ de-DE/ fr-FR/ it-IT/ nl-NL/

Checking Boot I find:

./ ../ bootx64.efi

Checking Microsoft I get another folder called Boot, which contains:

bg-BG/ boot.stl bootmgfw.efi bootmgr.efi cs-Cz/ en-GB/ en-US/ es-ES/ memtest.efi/ qps-ploc/ bootstat.data Fonts/Resources/ bcd bcd.log BCD.LOG1 BCD.LOG2

The instructions above assume I can find something in 'bin' which doesn't seem to exist anywhere. Also pressing tab after typing "linux /boot/vml" does nothing.

I have checked other instructions online and they are either for different problems or stated in such a way as I can't understand. Looking through the forum I see that others have had this problem but the answers are really for people who know a lot more than me. I don't know grub or ubuntu commands.

I would be really grateful if someone could tell me how I can access my computer as this is really stressful as I need it for work.

It has always worked fine before and it booted back into windows. Something seems to have happened overnight

Please let me know if I can provide any more details

Thanks

---

