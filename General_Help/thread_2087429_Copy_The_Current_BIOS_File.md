---
title: "Copy The Current BIOS File"
date: 2012-11-23
forum: General Help
---

### Post by Melita on 2012-11-23
My OS is Ubuntu 12.04. I am about to update the BIOS file of my Main Board ASUS P5LD2.
Before doing the update, _I need to copy the **current** BIOS_ file to a CD or a DVD as a back up, if the BIOS fails or gets corrupted during the update.  How can I do this from the Ubuntu OS.

Thank you.

---

### Post by Frogs Hair on 2012-11-23
With my Asus mobo the old Bios versions are available on their website so it is a matter down loading the one currently in use in case the new one would happen to fail. Only update if the the new Bios has benefits for your current system/hardware.

---

### Post by Melita on 2012-11-23
Thank you, but I am looking for a way to copy the current BIOS with the current settings, the way it can be done in a Windows OS environment (a few easy steps with Windows). My only OS is ubuntu and I have only three days experience with it! Hence, this question.
 
Regards.

---

### Post by Wim Sturkenboom on 2012-11-24
It's only a few easy steps in Windows because Asus provides software for Windows to do it.

If you still have a floppy drive and floppies, you should be able to make a bootable dos floppy in Linux (do a search) and take it from there.

---

### Post by dcstar on 2012-11-24
> **Melita said:**
> My OS is Ubuntu 12.04. I am about to update the BIOS file of my Main Board ASUS P5LD2.
Before doing the update, _I need to copy the **current** BIOS_ file to a CD or a DVD as a back up, if the BIOS fails or gets corrupted during the update.  How can I do this from the Ubuntu OS.

Thank you.

See if the **flashrom** package works on your hardware.

---

### Post by jerome1232 on 2012-11-24
Just throwing this out there, if your bios becomes corrupted during the update process your computer will likely become unbootable and a backup image will do little good.

---

### Post by Wim Sturkenboom on 2012-11-24
> 
Just throwing this out there, if your bios becomes corrupted during the update process your computer will likely become unbootable and a backup image will do little good.


The Asus seems to have recovery options in case the update fails; if I understand the manual correctly, one can still boot from the 'driver' CD and do recovery.

The days of not being able to do anything due to a failed bios flash should be long gone. The system does not have to flash the complete flash memory; it can leave a part untouched and that part can contain some basic functionality (e.g. to read a floppy or CD and do a flash operation).

---

### Post by Melita on 2012-11-25
> **Wim Sturkenboom said:**
> The Asus seems to have recovery options in case the update fails; if I understand the manual correctly, one can still boot from the 'driver' CD and do recovery.
 
The days of not being able to do anything due to a failed bios flash should be long gone. The system does not have to flash the complete flash memory; it can leave a part untouched and that part can contain some basic functionality (e.g. to read a floppy or CD and do a flash operation).
This is my worry. How can I find out whether my particular system would leave a part untouched, that contain some basic functionality, to read a CD or DVD? I have neither floppy nor Asus Support CD (secondhand computer). I am unable to find the answer to this from the manual.
 
Regards.

---

### Post by Wim Sturkenboom on 2012-11-25
If you have don't have the manual, download it. If I did download the correct one (P5LD2 without any additional description), it states that (in my words) you can recover a broken BIOS; you however need a CD or floppy with a BIOS image on it.

Check the Asus website if you can download the CD for your motherboard.

---

### Post by Melita on 2012-11-25
I have down loaded the manual. What you have got is the correct one - P5LD2 (without additional description). 
 
Form the manual, I don't understand whether the "system would leave a part untouched, that contain some basic functionality, to read a CD or DVD". Could you understand something of the sort from the manual? My experience is very limited. The BIOS default date is 01/01/2002. So I believe the P5LD2 is that old.  
 
I have already checked about the support CD and it is **not** available for download at the asus website.

---

