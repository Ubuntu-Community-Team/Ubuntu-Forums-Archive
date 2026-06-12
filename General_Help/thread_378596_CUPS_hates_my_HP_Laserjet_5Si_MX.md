---
title: "CUPS hates my HP Laserjet 5Si MX"
date: 2007-03-07
forum: General Help
---

### Post by bryan.taylor on 2007-03-07
I have been banging my head against the wall trying to get my printer to work.  It seems to be set up correctly, but when I try to print it fails.  I have had this printer working with Gnome + Gentoo about a year ago.

This is what I've done so far:
1) Install the printer driver (ppd file) in the gnome add printer wizard
2) The name of the printer is "Laserjet 5Si/5Si MX PS"
3) The suggested driver is "Standard" (and it's the only one I can choose)
4) Now the printer is configured, yay!

The issue is that when i try to print a test page (or any other page), CUPS is telling the printer to use A4 paper instead of letter.  Ok, so I went to the printer properties dialog.  There I noticed that under the "Paper" tab you can set the paper size.  It had been set to A4, so I changed it to Letter.  The source tray is set as Tray 2, which is the tray that contains letter sized paper.  Under the "Advanced" tab there is a PageRegion setting that was set to A4.  I changed it to Letter (i'm not sure what this setting is though).  CUPS is still telling to printer to use A4 sized paper.

I have no A4 sized paper, which means I can't print, and even if I did I wouldn't want to use it.  Does anyone have any ideas as to how to fix this?

---

### Post by drpaul on 2007-03-07
Did you see what setting exist in the properties of the printer in the gnome printer manager?

Paul

---

### Post by bryan.taylor on 2007-03-07
Yes.
[quote=bryan.taylor]Ok, so I went to the printer properties dialog. There I noticed that under the "Paper" tab you can set the paper size. It had been set to A4, so I changed it to Letter. The source tray is set as Tray 2, which is the tray that contains letter sized paper. Under the "Advanced" tab there is a PageRegion setting that was set to A4. I changed it to Letter (i'm not sure what this setting is though).[/quote]

If there is a way for me to get a dump of the printer properties I will gladly post them.

---

### Post by drpaul on 2007-03-07
Don't know. Just thought you could look at them to see if the settings you put into the CUPS interface are the same ones that show with the gnome manager.

I've just struggled through some network configurations with CUPS. Don't understand it [and the documentation didn't help much] but luckily got it to work. Don't know how well gnome and cups communicate, so just check it out.

:) 
Paul

---

### Post by bryan.taylor on 2007-03-07
Thanks for the help :)

I'll see what I can do.

---

### Post by bryan.taylor on 2007-03-07
For anyone else who has trouble, this line is crucial:
[quote=drpaul]Don't know how well gnome and cups communicate, so just check it out.[/quote]
The answer is that the settings in the gnome print manager can be completely different from the CUPS settings.  I suppose that the gnome print manager settings are stored in the gnome "registry" for apps to grab, but the CUPS settings are what really matter.

To find your cups settings go to [http://localhost:631/](http://localhost:631/).  All I had to do was change the "media size" option to Letter in the printer settings.

---

### Post by talen.quickblade on 2007-05-03
Good call.  Just wanted to report that this has corrected my issue.  Twiddling the CUPS paper size settings we necessary before I was able to print from the paper tray instead of having to manually load paper every time I wanted to print something.

---

