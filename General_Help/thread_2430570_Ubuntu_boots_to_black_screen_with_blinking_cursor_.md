---
title: "Ubuntu boots to black screen with blinking cursor after reboot"
date: 2019-11-04
forum: General Help
---

### Post by Fabio_Valentino on 2019-11-04
[COLOR=#141414][FONT=&amp]Hello,[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]I have aUDOO X86 Ultra and used it for over two years now, it has ubuntu 18.04 installed[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]My linux mount setup is as follows:[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Internal emmc: mounted as /[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]External SD card with 5 partitions, /var /opt /etc /usr and /home[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]I also have attached a SATA 700 GB HDD mounted as /media/SATADisk/ and an USB 2 TB HDD mounted as /media/USBDisk/[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Yesterday i've tried to scheduled an fdisk at boot with every device, but found no errors[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]I noticed in the last two weeks that when i do a "sudo reboot" at restart my udoo hangs with a black screen with a blinking cursor and doesn't even boots ubuntu[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]I don't understand if It is a grub problem or an error on the udoo bootloader, it is very strange because if I physically remove the A/C adapter and put it back on , the udoo just boots with no errors.[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]I've also posted this on udoo forums since I don't understand if it is a udoo problem or a ubuntu setup error

[/FONT][/COLOR][https://www.udoo.org/forum/threads/udoo-boots-to-black-screen-with-blinking-cursor-after-reboot.29866/](https://www.udoo.org/forum/threads/udoo-boots-to-black-screen-with-blinking-cursor-after-reboot.29866/)
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Can anyone help me?[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]
[/FONT][/COLOR]
[COLOR=#141414][FONT=&amp]Thanks[/FONT][/COLOR]

---

### Post by Chronon on 2019-11-06
Are you able to switch to tty2, for example?

---