### Post by Wim Sturkenboom on 2012-11-25
From the manual
> 
4.1.3      ASUS CrashFree BIOS 2 utility
The ASUS CrashFree BIOS 2 is an auto recovery tool that allows you to
restore the BIOS file when it fails or gets corrupted during the updating
process. You can update a corrupted BIOS file using the motherboard
support CD or the floppy disk that contains the updated BIOS file.

This implies that a CD/floppy can be accessed from a corrupted BIOS.

---

### Post by Mark Phelps on 2012-11-25
The last ASUS mobo I used had something named EZ-Flash (or something like that).  It was invoked using a special key combination when you booted the CD.

Using it, you booted into EZ-flash, and was presented with a menu of choices.  You always followed the first choice to save off the existing BIOS to a diskette.  Then, you inserted the diskette with the new BIOS image file and flashed from that.

You didn't need Windows to do the flashing, but you did need something to format the diskette and write the flash image file to it.

I would advise that, without a way of RECOVERING the current BIOS (from diskette or USB) or from a saved copy of the BIOS (some ASUS Mobos are dual-BIOS, meaning, they have a second BIOS chip and a way to boot from that one), flashing your BIOS is a VERY DANGEROUS thing and should NOT be attempted.

---

### Post by jerome1232 on 2012-11-25
Speaking from experience my computer says you can restore the bios from backup image, however I had a bios update go wrong, and the system would do nothing on power up. I had to order a new bios chip online, it was only 7 bucks but it was a week with only my netbook to use as a computer.

---

### Post by Melita on 2012-11-25
Thank you all, for the help. If things go as bad as a 'dead computer' (as jerome1232 says), what options do I have after that, to get my computer working again? ](*,)
 
Regards.

---

### Post by dcstar on 2012-11-26
> **Melita said:**
> Thank you all, for the help. If things go as bad as a 'dead computer' (as jerome1232 says), what options do I have after that, to get my computer working again? ](*,)


You go to a hardware forum for your particular motherboard.

This is **not** an Ubuntu issue.

---

### Post by Zill on 2012-11-26
> **Melita said:**
> My OS is Ubuntu 12.04. I am about to update the BIOS file of my Main Board ASUS P5LD2...
Just to ask the obvious question... *Why* do you want to update the BIOS?

Updating a working BIOS is normally unnecessary, unless you have discovered a particular incompatibility with your PC hardware.

There is a high risk of breaking your PC if you play around with BIOS upgrades for no good reason!

---

### Post by Melita on 2012-11-26
Mine is a second hand computer (little used and in very good condition) that I got without the HDD. I installed a new HDD, WD5000AAKX and installed Ubuntu 12.04 as the OS. The computer is working well, except for the following.
 
CMOS RAM is not saving the date and time. If the computer is unplugged from the mains or switched off from the power supply ON/OFF switch, when switching ON and starting the computer again, I get the following message from the boot menu.
"CMOS settings wrong
CMOS date/time not set
Press F1 to run set up
Press F2 to load default values and continue"
When F2 is pressed it boots normally. Else, I have to press F1 and reset Date/Time for it to boot. 'Save and exit' from the boot menu done properly. Battery contacts cleaned with alcohol and new batteries installed twice. Batteries checked with volt meter and battery tester - nothing wrong with them. Not knowing any other solution, I thought of updating the BIOS (the default CMOS date is 01/01/2002). Hence, my original question - how to make a copy of my current BIOS from Ubuntu before doing an update.
 
I had no idea that a BIOS update could result in such serious consequences.
 
Thank you,
Best regards.

---

