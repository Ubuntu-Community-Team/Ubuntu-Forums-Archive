---
title: "Giant Font Making Applications Unuseable"
date: 2008-01-26
forum: General Help
---

### Post by Gillette on 2008-01-26
When I am booting up Ubuntu (I'm a new user and haven't figured out very much about this operating system) the computer stops and there is a huge message: Ubuntu is Running. The only way to get the computer to proceed is to press escape. This problem was not there when I first loaded Ubuntu 7.1 on this Elderly Gateway (1999). Now today when I opened Open Office application the same problem was there. The fonts for the drop down menus like File are like size 100 font and it makes the application unusable. I looked in the help files and found some commands about changing fonts sizes but everything was totally foreign to me and I knew not how to proceed.

Lance

---

### Post by erginemr on 2008-01-26
Hi,

Can you please check the following semi English-Spanish (and Turkish) thread:
[http://ubuntuforums.org/showthread.php?t=608986](http://ubuntuforums.org/showthread.php?t=608986)

esp. screenshots therein and follow the same technique to correct your fonts? 
Ask for more if you do not get the idea.

---

### Post by Gillette on 2008-01-26
Thanks for the help. I did go to that thread. My Spanish is not too good but I did see where I should do alt-F2. Anyway I found a place called font rendering and it was 96 dpi. So I changed it to 14 and closed. Then I opened the Open office application and it had normal sized fonts. I went back to the font-rendering place and the 96 had reappeared. So I don't know what is going on.

---

### Post by erginemr on 2008-01-26
No no... "96 dpi" is something else and is correct. I have 96 dpi in the same setting, too.

Can you please right click on your desktop, select "change background", then onto the "fonts" tab and make sure that all font sizes are as the attachment? Does it make any difference?

---

### Post by Gillette on 2008-01-27
I right clicked on desktop and checked on the font sizes. They were all 10. So I guess that was not the source of the problem.

---

### Post by xc3RnbFO8P on 2008-01-27
Set your "Monospace" to 1

You need update.

---

### Post by Gillette on 2008-01-27
The applications are now usable again with regular sized font for the drop down menus--but this is before I set the Monospace to 1. I've set the monospace to 1. I rebooted and "Ubuntu is running" still shows up in giant font. Also when I type my logon name and password the font is humungous. The other day I asked ubuntu to look for updates but it said there aren't any.

---

### Post by erginemr on 2008-01-27
Well, I am confused. Does setting your monospace font size back to, say 10 px, resolve the problem?

---

### Post by Gillette on 2008-01-27
Actually when I opened a terminal the font was tiny so I had to se the monospace font back to size 10 and then the terminal was ok again. The large font "Ubuntu is running" and the large font when I type in my username and password are still very large.

Applications are now normal.

By the way, I have an ancestor that came from Izmer Turkey. He was Greek. He came to Florida about 230 years ago and married a Spanish woman from Minorca. They were indentured servants on an Indigo plantation.

---

### Post by erginemr on 2008-01-28
The initial login screen you see is called "gdm", so we have narrowed down the issue to a "gdm font size problem" now.

I have done a small research for your problem with these keywords, which resulted in the following three distinct solutions (I believe methods I & II are somewhat related). I have listed them in order starting from the easiest to most cumbersome. So, I suggest you to start with method-I and move on if it doesn't work.

------------------
SOLUTION-I:
------------------

From [http://ubuntuforums.org/showthread.php?t=23048](http://ubuntuforums.org/showthread.php?t=23048)

> **dmazzone said:**
> [b]...
On high-res screens (e.g. 15" 1680x1050), some users consider the default fonts too be too large. You can fix this by following these steps:
   1. Open System->Preferences->Appearance
   2. Select the "Fonts" tab
   3. Click the "Details" button (lower right)
   4. Adjust the Resolution down to 96dpi
   5. Make sure you have Subpixel (LCD) Smoothing enabled
   6. Save the preferences 

If you also want small fonts on the GDM login window, you can do this:
   1. Open System->Administration->Login Window
   2. Select the 'Security' tab
   3. Click the 'Configure X-Server' button
   4. Append '-dpi 96' (without quotes) to the text in the 'Command' field"
...

From [http://ubuntuforums.org/showthread.php?t=235214](http://ubuntuforums.org/showthread.php?t=235214)

> **seandlh said:**
> Are you using an nvidia graphics card?  I just installed edgy with a Geforce 6200 and LCD TV and saw this problem
....
You can change the X server options in the System->Administration->Login Window.  Click on the security tab and then click on the Configure X Server button.  I added "-dpi 100" to the options and the problem went away.
-- Sean

-------------------
SOLUTION-II:
-------------------

From [http://ubuntuforums.org/showthread.php?p=3609621](http://ubuntuforums.org/showthread.php?p=3609621)

> **pashashome said:**
> Ok drvista's suggestion did work I needed to reboot like he said instead of just restart X.

Try this, seems to work for me. 

I managed to fix the problem ,
sudo gedit /etc/gdm/gdm.conf
find
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0

and change it into
[server-Standard]
name=Standard server
-command=/usr/bin/X -br -audit 0 -dpi 96

then restart ubuntu and it's fixed now

From [http://ubuntuforums.org/showthread.php?t=583915](http://ubuntuforums.org/showthread.php?t=583915)

> **ashughes said:**
> ...
I have managed to fix it permanently however.  This is what I did:
1. sudo gedit /etc/gdm/gdm.conf
2. find the section [server-Standard] in that file
3. You should see a line that says "-command=/usr/bin/X -br -audit 0".  Change it to read "-command=/usr/bin/X -br -audit 0 -dpi 96".
4. Save, quit, and restart

You should be good to go now.

Cheers

--------------------
SOLUTION-III:
--------------------

From [http://ubuntuforums.org/showthread.php?t=72571](http://ubuntuforums.org/showthread.php?t=72571)

> **Dolphin said:**
> open a console

enter
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```

In your xorg.conf, look for Section "Monitor" and insert these lines:

```
#	DisplaySize	270	203	# 1024x768 96dpi
#	DisplaySize	338	254	# 1280x960 96dpi
#	DisplaySize	338	270	# 1280x1024 96dpi
#	DisplaySize	370	277	# 1400x1050 96dpi
#	DisplaySize	423	370	# 1600x1400 96dpi
```

Uncomment the line coresponding to the resolution you're using.
Restart X.

From [http://ubuntuforums.org/showthread.php?t=235214](http://ubuntuforums.org/showthread.php?t=235214)

> **Anduu said:**
> There is an option that can be set in the monitor section of your xorg.conf that could solve your problem...
"DisplaySize"

To calculate what numbers to use take the resolution of your monitor, multiply by 25.4, then divide by the desired DPI. For Example if you run at 1600x1280 and want 100dpi : 1600 x 25.4 / 100 = 406 and 1280 x 25.4 / 100 = 325

Now go to your Monitor section in xorg.conf and enter:
```
 DisplaySize 406 325
```
It should end up looking like this:
```
Section "Monitor"
	Identifier	"LCD Multi-Me"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
	Modeline "1280x720_60.00"  74.48  1280 1336 1472 1664 720 721 724 746
	DisplaySize 406 325
	Option "DPMS" "true"
EndSection
```

P.S. Thank you for the info regarding your ancestor's origin. So, this makes us half-citizen, which makes me double happy in trying to help you solve your problem. Take Care... :)

---

### Post by Gillette on 2008-01-28
I was mistaken about updates! Under administration I had gone to update manager and requested it look for updates. The reply was my system was up-to-date. This surprised me very much since my experience with installing windows operating systems there were always tons of updates.

Anyway yesterday someone pointed me to the software management under Administration. There I found I needed to enable some repositories and on the update tab enable some stuff there. So suddenly I found there were 78 updates waiting to download. I left my computer on all night downloading updates.  I've got a slow dialup connection at the moment. Only have about three left to download. I'll do those this evening. 

I did interrupt the downloading once and rebooted the computer and the giant fonts were gone! There was some other message about screen resolution and video drivers. 

Someone asked if I have an nvidia graphics card. Yes I do believe that is what it is. I always see nvidia appearing on the screen when the computer is booting up.

---

### Post by kmads on 2008-04-21
This thread solved my problem: [http://ubuntuforums.org/showthread.php?t=755930](http://ubuntuforums.org/showthread.php?t=755930)

Best,
Mads

---

### Post by kmads on 2008-04-21
> **kmads said:**
> This thread solved my problem: [http://ubuntuforums.org/showthread.php?t=755930](http://ubuntuforums.org/showthread.php?t=755930)

Best,
Mads

Which is the same as solution-II I now realize.. 

-mads

---

