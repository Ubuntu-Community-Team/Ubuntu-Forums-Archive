---
title: "How to: make a lexmark 4200 series work with Ubuntu"
date: 2005-10-27
forum: General Help
---

### Post by ThirdWorld on 2005-10-27
First of all I would like to thank the avalanche of replies on the original thread that I posted about how to make my Lexmark 4200 series work with Ubuntu. (actually only one person answered it Im just been ironic) :p 

However, i figure it out on MY OWN (thank you guys again) :p  how to make this thing work. Do i have to add that I search the entire internet for 3 days? (thank you guys again) :D 

well, this thing is actually very simple.
So if you have a lexmark 4200 series all you have to do is go to system > Adminitration > priting > Select local printer > 

your lexmark 4200 series should be listed. (make sure your USB cable is coneccted) 

Ok select Forward. 

Now select the correct driver: 

Manufacturer: Lexmark

Model: LEXMARK Z42 

Driver: High Quality Image (GIMP-Print)

Select apply.

now, turn off your printer. Disconect the power cable a reconect it again. turn power on.

You are ready to print.

Now in the ubuntu printing utility your new printer "LEXMARK Z42" shold be listed. rigth click on it and from the pop up menu select properties. 

Now you can change the printer resolution. Default is 300 Dpi which is excelent for quick prints and to save ink. If you want a good res but you dont want to waste to much ink i will recomend set it up on 600 dpi high quality.

for my all in one X4270 I can't clean or align the printer heads with this driver, in order to do that go to your printer (your actual printer) and press the copy button and then the option button several times until you can read "maintenance" then navigate with your right arrow until you get to the maintenance feature that you are interested in. You dont need software for this.

Hope this can help someone 

:razz:

---

### Post by Remmelas on 2005-10-27
I actually share my lexmark x83 over the network from my wifes windoze pc.  Works pretty well, using postscript drivers and printer redirection, etc.  In a nutshell it looks like this.  Windows machine has two printers defined.  the Lexmark x83 (the real one), and a fake one manually set up as an Apple Laserwriter II(because it uses a generic postscript driver).  Use Redmon to redirect output from the Apple Laserwriter to gsprint.exe(ghostscript goodness i think).  gsprint configured to use the Lexmark to print, and the Laserwriter printer shared either via samba or via unix print services in windows(i use the later).  Then, connect to the shared print queue from Ubuntu and presto, printing goodness.  great way to work a windoze only printer.  I only wish I could still find the original website I found it on so there was more detail, and, credit.  I'm glad you got yours to work natively connected though, i do wish I could achieve the same.

---

### Post by plunderisley on 2007-08-26
Any way to get the scanner working?

---

### Post by mrpippal on 2008-04-06
This was a big help - thank you!

---

### Post by ashvee on 2008-04-09
is there any way for lexmark x5470 to print in ubuntu

---

### Post by ashvee on 2008-04-09
its gr8 to hear tht x4270 is working in ubuntu

so there is chance for x5470 

is there anyone tried for x5470

---

### Post by ashvee on 2008-04-09
[COLOR="Red"][QUOTE=ThirdWorld;448851]First of all I would like to thank the avalanche of replies on the original thread that I posted about how to make my Lexmark 4200 series work with Ubuntu. (actually only one person answered it Im just been ironic) :p 

However, i figure it out on MY OWN (thank you guys again) :p  how to make this thing work. Do i have to add that I search the entire internet for 3 days? (thank you guys again) :D 

well, this thing is actually very simple.
So if you have a lexmark 4200 series all you have to do is go to system > Adminitration > priting > Select local printer >[/COLOR] 

[quote]
 
hi which version of ubuntu r u using  is it Gutsy Gibbon

---

### Post by Terraformgrigsby on 2008-07-22
> **ThirdWorld said:**
> First of all I would like to thank the avalanche of replies on the original thread that I posted about how to make my Lexmark 4200 series work with Ubuntu. (actually only one person answered it Im just been ironic) :p 

However, i figure it out on MY OWN (thank you guys again) :p  how to make this thing work. Do i have to add that I search the entire internet for 3 days? (thank you guys again) :D 

well, this thing is actually very simple.
So if you have a lexmark 4200 series all you have to do is go to system > Adminitration > priting > Select local printer > 

your lexmark 4200 series should be listed. (make sure your USB cable is coneccted) 

Ok select Forward. 

Now select the correct driver: 

Manufacturer: Lexmark

Model: LEXMARK Z42 

Driver: High Quality Image (GIMP-Print)

Select apply.

now, turn off your printer. Disconect the power cable a reconect it again. turn power on.

You are ready to print.

Now in the ubuntu printing utility your new printer "LEXMARK Z42" shold be listed. rigth click on it and from the pop up menu select properties. 

Now you can change the printer resolution. Default is 300 Dpi which is excelent for quick prints and to save ink. If you want a good res but you dont want to waste to much ink i will recomend set it up on 600 dpi high quality.

for my all in one X4270 I can't clean or align the printer heads with this driver, in order to do that go to your printer (your actual printer) and press the copy button and then the option button several times until you can read "maintenance" then navigate with your right arrow until you get to the maintenance feature that you are interested in. You dont need software for this.

Hope this can help someone 

:razz:
Thank you that helped alot I thought I was going to have to buy another printer again thankyou soooo much!!!!!!

---

