---
title: "Resolution issue"
date: 2006-09-17
forum: General Help
---

### Post by jebster on 2006-09-17
If this has been delt with before, sorry, I tried searching, but nothing I found seemed to fix this... Not to mention I am a huge n00b to linux. 

After I installed Ubuntu 6.06 stuff for the most part seemed to work fine, expect it only listed 640x480, 800x600, & 1024x768 resolutions. And all the text on the screen was weird and fuzzy looking, hard to read. So, I searched around and decided after reading a few articles and posts on forums, to change the driver it was using from ati to vesa. I edited xorg.conf to reflect the driver I wanted, restarted, and the text is now crisp and clear. But, it still wouldn't let to up the resolution and the screen stretchs off my monitor to the side(due to different aspect ratio I guess :confused: ), so, I read more, and tried adding "1280x1024"(the res I always use in windows) to the Modes lines under each Subsection "Display" thing then rebooted, then checked under System -> Preferences -> Screen Resolution, and still it only listed the original 3. So, I figured maybe it only wants 3 resolutions at a time, so I deleted 640x480 from each line then rebooted again, but, again, still only listed the original 3, including the one I just deleted from xorg.conf. :confused: 

And that is pretty much where I am now. Confused. Oh, and also have a head ache, the refresh rate is too low and it doesn't even give me an option other then 61 Hz. 

My gfx card is a ATI Radeon X800XL 256mb AGP(R430) and my monitor is a NEC MultiSync FP1350X(22").

```
Section "Device"
	Identifier	"ATI Technologies, Inc. R430 UM [Radeon X800 XL] (PCIe)"
#	Driver		"ati"
	Driver		"vesa"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R430 UM [Radeon X800 XL] (PCIe)"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600"
	EndSubSection
EndSection
```

Any other info you need just ask. Thanks :)

---

### Post by DoktorSeven on 2006-09-17
I'm really shocked that Ubuntu doesn't give you any way to edit or set your monitor sync/refresh values for issues like this. :(

Basically you'd have to find your "Horizontal Sync" and "Vertical Refresh" rates for your monitor and plug them into /etc/X11/xorg.conf.  I did a writeup on doing this in [this post](http://www.ubuntuforums.org/showpost.php?p=1463344&postcount=11) (note that in that specific case the HorizSync was already correct in that xorg.conf -- you may have to modify both depending on your correct values), so you can use that as a guide.

---

### Post by jebster on 2006-09-17
Cool thx, I will look into that tomorrow(2:20am + bad headache = bedtime lol). Hopefully that will solve one problem :)

---

### Post by semakwetu on 2006-09-17
> **DoktorSeven said:**
> I'm really shocked that Ubuntu doesn't give you any way to edit or set your monitor sync/refresh values for issues like this. :(

I too was surprised when I switched from Kubuntu where a there is a system GUI client to manage the monitor.

---

### Post by jebster on 2006-09-17
No suggestions on how to fix my res. problem? :(

---

### Post by jebster on 2006-09-17
I installed KDE in an atempt to get something working.. same as with Gnome, guess I should have seen that coming :( Oh  well.

Is there a different driver I can try using?
ati =  640x480 - 1024x768 res, fuzzy fonts hard to read, forget what refresh rate
vesa = 640x480 - 1024x768 res, clear fonts, 61 Hz refresh rate

Gnome and KDE menu to change refresh rate have no other options. Will go look into what DoktorSeven said. Hurts to look at monitor :(

---

### Post by jebster on 2006-09-17
What numbers do I use in the vertical and horizontal things? Here is the data sheet, I don't see seperate numbers for each [Link to PDF]("http://www.necdisplay.com/corpus/F/K/FP1350X_spec.pdf#search=%22NEC%20Multisync%20fp1350x%22") ([HTML Version]("http://72.14.203.104/search?q=cache:r2ZUSh86sPIJ:www.necdisplay.com/corpus/F/K/FP1350X_spec.pdf+NEC+Multisync+fp1350x&hl=en&gl=ca&ct=clnk&cd=2&client=firefox"))

Thanks :)

---

### Post by jebster on 2006-09-17
ok, I set the driver back to the ati one. Now, it gives me a bunch of resolution options, including ones not listed in xorg.conf :confused: I really have no idea how this all works lol Don't understand that... But whatever..

It now lets me use 1280x1024, BUT the fonts still look weird, in fact, everything does, including the smilies next to this post box.

Some parts of the fonts look to thick, some to thin. Actually, some letters are to thick, and some are to thin almost.. kinda like that movie A Beautiful Mind when he sees the hidding messages in a bunch of text.. some letters seem to sand out more then others :confused: But its not always the same, like sometimes it will be a whole line of thick letters, then a line of thin, seems quite random lol 

ANY idea would be helpful lol Would love to start using Linux more instead of Windows.

---

### Post by jebster on 2006-09-18
I switched it to a different monitor, a Samsung SyncMaster 753DF(17") and now with the ati driver the fonts and everything else seem to look fine. But, now it again only lets me have a max of 1024x768 resolution, when with the other monitor it looked fuzzy but let me have 1280x1024 resolution! I don't get it :(

I have this same problem with a couple liveCDs I have tried, like Knoppix. But others, like Kororaa XGL work fine, and that one sets my res to 1600x1200 by default!

lol I don't wanna be stuck with only windows!! Heck, if I could get Ubuntu looking right and everything, and be able to play my favorite games, I would burn everything I have related to Microsoft!

---

### Post by jebster on 2006-09-18
ROFL Man I am a n00b! Well, kinda, I changed xorg.conf to add 1600x1200 too, and with that res everything looks pretty much perfect with the "ati". I would perfer 1280x1024 but this will do for now lol

Still gotta figure out the refresh rate thing, my eyes are still killing me, even after taking 2 asprin :(

I checked Kororaa XGL's xorg.conf file, and it runs "fglrx" driver, which I understand is ATI's proprietary driver. And from what I understand, its possible to install that XGL thing on Ubuntu, so, I am going to try installing both that fglrx driver and XGL lol 

If I am wrong in my thinking, let me know :P Oh well, not like reinstalling Ubuntu is hard lol Already had to a couple times because I screwed up stuff a couple times. But I still haven't damaged my XP install on this hard drive amazingly enough lol

---

### Post by jebster on 2006-09-18
BOOYAA!!! fglrx driver installed, 1280x1024 now looks fine, and 1600x1200 still does too! AND it lets me change the refresh rates, but, sadly, 60Hz is still the highest.

Still one heck of a step in the right direction!! w000t!

Now to take on XGL or whatever :D


[SIZE="1"]Yes, I have realized no one else is posting in reply, but, posting this has helped me think and I can see what I have done so far and what-not :P hehe[/SIZE]

---

### Post by semakwetu on 2006-09-18
Hi

From the pdf link you gave your refresh rates are

Synchronization Range:
          Horizontal   31 kHz to 115 kHz
          Vertical     55 Hz to 160 Hz

from the xorg.conf you posted you would need

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	31-115
	VertRefresh	55-160
EndSection

Hope that helps

---

### Post by jebster on 2006-09-19
Cool thx, will give that a try tomorrow :)

---

