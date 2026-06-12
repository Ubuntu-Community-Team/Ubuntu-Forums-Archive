---
title: "XFCE: problem with font sizes"
date: 2006-07-21
forum: General Help
---

### Post by evaldas on 2006-07-21
hi there,

installed fresh Xubuntu 6.06. Then added ms core fonts
> sudo apt-get install msttcorefontsalso copied Tahoma ttfs (got separately) to /usr/share/fonts/truetype/msttcorefonts. But got strange problem with font sizes.

When I set Font to Tahoma 9 in Applications->Settings->User Interface Settings, in Firefox menus I really get Tahoma 9 font, but the XFCE desktop's real font size is smaller than Tahoma 9 (image attached).
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13067&d=1153509099[/IMG]

The problem here is, that I don't like Tahoma 9, it's too big for me, so I'd like to use Tahoma 8 as the main font. When I set font to Tahoma 8, in Firefox menus I get Tahoma 8, but in other places of XFCE desktop font becomes even smaller (second image attached).
[IMG]http://www.ubuntuforums.org/attachment.php?attachmentid=13068&d=1153509099[/IMG]

So, how to make that Tahoma 8 would be everywhere? In Ubuntu (GNOME) font size was equal anywhere.

P.S. If I remember correctly, it's not only the problem with Tahoma font. Default XFCE's font is Sans 9, and for example if you change the Sans size to 8 you'll also get the same anomalies.

---

### Post by l.tambiah on 2006-08-02
I added XFCE to my laptop today and also spot the same issue regarding fonts of desktop compared to firefox. Strange though because Thunderbird displays the fonts at the same size as desktop. Do not know how to get around this.

---

### Post by l.tambiah on 2006-08-02
We should change an option for the font settings in Firefox. Open Firefox, Click the "*Edit*" menu, select "*Preferences*", click "*Content Tab*", under the font section click the "*advanced*" button and select the Display Resolution to be the "*System Setting*". Now go back to your *Applications>Settings>User Interface* *Settings* and select the size you require to effect all applictions. ****** Note firefox will have to be closed and restarted after you select and confirm the Display Resolution.*

Hope this helps....

---

### Post by evaldas on 2006-08-04
I solved the problem by setting DPI in xorg.conf (by default it was 75 or 72 on my system). Also I added line ```
Xft.dpi: 96
``` to file ~/.config/xfce4/Xft.xrdb

update: here's a little guide how to set DPI in xorg.conf [http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html](http://xubuntulinux.blogspot.com/2006/07/ubuntu-set-correct-dpi-for-x-server.html)

---

### Post by jrblevin on 2006-08-09
> **l.tambiah said:**
> We should change an option for the font settings in Firefox. Open Firefox, Click the "*Edit*" menu, select "*Preferences*", click "*Content Tab*", under the font section click the "*advanced*" button and select the Display Resolution to be the "*System Setting*".

Thanks!  I have been wondering about this for a few weeks.  I have seen that option before but I never really thought about it what it was used for.  That solved the problem for me.

Also, thanks for your detailed posting evaldas.

---

### Post by TuxCrafter on 2006-12-24
I may have more info about this problem

see the attachment

---

### Post by BroadArrow on 2007-05-25
> **evaldas said:**
> I solved the problem by setting DPI in xorg.conf (by default it was 75 or 72 on my system). 

Newbie question: how do you know what DPI setting to use? I assume this is related to my display (currently a laptop LCD)?

---

### Post by TuxCrafter on 2007-05-25
see the attachment in my previous post, there is a calculation for the DPI in it.

---

### Post by adlin5000 on 2007-11-05
After about 3 months of working I figured out the problem. XFCE uses the EDID info from your monitor to set the display size, and then calculates the DPI from that. Setting the DPI in your xorg.conf does you no good because XFCE overrides it. Editing the xfce config files doesn't work either because it just ignores it and figures it out for itself. Finally I found the xorg.conf options to ignore EDID and DDC settings. 
```
	Option "IgnoreEDID" "true"
	Option "NoDDC" "true"
```
Then you have to put in the settings for your monitor because it wont detect them. Change the numbers to the settings of your monitor. You can calculate the display size by using resolution / DPI * 25.4 ie. 1280/96*25.4 and 768/96*25.4 for 1280x768 at 96 DPI
```
	DisplaySize	337 203
	HorizSync 	30-85
	VertRefresh 	50-80
```
The las thing is the resolutions. Unfortunatly it ignored the ones I put in and put in a whole bunch of them. Luckily one of them was the one I wanted.

After that you just hit Ctrl Alt Bksp to reset xorg and you should have the correct font size.

Now I am by no means a expert but if you have any trouble I'll try and help.

---

### Post by TuxCrafter on 2007-11-05
> **adlin5000 said:**
> After about 3 months of working I figured out the problem. XFCE uses the EDID info from your monitor to set the display size, and then calculates the DPI from that. Setting the DPI in your xorg.conf does you no good because XFCE overrides it. Editing the xfce config files doesn't work either because it just ignores it and figures it out for itself. Finally I found the xorg.conf options to ignore EDID and DDC settings. 
```
    Option "IgnoreEDID" "true"
    Option "NoDDC" "true"
```Then you have to put in the settings for your monitor because it wont detect them. Change the numbers to the settings of your monitor. You can calculate the display size by using resolution / DPI * 25.4 ie. 1280/96*25.4 and 768/96*25.4 for 1280x768 at 96 DPI
```
    DisplaySize    337 203
    HorizSync     30-85
    VertRefresh     50-80
```The las thing is the resolutions. Unfortunatly it ignored the ones I put in and put in a whole bunch of them. Luckily one of them was the one I wanted.

After that you just hit Ctrl Alt Bksp to reset xorg and you should have the correct font size.

Now I am by no means a expert but if you have any trouble I'll try and help.

Nice it works know, I hope my scripts helped you.

---

### Post by adlin5000 on 2007-11-06
The XFCE script really made the fonts look nicer. One thing I liked was that you did not have to restart for the changes to take effect. After you run the script you can actually watch the screen change and see the difference.

---

### Post by TuxCrafter on 2007-11-06
> **adlin5000 said:**
> The XFCE script really made the fonts look nicer. One thing I liked was that you did not have to restart for the changes to take effect. After you run the script you can actually watch the screen change and see the difference.

Yes nice little magic touch i had there, it toke me some time to figure it out since the hole setting managers changed with the new xfce release.

PS, I advice everybody to take a look at the Xserver Font rendering script (see signature). I just posted a new way of solving some dpi problems.

---

