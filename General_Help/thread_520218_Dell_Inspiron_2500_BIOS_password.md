---
title: "Dell Inspiron 2500 BIOS password"
date: 2007-08-07
forum: General Help
---

### Post by wie6Ein0 on 2007-08-07
[COLOR=DimGray]I have made this question easy for you all. First, there is the long version (including a back story), and then there is the short version (including only the important details). I hope that someone can help me!
[/COLOR] [COLOR=DimGray][B]
[COLOR=Black] LONG VERSION:[/COLOR][/B]
I recently bought a used laptop from a second-hand store. I brought it home only to find out that there was a password set for the BIOS and the Primary HDD. After messing with the laptop for an hour, I found the correct password for the HDD (the password was "12345678") and laughed for a few minutes about how simple it was. After inputting the HDD password, I was told that Windows 2000 was missing a file and could not boot. Anyway, half of the problem is solved. What I need now is a way to bypass the main BIOS password. I'm hoping that someone can help me because I've searched many sites and have tried many methods but I can't get past the password. I took apart the laptop but did not see any CMOS battery, so that didn't help much... I read somewhere that jumping a few pins with a paperclip or wire might help to reset the password but I'm not even sure which pins to do it to with this computer. Please, help me!

** [COLOR=Black] SHORT VERSION:[/COLOR]**[/COLOR][COLOR=DimGray]
I'm locked out of my laptop computer due to a password protected BIOS. I need a way to bypass the password. What can I do?

[/COLOR]  [COLOR=DimGray][B][COLOR=Black]Dell Inspiron 2500
Phoenix BIOS[/COLOR][/B]
[/COLOR]

---

### Post by n1418 on 2007-10-25
I'm not positive, but the boot password is usually the same as the BIOS password (to get into the "setup" section)  If this is the case, simply go into the BIOS setup and change/reset the power on password there.

If not, you'll need to manually reset the CMOS, which in turn will clear the BIOS of all settings.

Go to dell's support website.  

Find the documentation for your laptop detailing its disassembly.  This should be called "product documentation" or "user manual", etc.

Following the instructions, take your laptop apart until you have the motherboard "aka mainboard" exposed.

See if your instructions mention a "RTC reset" "BIOS reset" "CMOS Reset" "CMOS Clear", etc.

If they don't, pull out a flash light and look on the board itself.  Many times a three-pronged jumper will be labeled one of the above names.

If nothing is labeled, try to find a jumper near the little watch batter located on the board.

If you can find that jumper, assume the pins its on initial are "1" and "2".  Take the jumper off and jump pins "2" and "3".  Leave in place for about a minute.  Return the jumper to the original position, and you're good to go.

I hope this helps!

---