### Post by Zill on 2012-11-26
> **Melita said:**
> ...CMOS RAM is not saving the date and time. If the computer is unplugged from the mains or switched off from the power supply ON/OFF switch, when switching ON and starting the computer again, I get the following message from the boot menu.
"CMOS settings wrong
CMOS date/time not set
Press F1 to run set up
Press F2 to load default values and continue"
When F2 is pressed it boots normally. Else, I have to press F1 and reset Date/Time for it to boot. 'Save and exit' from the boot menu done properly. Battery contacts cleaned with alcohol and new batteries installed twice. Batteries checked with volt meter and battery tester - nothing wrong with them. Not knowing any other solution, I thought of updating the BIOS (the default CMOS date is 01/01/2002)...
These are all classic symptoms of a flat CMOS (BIOS) battery!  AIUI, most motherboards use a *single* button cell for this function and so your reference to *batteries* (plural) worries me. :-(  Does your ASUS P5LD2 have *one* or more than one cells?

If we are talking about the same CMOS battery (possibly a CR2032) then changing this for a new one should resolve your problem.

If a (good) new cell is installed then I suggest you could try resetting the CMOS back to defaults and how to do this is clearly explained in the ASUS P5LD2 motherboard manual.  See "Clear RTC RAM (CLRTC)" in para 2.6 entitled "Jumpers".  This will reset the BIOS settings to default and so you will have to re-enter any custom settings you need.

The motherboard manual can be downloaded from [http://www.asus.com:](http://www.asus.com:) [P5LD2 English Edition User's Manual(e2706)]("http://www.asus.com/Motherboards/Intel_Socket_775/P5LD2/#download")

---

### Post by Mark Phelps on 2012-11-26
> **Melita said:**
> Thank you all, for the help. If things go as bad as a 'dead computer' (as jerome1232 says), what options do I have after that, to get my computer working again? ](*,)
 
Regards.

DEPENDS ... 

If the MOBO has dual-BIOS chips and there is a way to select the OTHER BIOS chip, then you can boot using that.

IF the BIOS chip is replaceable (not all of them are), AND you can purchase a replacement online, AND you know to remove and insert BIOS chips without damaging them (a lot of IF's) then you would be able to boot your PC again.

---

### Post by Melita on 2012-11-26
My apologies for the confusion with** 'batteries'**. Yes it is CR 2032 and only a single battery is used. When the first *new* replacement didn't work, I replaced it with another* new* one. So there is a new battery there now.
 
I have got the manual and as you suggest, I will clear the RTC RAM using the jumper, as explained in the manual. I will re-enter the settings and this time I will keep the computer plugged on for about 24 hours for good measure, and see how it goes.
 
In reply to Mark Phelps - There is only a single BIOS chip and it is soldered to the board. So this option is not available. In any case, the risks outlined above made me loose my nerve about BIOS update! 
 
Thank you
Best regards.

---

### Post by Zill on 2012-11-27
> **Melita said:**
> ...I have got the manual and as you suggest, I will clear the RTC RAM using the jumper, as explained in the manual. I will re-enter the settings and this time I will keep the computer plugged on for about 24 hours for good measure, and see how it goes...
The function of the battery is to hold the CMOS settings while the computer is *off* and so there is no *need* to keep the PC powered-up for 24 hours unless you wish to do so.  Once the BIOS has been correctly set up such that the OS displays the correct time then it should be possible to power-down the PC fully and then restart.  If the PC retains the correct time then the CMOS battery is working correctly.

ps.  Just a thought - please make *sure* the battery is the right way round. ;-)

---

### Post by Melita on 2012-11-28
Problem solved! I cleared the RTC RAM using the jumper. At first it did't work. I kept on setting the date/time, over again. After the third time, the battery started saving it. I have checked it for two days, including an over night 'power off' and the computer is booting normally.
 
I am glad I took the advice and didn't try the BIOS update. Thank you very much for all the help. By the way, the battery* was* right side up!
 
Best regards.

---

### Post by robert shearer on 2012-11-28
Not to rain on your parade but I suspect that if you left it powered off for several days you would find it back to square one on restart.

The symptoms you describe suggest the possibility of faulty capacitors on board and should the problem reappear then try searching for 'bad caps'.

That said, I sincerely hope I am wrong and that whatever recovery has occured has fixed your compys problems so it gives you many years of solid use. :)

---

### Post by Melita on 2012-11-28
I did a thorough visual check of the complete board and the capacitors looked good and shiny. I know this is not conclusive but what else can I do with a computer board? I have much success in reforming the big electrolytic capacitors in my vintage valve (tube) equipment, but can I do anything more than a visual check here? They are all intact (not split at the top), not discoloured and no signs of over heating. 
 
Regards.

---

