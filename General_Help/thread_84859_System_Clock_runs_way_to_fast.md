---
title: "System Clock runs way to fast"
date: 2005-11-01
forum: General Help
---

### Post by UeB on 2005-11-01
Hallo,

i am new to Ubuntu ( i installed it just 2 days ago) and was positivly suprised by the good hardware detection. but it has the very anoying problem: the system clock runs at least with double the speed as it should.
This problem does not accure in windwos xp which was pre installed (and still is) on this machine and also does not accure in the bios so i assume that the motherboard clock runs fine.
By searching the forum i found this [http://www.ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed]("http://www.ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed")
but it says it is only "your problem" when the cpu usage is constantly at 50% or higher which is not the case: it is only at about 2% constantly.

Details:
Ubuntu 5.10 (i386) on an Acer Aspire 3022WLMi - Mobile AMD Sempron 2800+ (25W)/ 512MB/ 80GB/ Double Layer DVD&#177;RW / 15.4" WXGA TFT/ ATI X600 64MB/ 802.11g W-LAN/

---

### Post by UeB on 2005-11-02
<push>

---

### Post by RAOF on 2005-11-02
Is it easy for you to try a Breezy64 live cd?  I'd first want to check that this "double clock speed" bug is not your problem.  That seems like the most likely problem, given your clock is running "at least with double the speed it should" :)

---

### Post by UeB on 2005-11-02
[QUOTE=RAOF]Is it easy for you to try a Breezy64 live cd?[/QUOTE]
It is impossible because the sempron cpu in my notebook doesnt support AMD64

---

### Post by UeB on 2005-11-02
ok seems to be solved

the clock is running at normal speed after i did
> 
UBUNTU 32BIT SECTION

b) If you have installed Ubuntu...
If you have installed Ubuntu and you want to see if it works for you:
as soon as you turn on your computer after the bios you will see a the word "GRUB" etc. press ESC until it gets you to Grub boot menu and select kernel 2.6.10 from the list and press "e" to edit the line and add:
noapic nolapic


i was just to shy to try it right away

---

